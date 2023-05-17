---
title: "Bulk converting large PS4 screenshot png images into 1080p jpg's"
date: "2020-09-03"
categories: 
  - "braindumps"
tags: 
  - "command-line"
  - "linux"
  - "programming"
---

I tend to have my screenshots set to the highest resolution when saving on my PlayStation 4.

However, when I upload to the screenshots area of this website, I don't want the images to be that big -- either in dimensions or file size.

This snippet is how I bulk convert those images ready for uploading. I use an Ubuntu 20.04 operating system when running this.

```
# Make sure ImageMagick is installed
sudo apt install imagemagick
# Run the command
mogrify -resize 1920x1080 -format jpg folder/*.png
```

You can change the `width**x**height` dimensions after the `-resize` flag for your own required size. As well as changing the required image format after the `-format` flag.
