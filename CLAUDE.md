# CLAUDE.md

This file provides guidance to Claude Code when working in this repository.

## What this repository is

A passive two-connector adapter: the Sophia 3's 16-pin digital video header out to a micro
HDMI Type D receptacle, for the XEBook laptop build. Two layers, no active components. See
`README.md` for the pin mapping.

## Known cosmetic issue

**J2's symbol is still labelled "Sophia 2 Connector 1x16"** in the schematic, in a Sophia 3
project — the symbol was reused from the earlier Sophia 2 breakout
(`~/Documents/Development/KiCad/Sophia 2 HDMI Breakout Rev 1.2`) and never renamed. The
footprint and pin mapping are correct for Sophia 3; only the value string is wrong. Worth
fixing before any re-fab, but it does not affect the board.

## What is deliberately not connected

CEC (J1-15), SCL (J1-17), SDA (J1-18) and HEAC (J1-2) have no net, so there is **no
DDC/EDID channel**. The display cannot read the source's capabilities and has to accept the
mode blind. If a panel ever refuses to sync, that is the first thing to look at — not a
routing fault.

J2 pins 1–5 are unconnected by design.

## Fab output

The Fabrication Toolkit plugin writes to `production/`, which is **gitignored** (matching
the other XEBook KiCad repos). The committed package lives in `Fab/`. After regenerating,
copy the useful files across rather than committing `production/` itself.

## Related repositories

Part of the XEBook board family:

- [fujinet-xebook-kicad](https://github.com/sideburn/fujinet-xebook-kicad) — FujiNet main board
- [fujinet-xebook-sd-kicad](https://github.com/sideburn/fujinet-xebook-sd-kicad) — SD card board
- [fujinet-xebook-led-kicad](https://github.com/sideburn/fujinet-xebook-led-kicad) — LED status board
- [xebook-buttonbar-kicad](https://github.com/sideburn/xebook-buttonbar-kicad) — button bar
- `xebook-psu-easyeda` *(private)* — power and audio manager
