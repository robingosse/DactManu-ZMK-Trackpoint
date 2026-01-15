# BugBear ZMK Config with TrackPoint Support

This is a complete ZMK configuration for a 30-key split keyboard with PS/2 TrackPoint support.

## Quick Start

1. **Upload this to your GitHub repository** named `zmk-config`
2. **GitHub Actions will automatically build your firmware**
3. **Download the firmware** from Actions → Latest build → Artifacts
4. **Flash to your nice!nano** by copying the .uf2 file

## Hardware

- Controller: nice!nano v2
- TrackPoint: Connected to pins 8 (DATA) and 9 (CLK)
- Voltage: 3.3V through voltage regulator
- Right side is the central (brain)

## Features

- ✅ PS/2 TrackPoint support (UART driver for best performance)
- ✅ Mouse buttons on Layer 1
- ✅ Function keys on Layer 2
- ✅ Bluetooth with increased transmit power
- ✅ Automatic firmware builds via GitHub Actions

## Customization

### Adjust Your Matrix Pins

Edit `config/boards/shields/bugbearzmnright/bugbearzmnright.overlay` and change the row/col GPIO pins to match your keyboard wiring.

### Customize Your Keymap

Edit `config/bugbearzmnright.keymap` to change key positions and layers.

### TrackPoint Settings

All settings are in:
- `config/bugbearzmnright.conf` - Enable/disable features
- `config/boards/shields/bugbearzmnright/bugbearzmnright.overlay` - Pin configuration

## Troubleshooting

### Build Fails

Check the Actions tab for error messages. The most common issues:
- Wrong pin numbers in overlay
- Syntax errors in keymap

### TrackPoint Not Working

1. Verify wiring (CLK on pin 9, DATA on pin 8)
2. Check voltage regulator output (should be 3.3V)
3. Enable logging in `.conf` file to see debug output

### Mouse Moving Wrong Direction

In the overlay file, add these to the `trackpoint_listener` node:
```
xy-swap;    // Swap X and Y
x-invert;   // Invert X axis
y-invert;   // Invert Y axis
```

## Credits

- PS/2 Driver: https://github.com/infused-kim/kb_zmk_ps2_mouse_trackpoint_driver
- ZMK Firmware: https://zmk.dev

## License

MIT License - Copyright (c) 2025 Robin Gosse
