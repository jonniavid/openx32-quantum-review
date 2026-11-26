# Native port status

The show-first UI is also implemented as a native LVGL page in OpenMixerControl.

- Pull request: https://github.com/OpenMixerProject/OpenMixerControl/pull/128
- Branch: `ui/show-first-prototype` on `jonniavid/OpenMixerControl`
- Base branch: `development-v2`
- Current head: `3a4e907`

The page reuses the existing empty Prototype GUI tab, so the EEZ Studio project
does not need to be regenerated. It keeps the 800x480 layout, accent color,
16 tabs, fader map, DELAY/ALIGNMENT grid, SETUP IP editor and simulator encoder
bindings from this prototype.

Build checks on 26 November 2026:

- `TARGET_PC_SDL2`: clean build OK.
- `TARGET_XM32`: clean build OK with armel GCC 14.
- `TARGET_WING`: clean build OK with Arm GNU Toolchain 15.2.

`compile-cross.sh` in the fork downloads the cross toolchains and builds all
three targets from clean. The page is still UI only: DSP, FPGA and mixer network
settings are not connected.
