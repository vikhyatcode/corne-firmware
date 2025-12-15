# Corne Keyboard ZMK Firmware

ZMK firmware configuration for the Corne (CRKBD) split keyboard with Nice!Nano (or compatible) controllers.

## Quick Start

### Using This Config as a Template

1. **Fork this repository** to your own GitHub account
2. **Edit your keymap** in `config/corne.keymap`
3. **Commit and push** your changes
4. **Download firmware** from the Actions tab once the build completes

### Downloading the Firmware

After each commit, GitHub Actions automatically builds three firmware files:

| File | Purpose |
|------|---------|
| `corne_left-nice_nano-zmk.uf2` | Left half firmware |
| `corne_right-nice_nano-zmk.uf2` | Right half firmware |
| `settings_reset-nice_nano-zmk.uf2` | Reset to factory settings |

**To download:**
1. Go to the **Actions** tab in your forked repo
2. Click the latest successful workflow run
3. Download the `firmware` artifact (contains all `.uf2` files)

## Flashing the Firmware

1. Connect your keyboard half via USB
2. **Enter bootloader mode** by double-pressing the reset button
3. A drive named `NICENANO` (or similar) will appear
4. Drag and drop the appropriate `.uf2` file onto the drive
5. The keyboard will automatically reboot
6. Repeat for the other half

> **Tip:** Flash the left half first, then the right half. They will automatically pair over Bluetooth.

## Customizing Your Keymap

Edit `config/corne.keymap` to customize your layout. Key resources:

- [ZMK Keycodes Reference](https://zmk.dev/docs/codes)
- [ZMK Behaviors](https://zmk.dev/docs/behaviors) (hold-tap, mod-morph, macros, etc.)
- [ZMK Keymap Editor](https://nickcoutsos.github.io/keymap-editor/) — Visual editor that works with GitHub repos

### Keymap Structure

```
/ {
    keymap {
        compatible = "zmk,keymap";

        default_layer {
            bindings = <
                // Your key bindings here
            >;
        };

        lower_layer {
            // ...
        };

        raise_layer {
            // ...
        };
    };
};
```

## Troubleshooting

### Keyboard halves won't pair
Flash `settings_reset-nice_nano-zmk.uf2` to **both halves**, then re-flash the regular firmware.

### Build fails in GitHub Actions
Check the Actions log for errors. Common issues:
- Syntax errors in `corne.keymap`
- Invalid keycodes or behaviors

### Controller not entering bootloader
- Try a different USB cable (data cables, not charge-only)
- Hold the reset button while plugging in USB

## Compatible Controllers

This config is built for **Nice!Nano v2** and compatible clones:
- Nice!Nano v2
- SuperMini nRF52840
- Other nRF52840-based Nice!Nano clones

## Resources

- [ZMK Documentation](https://zmk.dev/docs)
- [Corne Keyboard GitHub](https://github.com/foostan/crkbd)
- [ZMK Discord](https://zmk.dev/community/discord/invite) — Community support

## License

This configuration is provided as-is. Feel free to fork and modify for your own use.
