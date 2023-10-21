# rog-ally-motion-evdev
This is the Arch Linux package for the fork of [ally-motion-evdev](https://github.com/NeroReflex/ally-motion-evdev) that lets any user expose the ROG ally bmi323 chip as a controller.

## Usage
To use this package compile it, install it and use the provided systemd service file:

```sh
makepkg -sfi
systemctl --user enable ally-motion-evdev
```

## Contributions
A big thanks goes to [TwinHaelix](https://github.com/KWottrich) that has modified the original package to provide all of us this good stuff <3
Another big thanks goes to WarlockLord that has written the systemd service file to run this program as a user service allowing the usage in game mode (Nintendo) emulators