# cliamp-plugin-reverb

A horizontal LED-matrix visualizer for [cliamp](https://cliamp.stream), inspired by vintage HiFi "Reverberation Graphic" displays. Ten frequency bands are drawn as vertical bars rendered with Unicode braille (U+2800 to U+28FF), growing symmetrically up AND down from a center line. Band 1 (subbass) sits in the middle; higher bands fan outward to both sides (mirrored left/right). The result is a quad-symmetric pattern that pulses outward with the music. Sibling of [led-burst](https://github.com/AlexZeitler/cliamp-plugin-led-burst), [block-burst](https://github.com/AlexZeitler/cliamp-plugin-block-burst), and [vu-meter](https://github.com/AlexZeitler/cliamp-plugin-vu-meter).

https://github.com/user-attachments/assets/12a15260-6246-4845-9bed-b1310d909f6d

## Install

```sh
cliamp plugins install AlexZeitler/cliamp-plugin-reverb
```

Then start cliamp and press `v` to cycle visualizers until `reverb` appears.

To pin a specific version:

```sh
cliamp plugins install AlexZeitler/cliamp-plugin-reverb@v0.1.0
```

Remove with:

```sh
cliamp plugins remove reverb
```

## Tuning

The plugin is a single Lua file. Edit `~/.config/cliamp/plugins/reverb.lua` after installing if you want to customize:

| What | Where | Effect |
|------|-------|--------|
| Color ramp | `LEVEL_RAMP` | The four-step intensity gradient. Defaults to bright green / green / bright yellow / bright red (the classic VU-meter palette shared with the sibling plugins); swap to any ANSI 16-color SGR codes to match a different theme palette. |
| Max bar width | `MAX_BAR_WIDTH` | Cap on bar thickness in dots (2 dots = 1 char cell). Default 10 (= 5 cells). Raise for fatter bars on wide panels, lower for a leaner look. |
| Minimum gap | `MIN_GAP` | Smallest gap between adjacent bars in dots. Default 1. Raise for more breathing room, lower to pack bars tighter on narrow panels. |
| Bar density | `DOT_STEP` | Vertical dot spacing inside a bar. `1` draws a solid line, `2` (default) gives the LED-matrix look. |
| Decay rate | `prev - 0.05` in `p:render` | Per-frame fall-off after a peak. Lower for slower decay (bars hang longer), higher for snappier response. |

## Requirements

- cliamp with Lua plugin support
- A terminal with ANSI 16-color support and Unicode braille glyphs (effectively every modern terminal)

## Related plugins

- [AlexZeitler/cliamp-plugin-led-burst](https://github.com/AlexZeitler/cliamp-plugin-led-burst) - Stereo LED matrix that bursts outward from a center divider, with green / yellow / red tiers and peak hold.
- [AlexZeitler/cliamp-plugin-block-burst](https://github.com/AlexZeitler/cliamp-plugin-block-burst) - Nested LED pyramid where each tier responds to a different frequency range.
- [AlexZeitler/cliamp-plugin-vu-meter](https://github.com/AlexZeitler/cliamp-plugin-vu-meter) - Ten analog-needle VU meters, one per spectrum band, drawn with sub-pixel braille.

## License

MIT - see [LICENSE](LICENSE).
