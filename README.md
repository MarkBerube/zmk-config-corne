# Corne keymap and firmware

This repository builds the firmware Mark flashes to his wireless Corne. The layout follows his Kinesis Advantage2. The left half is the central controller and resolves key presses from both halves. The right half displays the Corge artwork.

| Change | Where to make it |
| --- | --- |
| Keys, layers, thumb positions, tap and hold behavior | [config/corne.keymap](config/corne.keymap) in this repository |
| Board and display shields for either half | [build.yaml](build.yaml) in this repository |
| Corge bitmap and display integration | [Display artwork repository](https://github.com/MarkBerube/corne-wireless-view-zmk-config/tree/master/zephyr) |
| Select the artwork revision included in firmware | The `corne-display-art` project in [config/west.yml](config/west.yml) |

## Build and flash

1. For a layout change, edit the keymap here. For an artwork change, commit the module in the display repository first, then update its pinned commit here.
2. Open the [firmware workflow](https://github.com/MarkBerube/zmk-config-corne/actions/workflows/build.yml) and select the run for the intended `master` commit. Check that both half builds and **Merge Output Artifacts** succeeded. For an artwork change, check the right-half build log for `corge.c.obj`.
3. Download **firmware** from that run. For a matched pair, use both UF2s from that ZIP. Flash the file containing `corne_left` to the left controller and `corne_right` to the right. A keymap-only update takes effect on the left controller. The right-side image supplies the artwork.

## Quick hardware check

On the Advantage2-style Base layer, the middle left thumb sends Backspace and the upper-right key also sends Backspace. From the split outward, the right thumbs are **Enter**, **Space**, and **Keypad** (hold for Numbers/F-keys). Hold the inner left thumb for Code and press U/I for brackets or J/K for parentheses. Check the Corge image on the right display separately.

If results differ, record the repository, run URL, commit, and which UF2 went onto each controller. A ZIP checksum identifies a download. A physical key or screen test confirms what the keyboard is doing.
