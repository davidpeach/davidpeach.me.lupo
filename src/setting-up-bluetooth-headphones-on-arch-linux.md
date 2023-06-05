---
title: Setting up my WH-1000XM4 bluetooth headphones on Arch Linux (i3 window manager)
---

Please note: I'm writing these notes up after I've fully set up my bluetooth headset (WH-1000XM4). I apologise if I've missed any steps, but I will be using this page in the near
future to re-setup my laptop again. I will fill in the blanks then.

Install the required packages as per the [ Arch Wiki ](https://wiki.archlinux.org/title/Bluetooth_headset#Headset_via_Bluez5/PulseAudio):
```
sudo pacman -S pulseaudio-alsa pulseaudio-bluetooth bluez-utils
```

Enable and start the required services:
```
sudo systemctl enable --now bluetooth
systemctl --user enable --now pulseaudio
```

Turn on the bluetooth headphones to "pairing" mode.

Enter `bluetoothctl` and press enter to go into the bluetoothctl interactive prompt:

```
bluetoothctl
```

Then use the following commands within the bluetoothctl interactive mode to find, trust and connect to the headset.

The trust command will ensure that the headphones automatically connect when the bluetooth daemon service is running.

```
scan on
pair _HEADSET_IDENTIFIER_
trust _HEADSET_IDENTIFIER_
connect _HEADSET_IDENTIFIER_
quit
```
