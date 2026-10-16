# Sophia 3 Micro HDMI Breakout

A small adapter board that carries the **Sophia 3** digital-video output from its 16-pin
header to a panel-mountable **micro HDMI (Type D)** connector, for the
[XEBook](https://xebook.sideburn.com) Atari 8-bit laptop build.

[Sophia](http://spiflash.org/sophia.html) is Dr. Sławomir "Simius" Ryszkowski's GTIA
replacement for Atari 8-bit computers; Sophia 3 outputs digital video directly. In the
XEBook the display is a 13.3" 1920×1080 IPS panel driven over micro HDMI, and this board is
what gets the signal from the Sophia 3 to that cable in the space available.

Passive — two connectors and copper, no active components.

## What's on it

- **J2** — 1×16 header, TE Connectivity `1-215079-6`, mating the Sophia 3's output row
- **J1** — micro HDMI Type D receptacle, Molex 46765 footprint
- Two-layer board, TMDS pairs routed as differential pairs

## Pin mapping

| J2 pin | Signal | J1 (micro HDMI) |
|---|---|---|
| 1–5 | *not connected* | — |
| 6, 7 | Ground / TMDS shield | 4, 7, 10, 13, 16 |
| 8 | +5V | 1, 19 |
| 9 | TMDS Data2+ | 3 |
| 10 | TMDS Data2− | 5 |
| 11 | TMDS Data1+ | 6 |
| 12 | TMDS Data1− | 8 |
| 13 | TMDS Data0+ | 9 |
| 14 | TMDS Data0− | 11 |
| 15 | TMDS Clock+ | 12 |
| 16 | TMDS Clock− | 14 |

Ground arrives on J2 pins 6 and 7 and fans out to all four TMDS shield pins. The HDMI
connector's **CEC (15), SCL (17), SDA (18) and HEAC (2) are left unconnected** — there is no
DDC/EDID path, so the attached display has to accept the incoming mode without negotiating
it. J1 pins 1 and 19 share the +5V net.

## Layout

```
Sophia 3 Micro HDMI.kicad_sch / .kicad_pcb / .kicad_pro   KiCad 9 source
Fab/            Fabrication package — gerber zip, BOM, positions, IPC netlist
docs/           jlcBOM.txt
freerouting.dsn Freerouting export used while routing
```

## Status

Fabricated and in service — this is the display interface in shipping XEBook builds.

## Tooling

KiCad 9. Fab package generated with the Fabrication Toolkit plugin (its `production/`
output directory is gitignored; the curated copy lives in `Fab/`).

## License

[CERN Open Hardware Licence Version 2 - Strongly Reciprocal](LICENSE) (CERN-OHL-S-2.0),
matching the other XEBook board repositories.

Sophia itself is a separate commercial product and is **not** covered by this license — this
repository is only the adapter board that plugs into it.
