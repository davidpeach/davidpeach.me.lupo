---
title: Setting up bluetooth headset on Arch Linux
---

```
sudo pacman -S pulseaudio-alsa pulseaudio-bluetooth bluez-utils
```

```
sudo systemctl enable --now bluetooth
systemctl --user enable --now pulseaudio
```

Turn on headset to pairing mode

```
bluetoothctl

scan on
pair _HEADSET_IDENTIFIER_
trust _HEADSET_IDENTIFIER_
connect _HEADSET_IDENTIFIER_
quit
```
