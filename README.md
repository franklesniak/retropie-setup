# RetroPie Setup Guide

Step-by-step instructions for building a RetroPie, a Linux-based video game console used to play retro games

## Supported Hardware and Software

This guide covers the following hardware-software combinations:

### Supported Cases

**Game Console Form Factor:**

- Argon ONE m.2 case (i.e., Argon ONE v2 + Argon ONE m.2 SATA Expansion Board) (Raspberry Pi 4B, 2-8 GB RAM only)
- RetroFlag NesPi 4 case (with SATA SSD installed in "cartridge") (Raspberry Pi 4B, 2-8 GB RAM only)
- RetroFlag NesPi+ case (Raspberry Pi 3B+ or Raspberry Pi 3B only)

**Arcade Cabinet Form Factor:**

- Pimoroni Picade with a MonkMakes Squid button, with either a USB-attached SSD or a microSD card

**Handheld Form Factor:**

- ExperimentalPi PiBoy DMG (Raspberry Pi 4B, Raspberry Pi 3B, or Raspberry Pi Zero W only)
- RetroFlag GPi Case with Retro Game Restore GPiMate Plus for CM4 Lite (Raspberry Pi Compute Module 4 Lite, 2-8 GB RAM, no eMMC, with Wi-Fi only)
- RetroFlag GPi Case 2W (Raspberry Pi Zero 2W or Zero W only)
- RetroFlag GPi case (Raspberry Pi Zero W only)

**Other:**

- Generic case (or no case), with sufficient cooling

### Supported Computers

Subject to the limitations noted in the cases section, the following computers are supported by this guide:

- Raspberry Pi 4B, 2-8 GB RAM
- Raspberry Pi Compute Module 4 Lite, 2-8 GB RAM, no eMMC, with Wi-Fi
- Raspberry Pi 3B+
- Raspberry Pi 3B
- Raspberry Pi Zero 2W
- Raspberry Pi Zero W

**Note:** RetroPie does not yet support the Raspberry Pi 5.

**Note #2:** If you are trying to set up RetroPie on an x86 (Intel or AMD) system, please consider using Ubuntu Server and see [this guide](https://github.com/franklesniak/RetroPie-Setup-Ubuntu/tree/Support-Ubuntu-22dot04).

### Supported Operating Systems

- RetroPie 4.8

**Note:** If you are trying to set up RetroPie on a Ubuntu or Ubuntu Server system, please see [this guide](https://github.com/franklesniak/RetroPie-Setup-Ubuntu/tree/Support-Ubuntu-22dot04).

### Supported "Technician Computer" Operating Systems

The "technician computer" is a computer different than the one that will be used to run emulation software.
It is used to bootstrap the overall setup process and it is where some configuration activities are performed.

- Windows 11

**Note:** Other technician computer operating systems will certainly work; however, this guide is not written for them.

