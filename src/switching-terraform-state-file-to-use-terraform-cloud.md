## Setting up Terraform state in Terraform cloud

Head to [Terraform Cloud](https://www.hashicorp.com/products/terraform/pricing?product_intent=terraform) and create a free tier account.

Once created and logged into your dashboard, click the create button in the top right and select "workspace".

Step 1: Click "CLI-driven workflow"
Step 2: Give your workspace a name
Step 3: Click create workspace

You should now be shown a page with a snippet of code that we can add to our terraform configuration to tell it to store our state file in Terraform Cloud.

Heres my example code:

```
terraform {
  cloud {
    organization = "davidpeach"

    workspaces {
      name = "davidpeachme"
    }
  }
}
```

You can merge this with the existing initial terraform block at the top of the configuration file.

Then you just need to login to terraform cloud from your cli.

```
terraform login
```

This will let you know of a file it will create in your home directory and that it will open a browser to obtain a token to authenticate with.

type "yes" and hit enter.

When the browser opens it should ask you to give your token a description and choose an expiry. Enter these and click create.

Then just copy the token string in the green box and paste it into your terminal where it asks and hit enter.

You should see a message reading "Welcome to Terraform Cloud"
