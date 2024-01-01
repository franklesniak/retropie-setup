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

### Supported Locales

The author is based in the United States of America, speaks English (US) and uses an English (US) keyboard layout, and is in the Central US time zone.
Accordingly, the products listed and the instructions in this repository will be US and English-centric.
However, it is possible to complete these steps using alternative languages, locales, etc.

## Required Hardware Accessories/Tools

In addition to the core bill of materials, you will need some additional hardware to support your RetroPie build.

- A **microSD card** is required even if you are planning a build that uses SSD or NVMe storage.
A microSD card is used to load Raspberry Pi OS Lite and update the firmware of your Raspberry Pi.
  - Pretty much any microSD card will do as long as the capacity is greater or equal to 8 GB.
  - If you need to purchase a smaller, lower-cost microSD card **for the sole purpose of updating the Raspberry Pi's firmware**, I recommend this 64 GB one from SanDisk: [SanDisk Ultra 64GB microSD UHS-I Card with A1 Performance Rating - Affiliate Link](https://amzn.to/47j14ET).
  - If you are building a RetroPie system and planning to use the microSD card for storage (as opposed to a SATA or NVMe SSD), you are going to want a larger card.
In this case, I recommend this SanDisk Ultra 1.5TB one: [SanDisk Ultra 1.5TB microSDXC UHS-I card with A1 Performance Rating - Affiliate Link](https://amzn.to/41JNZmH).
Or, for a slightly faster microSD card, get one with an A2 performance rating and slightly less capacity like this Lexar 1TB one: [Lexar PLAY 1TB microSDXC UHS-I card with A2 Performance Rating - Affiliate Link](https://amzn.to/3vqAqwo).
- Likewise, **a microSD card reader** is required. I recommend a USB 3.0 / USB 3.1 Gen 1 / USB 3.2 Gen 1x1 (or better) microSD reader like this inexpensive one from SanDisk: [SanDisk MobileMate USB 3.0 microSD Card Reader - Affiliate Link](https://amzn.to/48i3Ew3).
  - **Note**: if the technician computer only has USB-C ports, you will need an adapter or a different microSD card reader.
Here are some options:
    - USB A to C adapter: [Amazon Basics USB A (female) to USB-C (male) Adapter - Affiliate Link](https://amzn.to/41JMg11)
    - USB C microSD card reader: [Anker SD and microSD Card Reader, USB-C Connector - Affiliate Link](https://amzn.to/41LLKj4)
    - USB A and C microSD card reader (supports both!): [Anker SD and microSD Card Reader, USB-A and USB-C Connectors - Affiliate Link](https://amzn.to/3H40SyD)
- A **USB keyboard and mouse** are required.
If you need to purchase one, it's nothing fancy, but I like this simple, compact, all-in-one unit from Logitech: [Logitech K400 Plus Wireless Keyboard with Touchpad Mouse](https://www.amazon.com/Logitech-Wireless-Keyboard-Touchpad-PC-connected/dp/B014EUQOGK)
- A **precision screwdriver** is required for assembly. If you can find it, I really like this electrostatic discharge-resistant one from Wiha: [Wihi 27324 Phillips Screwdriver with Precision ESD-Safe Dissipative Handle](https://amzn.to/48xjNgS).
- For **Raspberry Pi 4B builds**, a **micro HDMI to full-size HDMI adapter** is needed.
This one from Monoprice works great: [Monoprice Micro HDMI (Male) to Full-Size HDMI (Female) Adapter Cable - Affiliate Link](https://amzn.to/4aDzpkR).
- For builds involving the **Argon One m.2 SATA Expansion Board**, a **USB-A to USB-A cable** is needed.
I have this one, and it's working great for me so far: [AINOPE USB 3.0 A (Male) to USB 3.0 A (Male) Cable, 6.6 Ft. - Affiliate Link](https://amzn.to/3S4CumV).
- For **all builds except handhelds**, a HDMI cable is required.
If you have one, use what you have.
If you need one, I recommend one of the following:
  - 3 Ft.: [Monoprice Certified Ultra High Speed HDMI 2.1 Cable, 3 Ft. - Affiliate Link](https://amzn.to/3H4vTmc)
  - 6 Ft.: [Monoprice Certified Ultra High Speed HDMI 2.1 Cable, 6 Ft. - Affiliate Link](https://amzn.to/41HNrxI)
  - 10 Ft.: [Monoprice Certified Ultra High Speed HDMI 2.1 Cable, 10 Ft. - Affiliate Link](https://amzn.to/4aJqSNt)
- For **all builds except handhelds**, you're also going to need **a TV or computer monitor** that supports an HDMI connection.
I hope that you already have one of these!
But, if you need a recommendation for a TV, you can't go wrong with an 83-inch LG C3 OLED: [LG C3 Series 83-Inch OLED TV - Affiliate Link](https://amzn.to/3tBKcLG) - **be sure to purchase one shipped and sold by Amazon**.
- If you are building a non-handheld build, and if your setup supports it, an Ethernet cable.
Use what you already have - but if you need to purchase one, I recommend one of the following:
  - 3 Ft: [C2G Legrand CAT6a Ethernet Cable, Snagless Unshielded, Black, 3 Ft. - Affiliate Link](https://amzn.to/3NM1OLD)
  - 6 Ft.: [C2G Legrand CAT6a Ethernet Cable, Snagless Unshielded, Black, 6 Ft. - Affiliate Link](https://amzn.to/3tBrGmO)
  - 10 Ft.: [C2G Legrand CAT6a Ethernet Cable, Snagless Unshielded, Black, 10 Ft. - Affiliate Link](https://amzn.to/3NHPtrN)
  - Other sizes available at the above links)

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

## Update the Raspberry Pi's Firmware

These steps are **required on Raspberry Pi 4B-based builds that use SATA or NVMe storage** (e.g., the Argon ONE m.2 case). They should be considered **optional for all other Raspberry Pi builds**.

### Prepare the microSD Card with a Raspberry Pi OS Lite Image

1. On the technician computer, extract the Raspberry Pi OS Lite `.img.xz` file:
    - Right-click on the `.img.xz` file, then click `NanaZip` > `Extract to "[year]-[month]-[date]-raspios-[version]-[platform]-lite.img\"`.
1. Use balenaEtcher to load the image file onto your microSD card
    - Insert your microSD card into the technician computer and open balenaEtcher.
    - In balenaEtcher, select `Flash from file`, then navigate to and select the image file you extracted.
It should be in the `[year]-[month]-[date]-raspios-[version]-[platform]-lite.img` folder.
    - Click `Select target` then make sure the checkbox is checked next to your microSD card reader.
Click `Select 1`, then click `Flash!`.
    - You may receive a warning that the drive you selected is `unusually large`.
If you have a large storage device, this is expected.
Click `Yes, I'm sure`.
    - You may receive a User Account Control (UAC) prompt to provide balenaEtcher with the required permissions to flash the microSD card.
Approve the prompt and/or enter credentials when needed.
    - Close balenaEtcher when done.

### Perform Initial Wireless Configuration

These steps are only necessary if you intend to connect the Raspberry Pi to a Wi-Fi connection instead of a wired (Ethernet) connection.

**Note**: you must know your wireless SSID and password _exactly_ (including the correct capitalization) to complete these steps.

1. Remove and reconnect the microSD card to the Windows computer.
1. Create the wireless settings file:
    - Open Notepad++
    - Click the icon to create a new file (or navigate to the `File` menu and click `New`).
    - Click on the `Edit` menu, then click `EOL Conversion` > `Unix (LF)`
    - Paste in template WiFi settings:

        ```text
        ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
        update_config=1
        country=US

        network={
        scan_ssid=1
        ssid="MyNetworkSSID"
        psk="WiFiPasswordHere"
        key_mgmt=WPA-PSK
        identity="home"
        }

        ```

    - Replace `MyNetworkSSID` with the name of your wireless network's SSID.
    - Replace `WiFiPasswordHere` with the pre-shared key of your wireless network.
    - **Note**: for other types of wireless networks, review the reference material [here](https://w1.fi/cgit/hostap/plain/wpa_supplicant/wpa_supplicant.conf).
1. If you want to configure one or more additional wireless networks:
    - Add another `network={}` section by copying and pasting the template above, and then updating the values for the SSID and wireless password as noted previously.
    - Make sure that the identity text for each wireless network is unique (e.g., "home", "work", etc.).
1. Save the file.
    - In the `Save As` dialog, box, change the `Save as type` to `All types`.
    - Then, when prompted for a file name, with the microSD card still attached, navigate to the boot drive that appears in Computer (it may be labeled as `bootfs`).
    - Enter the file name:

      `wpa_supplicant.conf`

      and then click `Save`.

Keep Notepad++ open for the next step.

**Note**: to read more about this process, see [this guide for preparing a microSD card for Wi-Fi](https://raspberrypi.stackexchange.com/a/57023/78201)

### Enable SSH at the First Boot of the Raspberry Pi

Secure Shell (SSH) is a remote access protocol that we will use to connect to the Raspberry Pi from the technician computer.

1. If you haven't already done so, remove and reconnect the microSD card to the Windows computer.
1. Create the SSH file:
    - If it isn't already started, start Notepad++ on the technician computer.
    - Click the icon to create a new file (or navigate to the `File` menu and click `New`).
    - Leave the file blank/empty.
1. Save the file.
    - In the `Save As` dialog, box, change the `Save as type` to `All types`.
    - Then, when prompted for a file name, with the microSD card still attached, navigate to the boot drive that appears in Computer (it may be labeled as `bootfs`).
    - Enter the file name:

      `ssh`

      and then click `Save`.
1. "Eject" and then remove the microSD card from the technician computer.
    - In the _Notification Area_ or _System Tray_, find the icon for `Safely Remove Hardware and Eject Media`. `Right-click` on it, then click `Eject bootfs (E:)` - or a similarly named item related to the installed microSD card.
    - In a few moments, you should receive a `Safe to remove hardware` notification. Remove the microSD card.
    - If you do not receive the `Safe to remove hardware` notification, close all programs,  Windows Explorer windows, and Terminal/Command Prompt/PowerShell windows that could be using the drive, then try again.
    - If you still cannot safely remove the microSD card and are confident that every relevant program has been closed, remove the drive anyway.

### Setup and Boot Up the Raspberry Pi

1. Insert the microSD card into the Raspberry Pi.
1. Connect the Raspberry Pi to a monitor or TV using an HDMI cable.
1. Connect a USB keyboard to the Raspberry Pi.
1. Optionally, connect an Ethernet cable to the Raspberry Pi.
1. Connect a power cable to the Raspberry Pi.
After a few moments, it will power on. The Raspberry Pi will take a few minutes to complete its initialization process.

### Complete the Initial Operating System Configuration

1. After a few minutes, you will be prompted to select a keyboard layout.
    - Use the down arrow key to select `Other`, then press **Enter**.
    - Use the down arrow key to select `English (US)`, then press **Enter**.
    - Use the up arrow key to select `English (US)` again, then press **Enter**.
2. Create a set of credentials
    - When prompted to enter a new username, enter one (e.g., enter `flesniak`), then press **Enter**.
    - When prompted, enter a password, then press **Enter**.
    - Enter the password again, then press **Enter**.
3. Login to the Raspberry Pi
    - After a few seconds, a `raspberrypi login` prompt will appear.
Enter your username, then press **Enter**.
    - Enter your password, then press **Enter**.

