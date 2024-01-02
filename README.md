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

### Supported "Technician's Computer" Operating Systems

The "technician's computer" is a computer different than the one that will be used to run emulation software.
It is used to bootstrap the overall setup process and it is where some configuration activities are performed.

- Windows 11

**Note:** Other technician's computer operating systems will certainly work; however, this guide is not written for them.

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
  - **Note**: if the technician's computer only has USB-C ports, you will need an adapter or a different microSD card reader.
Here are some options:
    - USB A to C adapter: [Amazon Basics USB A (female) to USB-C (male) Adapter - Affiliate Link](https://amzn.to/41JMg11)
    - USB C microSD card reader: [Anker SD and microSD Card Reader, USB-C Connector - Affiliate Link](https://amzn.to/41LLKj4)
    - USB A and C microSD card reader (supports both!): [Anker SD and microSD Card Reader, USB-A and USB-C Connectors - Affiliate Link](https://amzn.to/3H40SyD)
- A **USB keyboard and mouse** are required.
If you need to purchase one, it's nothing fancy, but I like this simple, compact, all-in-one unit from Logitech: [Logitech K400 Plus Wireless Keyboard with Touchpad Mouse](https://www.amazon.com/Logitech-Wireless-Keyboard-Touchpad-PC-connected/dp/B014EUQOGK)
- A **precision screwdriver** is required for assembly. If you can find it, I really like this electrostatic discharge-resistant one from Wiha: [Wihi 27324 Phillips Screwdriver with Precision ESD-Safe Dissipative Handle](https://amzn.to/48xjNgS).
- For **Raspberry Pi 4B builds**, a **micro HDMI to full-size HDMI adapter** is needed.
This one from Monoprice works great: [Monoprice Micro HDMI (Male) to Full-Size HDMI (Female) Adapter Cable - Affiliate Link](https://amzn.to/4aDzpkR).
- For builds involving the **Argon ONE m.2 SATA Expansion Board**, a **USB-A to USB-A cable** is needed.
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

## Prepare the "Technician's Computer"

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

1. On the technician's computer, extract the Raspberry Pi OS Lite `.img.xz` file:
    - Right-click on the `.img.xz` file, then click `NanaZip` > `Extract to "[year]-[month]-[date]-raspios-[version]-[platform]-lite.img\"`.
1. Use balenaEtcher to load the image file onto your microSD card
    - Insert your microSD card into the technician's computer and open balenaEtcher.
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

### Perform Initial Wireless Configuration on Raspberry Pi OS Lite

These steps are only necessary if you intend to connect the Raspberry Pi to a Wi-Fi connection instead of a wired (Ethernet) connection.

**Note**: you must know your wireless SSID and password _exactly_ (including the correct capitalization) to complete these steps.

1. Remove the microSD card from the card reader, then reconnect it.
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

**Note**: to read more about this process, see [this guide for preparing a microSD card for Wi-Fi](https://raspberrypi.stackexchange.com/a/57023/78201).

### "Eject" and Then Remove the microSD card from the Technician's Computer

1. In the _Notification Area_ or _System Tray_, find the icon for `Safely Remove Hardware and Eject Media`. `Right-click` on it, then click `Eject bootfs (E:)` - or a similarly named item related to the installed microSD card.
1. In a few moments, you should receive a `Safe to Remove Hardware` notification. Remove the microSD card.
1. If you do not receive the `Safe to remove hardware` notification, close all programs,  Windows Explorer windows, and Terminal/Command Prompt/PowerShell windows that could be using the drive, then try again.
1. If you still cannot safely remove the microSD card and are confident that every relevant program has been closed, remove the drive anyway.

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

### Update the Raspberry Pi, Including its Firmware

**Note**: these steps assume that you are installing the latest stable firmware release (recommended).
If, for some reason, you need to install a beta firmware instead of the latest stable release, check out [the rpi-update project](https://github.com/raspberrypi/rpi-update).

1. At the terminal prompt, type the following commands:

    ```bash
    sudo apt update
    sleep 2
    sudo apt -y dist-upgrade

    ```

1. When the process completes, type the following command:

    `sudo reboot`

### Shut Down the Raspberry Pi

1. After the reboot completes, enter your username and password to log back in.
1. At the terminal prompt, type the following command:

    `sudo shutdown now`

### Disconnect the Power and the microSD Card

When the Raspberry Pi completes its shutdown, remove the power cable, and then remove the microSD card.

## Copy RetroPie to Its Storage Device and Configure It

### Connect the RetroPie Storage Device to the Technician's Computer

By default, Raspberry Pis boot from microSD.
However, Raspberry Pi 2B v1.2, Raspberry Pi 3B, 3B+, 3A+, and Raspberry Pi 4B support boot from USB.

The Raspberry Pi 4B supports USB 3.0 / USB 3.1 Gen 1 / USB 3.2 Gen 1x1, making USB-attached storage notably more performant and capacious compared to microSD card options.

In any case, the choice of RetroPie storage device referenced in this section will depend on the selected case.
For example, using the Argon ONE m.2 SATA Expansion Board would result in you deciding to boot from USB using the m.2 SATA Expansion Board as the USB device.

#### Argon ONE m.2 Case Storage Device Setup

If you are building a RetroPie using the Argon ONE m.2 case, please install the m.2 SATA drive into the Argon ONE m.2 SATA Expansion Board by following the instructions supplied with the Expansion Board.
Next, connect the Argon ONE m.2 SATA Expansion Board to the technician's computer by using a USB-A to USB-A cable.

### Prepare the RetroPie Storage Device with the RetroPie Image

1. On the technician's computer, extract the RetroPie `.img.gz` file:
    - Right-click on the `.img.gz` file, then click `NanaZip` > `Extract to "retropie-[version]-[platform].img\"`.
1. Use balenaEtcher to load the image file onto your microSD card
    - Open balenaEtcher on the technician's computer.
    - In balenaEtcher, select `Flash from file`, then navigate to and select the RetroPie image file you extracted.
It should be in the `retropie-[version]-[platform].img` folder.
    - Click `Select target` then make sure the checkbox is checked next to your microSD card reader.
Click `Select 1`, then click `Flash!`.
    - You may receive a warning that the drive you selected is `unusually large`.
If you have a large storage device, this is expected.
Click `Yes, I'm sure`.
    - You may receive a User Account Control (UAC) prompt to provide balenaEtcher with the required permissions to flash the microSD card.
Approve the prompt and/or enter credentials when needed.
    - Close balenaEtcher when done.

### Disconnect and Reconnect the RetroPie Storage Device; Start Notepad++

1. Remove the RetroPie storage device from the technician's computer.
1. If the device is the Argon ONE m.2 SATA Expansion Board, wait two minutes.
1. Reconnect the storage device to the technician's computer.
1. If it isn't already open, start Notepad++. on the technician's computer.
1. On the technician's computer, open `Computer` and wait for the `boot` drive to appear.
It may take up to five minutes.
1. If, after five minutes, the boot drive has not appeared, then continue with these steps:
    - On the technician's computer, open an elevated Command Prompt.
You may do this by clicking `Start` and typing:

      `cmd`

      and then right-clicking `Command Prompt`, and clicking `Run as administrator`.
You may receive a User Account Control (UAC) prompt to provide the required permissions.
    - Next, at the Command Prompt, type:

      `diskpart`

      Wait for diskpart to start. It may take a few minutes.

    - Next, at the `diskpart` prompt, type:

      `list volume`

    - A list of volumes will appear. Look for a 256 MB volume and note its volume number.
    - Determine if the volume has a letter (`Ltr`) assigned.
If it does, then try accessing the storage device from Windows Explorer (`Computer`) again.
    - If it does not have a drive letter assigned, type:

      `select volume 6`

      (replace `6` with the number of the volume).
Next, type:

      `assign letter=G`

      (replace `G` with an available drive letter)
    - Verify the drive is accessible in Windows Explorer (`Computer`).
If it is, in the Command Prompt, type:

      `exit`

### Perform Initial Wireless Configuration on RetroPie

These steps are only necessary if you intend to connect the RetroPie to a Wi-Fi connection instead of a wired (Ethernet) connection.

**Note**: you must know your wireless SSID and password _exactly_ (including the correct capitalization) to complete these steps.

1. Create the wireless settings file:
    - In Notepad++, click the icon to create a new file (or navigate to the `File` menu and click `New`).
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
    - Then, when prompted for a file name, with the storage device still attached, navigate to the boot drive that appears in Computer (it will be labeled as `boot`).
    - Enter the file name:

      `wpa_supplicant.conf`

      and then click `Save`.

Keep Notepad++ open for the next step.

**Note**: to read more about this process, see [this guide for preparing a Raspberry Pi for Wi-Fi](https://raspberrypi.stackexchange.com/a/57023/78201).

### Enable SSH at the First Boot of the Raspberry Pi

Secure Shell (SSH) is a remote access protocol that we will use to connect to the Raspberry Pi from the technician's computer.

1. Create the SSH file:
    - In Notepad++, click the icon to create a new file (or navigate to the `File` menu and click `New`).
    - Leave the file blank/empty.
1. Save the file.
    - In the `Save As` dialog, box, change the `Save as type` to `All types`.
    - Then, when prompted for a file name, with the RetroPie storage device still attached, navigate to the boot drive that appears in Computer (it will be labeled as `boot`).
    - Enter the file name:

      `ssh`

      and then click `Save`.

### "Eject" and Then Remove the RetroPie Storage Device from the Technician's Computer

1. In the _Notification Area_ or _System Tray_, find the icon for `Safely Remove Hardware and Eject Media`. `Right-click` on it, then click `Eject boot (G:)` - or a similarly named item related to the connected storage device.
1. In a few moments, you should receive a `Safe to Remove Hardware` notification. Disconnect the RetroPie storage device.
1. If you do not receive the `Safe to Remove Hardware` notification, close all programs,  Windows Explorer windows, and Terminal/Command Prompt/PowerShell windows that could be using the storage device, then try again.
1. If you still cannot safely remove the RetroPie storage device and are confident that every relevant program has been closed, disconnect the drive anyway.

## Install the Raspberry Pi Into Its Case and Set it Up

### Raspberry Pi Case Installation

The procedure here varies based on the type of case that you are using - but, generally, you should follow the manufacturer's instructions.

Here are a few case-specific notes:

#### Argon ONE m.2 Case Assembly

- Keep the Power Button Management Mode jumper set to pins 1-2, the default setting (also known as mode 1).
- Instead of using the plain, plastic case bottom, attach the Argon ONE m.2 SATA Expansion Board to the bottom of the case.
- Don't worry about the Argon ONE Pi 4 v2 Power Button and Fan Control software - we will address this a little later

### Install Controller Firmware Updates

#### Xbox Controller Firmware Update

The easiest way to do this is to use your Xbox.

If you don't have an Xbox or don't want to use it, follow these steps:

1. On the technician's computer, open the Microsoft Store.
Then, install the [Xbox Accessories app](https://apps.microsoft.com/detail/9NBLGGH30XJ3?rtc=1&hl=en-us&gl=US).

2. Update the controller firmware.
    - Launch the Xbox Accessories app
    - Plug in the Xbox controller to the technician's computer via USB.
    - The app should tell you if a firmware update is available - press the `...` button to be sure.
    - Repeat for any other Xbox controllers.

### Connect the Storage Device, Display, and Peripherals and Turn on the RetroPie

As the header indicates, this is the step where you connect the required cables.
Optionally, you could also connect a wired Ethernet cable.

Here are some case-specific notes:

#### Argon ONE m.2 Cabling and Power-On

- Use the USB A-USB-A bridge to attach the Argon ONE m.2 SATA Expansion Board to the Raspberry Pi
- Connect a USB keyboard and the TV or computer monitor (via HDMI).
- Optionally, connect a wired Ethernet cable.
- Attach the power adapter, then press the power button on the rear of the unit (above the Ethernet port).

## Complete the First Boot and Connect to the RetroPie Using SSH

Now that you have powered on the RetroPie, it will complete its initialization and reboot several times.
When you arrive at a screen that says, `Welcome` and `Hold a button on your device to configure it.`, the initialization process is complete.

### Handhelds Only: Complete Controller Setup

This is a placeholder.

### Get the IP Address of the Raspberry Pi

The procedure for obtaining the Raspberry Pi's IP address varies depending on whether your RetroPie is installed in a handheld case.

#### Handhelds Only: Use the RetroPie Menu to Get the IP Address

- Using the D-pad on the controller, select RetroPie Configuration, then press A (rightmost button).
- Use the D-pad to scroll down to Show IP, then press A.
- After about 15-45 seconds, the IP address information will display.
- The IP address is noted as the very first line in the gray box (for example:
`Your IP is: 10.1.2.120`).
- Make note of the IP address; you will need it in subsequent steps.
- Press A.

#### All Other Systems: Use the Keyboard to Get the IP Address

On the USB keyboard attached to the RetroPie, press **F4**.
EmulationStation (the graphical interface) should quit, leaving you at a terminal prompt.

At the terminal prompt, type:

`ip addr show`

If you are using a wired Ethernet connection, your RetroPie's IP address will be listed next to the `inet` keyword beneath `eth0`.

If you are using wireless (Wi-Fi), your RetroPie's IP address will be listed next to the `inet` keyword beneath `wlan0`.

Take note of the IP address, as you will need it for the next step.

### Connect to the RetroPie using SSH

1. On the technician's computer, open a Command Prompt:
    - Click `Start`, then type:

      `cmd`

    `Command Prompt` will appear in the search results. Press **Enter** to start it.
1. At the Command Prompt, type:

      `ssh 10.1.2.120 -l pi`

    (replace 10.1.2.120 with the IP address noted previously).
Press **Enter**.
1. You should receive a prompt like the following:

      ```text
      The authenticity of host '10.1.2.51 (10.1.2.51)' can't be established.
      ED25519 key fingerprint is SHA256:3sD13XzoMsfqnf2GiGwM5LOpEm7VkZAobdb0qQDQl+g.
      This key is not known by any other names
      Are you sure you want to continue connecting (yes/no/[fingerprint])?
      ```

    In response to this prompt, type `yes` and then press **Enter**.
1. Enter the following password: `raspberry` (then press **Enter**).
1. The connection to the RetroPie will be established.
Effectively, this Command Prompt on the technician's computer is equivalent to the terminal prompt on the RetroPie.
The term "terminal prompt" will now be used interchangeably to mean either the SSH prompt on the technician's computer or the prompt on the RetroPie.

## Configure and Update the RetroPie System

### Set the Keyboard Layout to English (US)

1. At the terminal prompt, type:

    `sudo editor /etc/default/keyboard`

    (then press **Enter**)

1. Use the keyboard's arrow keys to navigate to the line that reads:

    `XKBLAYOUT="gb"`

    Modify this line so that it reads:

    `XKBLAYOUT="us"`

1. Press **Ctrl** and **O** simultaneously to save the file, then press **Enter** to confirm the file name.
1. Press **Ctrl** and **X** simultaneously to exit Editor.

### Set the Time Zone

1. At the terminal prompt, type:

    `sudo raspi-config`

    (then press **Enter**).
The `Raspberry Pi Software Configuration Tool (raspi-config)` starts.
1. Use the keyboard's arrow keys to select option `5` (`Localisation Options`), then press **Enter**.
1. Use the keyboard's arrow keys to select option `L2` (`Configure time zone`), then press **Enter**.
1. Use the keyboard's arrow keys to select `US`, then press **Enter**.
1. Use the keyboard's arrow keys to select your US time zone, then press **Enter**.
1. Keep `Raspi-Config` open, as it will be used in the next step.

### Change the RetroPie's Hostname

1. In `Raspi-Config`, use the keyboard's arrow keys to select option `1` (`System Options`), then press **Enter**.
1. Use the keyboard's arrow keys to select option `S4` (`Hostname`), then press **Enter**.
1. Press **Enter** to acknowledge the warning.
1. Use the **Backspace** key to clear the current hostname.
Replace it with a new one, keeping the new one 15 characters or less.
Press **Enter** when done.
1. Keep `Raspi-Config` open, as it will be used in the next step.

### Change the Default Password and Reboot

1. In `Raspi-Config`, use the keyboard's arrow keys to select option `1` (`System Options`), then press **Enter**.
1. Use the keyboard's arrow keys to select option `S3` (`Password`), then press **Enter**.
1. Press **Enter** to confirm.
1. At the `New password:` prompt, type the password that you would like to use, then press **Enter**.
1. At the `Retype new password:` prompt, type the password one more time, then press **Enter**.
1. Press **Enter** to acknowledge that the password was changed successfully.
1. Use the keyboard's left-right arrow keys to select `Finish`, then press **Enter**.
Press **Enter** again to confirm that we would like to reboot now.

### Wait a Bit, then Reconnect to the RetroPie via SSH

The RetroPie system will reboot.
When it completes, you will arrive at a familiar EmulationStation screen.
Repeat the steps noted earlier to connect to the RetroPie from the technician's computer using SSH -- except this time, you should not receive a confirmation prompt about the SSH key, and you will need to use the updated password that you just set.

### Encrypt the Wireless Password(s)

If you are using a Wi-Fi connection for the RetroPie, the wireless passwords defined earlier are stored in plain text -- this is not a good security practice.
Therefore, we will follow these steps to encrypt the password.

1. At the terminal prompt, type:

    `wpa_passphrase WirelessSSID`

    (replace `WirelessSSID` with the actual SSID of your wireless network, including the correct capitalization, then press **Enter**)
1. Enter the pre-shared key (wireless password), then press **Enter**
1. The command returns an encrypted psk.
Use the mouse to highlight the encrypted key (which looks like a long series of numbers and letters).
Once highlighted, press **Enter** to copy it to the clipboard.
1. On the technician's computer, open Notepad/Notepad++ and paste the text to store it temporarily.
    - **Note**: if you have multiple wireless networks configured, repeat the above steps for each wireless network
1. At the terminal prompt, type:

    `sudo editor /etc/wpa_supplicant/wpa_supplicant.conf`

1. Use the keyboard's arrow keys to navigate to the line that looks like:

    `psk="WiFiPasswordHere"`

1. Replace the existing psk line with a new one like:

    `psk=1234567890abcdef1234567890abcdef`

    (right click to paste the text from the clipboard, and be sure to remove the quotation marks)
    - **Note**: If you have multiple wireless networks configured, replace the PSK for the remaining wireless networks with the respective encrypted key.
1. Press **Ctrl** and **O** simultaneously to save the file, then press **Enter** to confirm the file name.
1. Press **Ctrl** and **X** simultaneously to exit Editor.
1. Reboot the RetroPie by typing the following at the terminal prompt:

    `sudo reboot`

    (then press **Enter**).
1. The RetroPie system will reboot.
When it completes, you will arrive at a familiar EmulationStation screen.
Repeat the steps noted earlier to connect to the RetroPie from the technician's computer using SSH.

### Set a Password for Network File Access (SMB)

1. At the terminal prompt, type:

    `sudo smbpasswd -a pi`

    (then press **Enter**).
1. Next, when prompted for `New SMB password`, type the same password entered previously and press **Enter** when done.
1. When prompted to `Retype new SMB password`, type the password again and press **Enter** when done.

### Set the Locale to English (US)

1. At the terminal prompt, type:

    `sudo raspi-config`

    (then press **Enter**).
1. Use the keyboard's arrow keys to select option `5` (`Localisation Options`), then press **Enter**.
1. Keep option `L1` (`Locale`) selected, then press **Enter**.
1. Use the keyboard's arrow keys and/or the **Page Up** and **Page Down** keys to scroll down to `en_GB.UTF-8 UTF-8`.
Press **Space** to unselect `en_GB.UTF.8 UTF-8`.
1. Use the keyboard's arrow keys and/or the **Page Up** and **Page Down** keys to scroll down to `en_US.UTF-8 UTF-8`.
Press **Space** to select `en_US.UTF.8 UTF-8`.
1. Press **Enter**.
1. On the next screen, select `en_US.UTF-8` and press **Enter**.
1. Wait for locale generation to complete.
When completed, use the keyboard's left-right arrow keys to select `Finish`, then press **Enter**.
1. Reboot the RetroPie by typing the following at the terminal prompt:

    `sudo reboot`

    (then press **Enter**).
1. The RetroPie system will reboot.
When it completes, you will arrive at a familiar EmulationStation screen.
Repeat the steps noted earlier to connect to the RetroPie from the technician's computer using SSH.

### Configure Case-Specific Software Components

The procedure here varies depending on which case you are using for your RetroPie build:

#### Argon ONE Software Configuration

1. At the terminal prompt, type:

    `wget -O get_argononed.sh https://gitlab.com/DarkElvenAngel/argononed/-/raw/master/get_argononed.sh`

    (the above is all one line - once entered, press **Enter**).
1. At the terminal prompt, type:

    `sudo bash get_argononed.sh`

    (then press **Enter**).
1. Press **1** and then **Enter** to `Install Stable version`.
1. When you see `Complete`, press **Enter** a couple of times to clear the buffer.
1. Reboot the RetroPie by typing the following at the terminal prompt:

    `sudo reboot`

    (then press **Enter**).
1. The RetroPie system will reboot.
When it completes, you will arrive at a familiar EmulationStation screen.
1. Wait approximately one additional minute.
1. Test "graceful reboot" by pressing the power button twice.
1. The RetroPie system will reboot.
When it completes, you will arrive at a familiar EmulationStation screen.
1. Wait approximately one additional minute.
1. Test "soft shutdown" by pressing and holding down the power button for just over three seconds (but not five seconds or more).
1. The RetroPie system will shut down and then power off.
Press the power button to turn it back on.
1. When the RetroPie boots up, you will arrive at a familiar EmulationStation screen.
1. Repeat the steps noted earlier to connect to the RetroPie from the technician's computer using SSH.
1. Once reconnected, type the following command:

    `sudo argonone-cli --decode`

    (then press **Enter**).
Verify that the output indicates a current temperature and no obvious errors.
