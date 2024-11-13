# nrfpill
## Overview
nrfpill is a simple custom development board designed to help users make Bluetooth HID devices. It consists of two main components: the [Seeed Studio XIAO nRF52840](https://www.seeedstudio.com/Seeed-XIAO-BLE-nRF52840-p-5201.html) and the WeAct BlackPill F4x1. Users can run their own applications on the Blackpill and send fixed-format HID data to the XIAO via UART, and the XIAO running Blueism firmware will send the received data to the host via Bluetooth HID.
![nrfpill](https://i.imgur.com/OYeBnak.jpg)

## Building
Making your own nrfpill is very easy, you only need the following parts for assembly:
![nrfpill_building](https://i.imgur.com/dAYtJu9.jpg)
| Num | Part                               | Quantity | Note                                                  |
|-----|------------------------------------|----------|-------------------------------------------------------|
| 1   | WeAct Blackpill F4x1 v2.2 or later | 1        |                                                       |
| 2   | 1x20p male header                  | 2        | Don't need to buy they should come with the Blackpill |
| 3   | Seeed Studio XIAO nRF52840         | 1        | "XIAO nRF52840 Sense" should work but untested        |
| 4   | 1x7p female header                 | 2        |                                                       |
| 5   | 3.7V battery                       | 1        |                                                       |

Solder the pin headers to the two boards according to the pictures below, and solder the battery to the back of the XIAO if you have one, you can find the battery contacts by following Seeed's [documentation](https://wiki.seeedstudio.com/XIAO_BLE/).

Note that there is no battery switch on the XIAO, if a battery switch is needed you will have to design one on the battery power cable.

![nrfpill_building](https://i.imgur.com/EYlbBSV.jpg)

## Pinout
![nrfpill_building](https://i.imgur.com/ST51hbS.png)
| Name   | I/O | DESCRIPTION                                                              | Note |
|--------|-----|--------------------------------------------------------------------------|------|
| 5V     | -   | Connect to Blackpill 5V.                                                 |      |
| GND    | -   | Connect to Blackpill ground.                                             |      |
| 3.3V   | -   | Connect to Blackpill 3V3.                                                |      |
| SCR.L  | O   | Scroll lock status output. It is in logic low when scroll lock triggers. |      |
| CAPS.L | O   | Caps lock status output. It is in logic low when caps lock triggers.     |      |
| NUM.L  | O   | Num lock status output. It is in logic low when num lock triggers.       |      |
| RX     | -   | Connect to Blackpill TX.                                                 |      |
| TX     | -   | Connect to Blackpill RX.                                                 |      |

## LED indicator
There are two types of indicators on the XIAO board: a charging indicator, which is yellow when charging the battery. The other is the RGB indicator, controlled by the Blueism firmware, which is blue when advertising and green when a connection to a peer has been established.

## Charging
Use XIAO's on-board charger to charge battery. Charging current is 50mA.

## Power path
Use XIAO's on-board power path circuit to automatically switch between USB and battery power.

## Flashing XIAO
Follow [Flashing](https://github.com/object-blueism/blueism_firmware/blob/main/docs/flashing.md) guide to flash blueism firmware to XIAO.
