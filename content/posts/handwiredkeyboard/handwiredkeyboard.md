+++
title = "Handwiring my own Ortholinear Keyboard"
date = "2026-08-22"
category = "keyboard, soldering, 3dprint"
+++

![Image alt](/handwiredkeyboard.jpg)

Was looking at making my own keyboard for a long time, but after getting a 3d-printer I decided to try.

From [Printables](https://www.printables.com) I have found a 3d-print file for an compact ortholinear keyboard I wanted to build [A⋅TE⋅B1 Ortholinear Keyboard](https://www.printables.com/model/670107-ateb1-ortholinear-keyboard) so I printed it on my 3d printer [Creality Ender 3 Max](https://www.creality.com/products/ender-3-max-3d-printer) with Black PLA 1.75mm filament.

# Parts I used
- 3d printed case
- Electric wire - [Sparkfun Hook-Up Wire Kit](https://www.sparkfun.com/hook-up-wire-assortment-stranded-22-awg.html)
- USB-C Arduino Pro Micro (ATmega32U4) from Aliexpress
- 59 Keychron Z114 Gateron Phantom Switch - Yellow
- 59 1N4148 diodes
- Glorious Aura Keycaps v2 - Pixel Pink
## Parts not used
- 2 Stabilisers
- 4 M2 screw inserts + 4 M2x8mm screws

# Tools
- 3d printer ([Creality Ender 3 Max](https://www.creality.com/products/ender-3-max-3d-printer)) + Black PLA 1.75mm Filament
- Soldering iron [PINECIL V2](https://pine64.com/product/pinecil-smart-mini-portable-soldering-iron/) + lead free solder + Helping hands + Blue soldering mat
- Wire stripper + Wire cutter
- Tweezers from [iFixit Pro Tech Toolkit](https://www.ifixit.com/products/pro-tech-toolkit)

# Assembly
After putting in all the key switches, I bended, cut, and soldered diodes on the key switches then to each other (row).
| Setup | Closeup |
|:--:|:--:|
| ![Image alt](/handwiredkeyboard1.jpg) | ![Image alt](/handwiredkeyboard2.jpg) |

| Soldered (column) wires | Then soldered wires to each column and row |
|:--:|:--:|
| ![Image alt](/handwiredkeyboard3.jpg) | ![Image alt](/handwiredkeyboard4.jpg) |

| Finally to the controller, which I recommend mounting properly | Some wastes: wire, wire insulator, diode legs, diode packaging |
|:--:|:--:|
| ![Image alt](/handwiredkeyboard5.jpg) | ![Image alt](/handwiredkeyboard6.jpg) |

I decided to sand the 3d print

After painstakingly painter taping each key switch I spray painted couple coats of white primer on.

In hindsight should've sanded & spray painted before installing the hardware

Installed the Keycaps

# Software
Flashed [QMK](https://docs.qmk.fm/) firmware to the controller with the [Keyboard config for A⋅TE⋅B1](https://github.com/djvanderlaan/ate/tree/main/b1). Entering the flash mode with a pair of tweezers.

# Finished product
![Image alt](/handwiredkeyboard7.jpg)

