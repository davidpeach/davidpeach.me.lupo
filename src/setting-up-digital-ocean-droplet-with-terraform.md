---
title: Setting up a Digital Ocean droplet with Terraform
---

## Installing Terraform

Terraform has [installation instructions](https://developer.hashicorp.com/terraform/downloads?product_intent=terraform), but you may be able to find it with your package manager.

Here I am installing it on Arch Linux with `pacman`

```
sudo pacman -S terraform
```

## Describing your desired infrastructure with code

Terraform uses a declaritive language, as opposed to imperetive.

What this means for you, is that you write configuration files that describe the state that you want your infrastructure to be in.
For example if you want a single server, you just add the server spec in your configuration and Terraform will work out how best to do it.
You dont need to be concerned with the nitty gritty of how it is achieved.

I have a real-life example that will show you exactly what a minimal configutation can look like.

Clone / fork [the repository for my website serve](https://github.com/davidpeach/davidpeach.me.terraform).

## Explaination of my terraform repository.

```
terraform {
  required_providers {
    digitalocean = {
      source = "digitalocean/digitalocean"
      version = "~> 2.0"
    }
  }
}

variable "do_token" {}

provider "digitalocean" {
  token = var.do_token
}
```

The first block tells terraform which providers I want to use. Providers are essentially the third-party APIs that I am going to interact with.  
Since I'm only creating a Digital Ocean droplet, and a couple of surrounding resources, I only need the digitalocean/digitalocean provider.

The middle block above tells terraform that it should expect - and require - a single variable to be able to run. This is the Digital Ocean Access Token that will be obtained from the Digital Ocean dashboard.

The bottom block is the setting up of the provider. Basically just passing the access token into the provider so that it can perform the necessary API calls it needs to.

```
resource "digitalocean_ssh_key" "davidpeachme" {
  name       = "davidpeachme"
  public_key = file("/home/david/.ssh/id_rsa.davidpeachme.pub")
}
```
Here is the first resource that I am telling terraform to create. Its taking a public key on my local filesystem and sending it to Digital Ocean.  
This is needed for ssh access to the server once it is ready. However it is added to the root account on server.

I use Ansible for setting up the server with the required programs once Terraform has built it. So this ssh key is actually used by Ansible to gain access to do its thing.

```
resource "digitalocean_droplet" "davidpeachme" {
  image    = "ubuntu-22-10-x64"
  name     = "davidpeach.me"
  region   = "lon1"
  size     = "s-1vcpu-1gb"
  ssh_keys = [digitalocean_ssh_key.davidpeachme.fingerprint]
}
```

Here is the meat of the infrastructure - the droplet itself. I am telling it what operating system image I want to use; what size and region I want; and am telling it to make use of the ssh key I added in the previous block.

```
data "digitalocean_domain" "davidpeachme" {
  name = "davidpeach.me"
}
```
