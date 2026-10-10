# nice-view-mod

Private ZMK module: vendored `nice_view` shield from [zmkfirmware/zmk](https://github.com/zmkfirmware/zmk)
(`app/boards/shields/nice_view/`, branch main), renamed to `nice_view_custom`.

Changes vs upstream:

- WPM widget removed (number + sparkline, `wpm_status_state`, WPM listeners/subscriptions,
  `ZMK_WPM` select in Kconfig.defconfig).
- Battery percentage drawn as text next to the battery icon (`lv_font_unscii_8`).

The SPI overlay keeps the upstream `&nice_view_spi` label and `sharp,ls0xx` node — the
board (e.g. `piantor_pro_bt`) must provide `&nice_view_spi`.

## Usage

In your ZMK user config `west.yml`:

```yaml
manifest:
  remotes:
    - name: teddybear
      url-base: https://github.com/teddybear
  projects:
    - name: nice-view-mod
      remote: teddybear
      revision: main
```

Then build with `shield: nice_view_custom`.
