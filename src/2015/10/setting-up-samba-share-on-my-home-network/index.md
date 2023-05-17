---
title: "Setting up samba share on my home network"
date: "2015-10-26"
categories: 
  - "braindumps"
tags: 
  - "braindump"
  - "linux"
  - "networking"
  - "servers"
---

Secure shell into file server.

Install samba if not already present:

```
sudo apt-get install samba
```

Create samba password with :

sudo smbpasswd -a YOUR\_USERNAME

Configuring the share:

```
sudo nano /etc/samba/smb.conf
```

```
# /etc/samba/smb.conf
[media]
path = /home/YOUR_USERNAME/Share
available = yes
valid users = YOUR_USERNAME
read only = no
browsable = yes
public = yes
writable = yes
```

Restart samba:

```
sudo restart smbd
```
