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

## Prepare the "Technician Computer"

Before beginning the RetroPie setup process, you will need to download and install some software.

### Download and Install Required Software

1. Download and install **balenaEtcher**.
This software is used to write the Raspberry Pi OS or RetroPie image to a microSD card.

    Link: [balenaEtcher](https://etcher.io/)

    **Note**: this software installs to your user profile, so you should **not** right-click and run it as administrator (i.e., do not run setup elevated)

1. Confirm your system has **OpenSSH** installed.
If it doesn't, install it. This software is used to remote into the Raspberry Pi system once it is online.
It allows us to copy-paste commands to expedite the setup process and make it less error-prone.
    - On the newest versions of Windows, OpenSSH is installed by default.
    - To confirm it's installed, open `Settings` > `System` > `Optional features`
        - If you can't find `Optional Features` under settings: try opening `Settings` > `Apps` > `Optional Features`.
        - Once you are in `Optional Features`, review the list of installed optional features and see if `OpenSSH Client` is installed.
    - If it isn't installed:
        - Next to `Add an optional feature`, click `View features`.
        - Check the checkbox for `OpenSSH Client`. Click `Next`.
        - Continue with the installation.

    **Note**: you can use a different SSH client if you prefer

1. Download and install **NanaZip**. This software is similar to 7-Zip, except it better integrates with Windows 11's updated right-click context menus.
This software is used to extract the Raspberry Pi OS and RetroPie images.

    Link: [NanaZip](https://www.microsoft.com/store/productId/9N8G7TSCL18R?ocid=pdpshare)

1. Download and install the latest version of **Notepad++**.
This software is used to create or edit configuration files, while more easily keeping with the Unix file format.

    Link: [Notepad++](https://notepad-plus-plus.org/download/)

    **Note**: you should download the `Installer` that matches your processor architecture.
    For most people, this will be the `64-bit x64` download.

1. Download the newest **Raspberry Pi OS Lite image**. Raspberry Pi OS Lite is used to update the firmware of the Raspberry Pi.

    Link: [Raspberry Pi OS images](https://www.raspberrypi.com/software/operating-systems/) - please download Raspberry Pi OS **Lite**.

1. Download the newest **RetroPie** image.
RetroPie is the software package that includes the operating system, user interface, emulators, and the base configuration to make retro gaming run well on Raspberry Pi.

    Link: [RetroPie images](https://retropie.org.uk/download/)

    **Note**: take care to download the image that matches your hardware:

    - Raspberry Pi 4B and Compute Module 4 users should download the `Raspberry Pi 4/400` image.
    - Raspberry Pi 3B+ or 3B users should download the `Raspberry Pi 2/3/Zero 2 W` image.
    - Raspberry Pi Zero W users should download the `Raspberry Pi 1/Zero` image.
