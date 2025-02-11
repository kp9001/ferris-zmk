# Ferris-ZMK

My personal configuration for the [Ferris Sweep](https://github.com/davidphilipbarr/Sweep) keyboard using [ZMK](https://github.com/zmkfirmware/zmk) firmware. 

Instructions for installing ZMK and customizing the firmware on a compatible board are found [here](https://zmk.dev/docs/user-setup). 

## Keymap Philosophy

The keymap for this firmware contains 3 main layers:

- QWERTY with home row mods
- A slight variation on COLEMAK-DH with home row mods
- A QWERTY-based game layer, which provides a normal left hand space and esdf keys for game movement

These main layers are swapped between using global combo keys. All other layers are accessed via layer keys. The symbols contains numbers in their usual position on the top row, various system keys on the second row, such as escape, tab, backspace, and delete, and extraneous symbols on the bottom row. Other symbols can be reached as a shifted number layer, in their normal positions. 

The placement of delete and backspace are based on esdf (game) and hjkl (vim) movement keys. The navigation layer maps arrow keys to the same, to provide natural navigation with both hands. Media control keys are found here as well. The additional thumb key is reserved for enter/return. 

All other keys are fit into the misc layer, e.g. the funnction keys. BT_SEL keys are also found on this layer, but are largely useless due to the bluetoooth device limitation outlined below. They do, however, serve a natural use if the bluetooth connnection limit is raised. 

## Bluetooth

By default, ZMK allows 5 bluetooth connections. This config effectively limits that number to 1. Pairing a new device will require clearing a previously paired device, which can be achieved using the BT_CLR combo key. 

Default functionality can be restored by setting the following in [cradio.conf](config/cradio.conf). 

```
CONFIG_BT_MAX_CONN=5
CONFIG_BT_MAX_PAIRED=5
```

On the other hand, bluetooth functionality can be effectively disabled by setting the following in [cradio.conf](config/cradio.conf). 

```
CONFIG_BT_MAX_CONN=2
CONFIG_BT_MAX_PAIRED=1
```

## Security Hardening

This firmware sets certain hardening configs based on [Zephyr Documentation](https://docs.zephyrproject.org/latest/security/index.html). It also sets certain [experimental bluetooth security features](https://zmk.dev/docs/config/bluetooth) in ZMK, such as enforcing passkey entry for bluetooth pairing. 
