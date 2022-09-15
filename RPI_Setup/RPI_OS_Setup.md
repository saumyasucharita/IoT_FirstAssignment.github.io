**Raspberry PI set up via wifi**

**Laptop information**
System manufacturer: Dell Inc
System Model: XPS 13 7390
OS Name: Microsoft Windows 10 Home
Having micro SD card slot

**Router information**
Type: Travel Router
Brand:	GL.iNet
Model Name:	GL-MT300N-V2
Wireless Communication Standard:	802.11n
Compatible Devices:	Laptop
Frequency:	2.4 GHz
Connectivity Technology:	Wireless, Ethernet
Operating System:	OpenWrt
Number of Ports:	2
Data Transfer Rate:	300 Megabytes Per Second

**Device information**
Brand:	Raspberry
Ram Memory Installed Size:	2 GB
Memory Storage Capacity:	2 GB
CPU Model:	Cortex
Connectivity Technology:	Bluetooth, Wi-Fi, USB, Ethernet, HDMI, GPIO
Broadcom BCM2711, quad-core Cortex-A72 (ARM v8) 64-bit SoC @ 1. 5GHz
2. 4 GHz and 5. 0 GHz IEEE 802. 11b/g/n/ac wireless LAN, Bluetooth 5. 0, BLE
2 × USB 3. 0 ports, 2 x USB 2. 0 Ports
2 × micro HDMI ports supproting up to 4Kp60 video resolution
Micro SD card slot for loading operating system and data storage

**Steps to set up DietPI image on Raspberry PI**

1. Download the below before class:
  1. BreeZip extractor as I have a windows laptop.
  2. BalenaEtcher
  3. DietPI ARMv8 64-bit image using the download link:
  https://dietpi.com/downloads/images/DietPi_RPi-ARMv8-Bullseye.7z

2. Extract the DietPi_RPi-ARMv8-Bullseye.7z using BreeZip extractor.
3. Insert the micro SD card into the micro SD drive.
4. Using BalenaEtcher, flash the DietPi image onto the SD card.
  1. Open BalenaEtcher.
  2. Select Flash from file.
  3. Select the dietpi image from your computer.
  4. Select target(the inserted card).
  5. Press flash.
  6. Wait until flashing is finished.
  7. Close BalenaEtcher.
5. A separate drive(E drive in my case) was accessible in my computer from which I could access the SD card contents. 
  Copy the dietpi.txt and dietpi-wifi.txt to a separate location on the computer.
6. Edit the dietpi-wifi.txt with the router SSID and credentials( as shown on the Wireless tab of the router’s admin panel).
7. Edit the dietpi.txt with the location and wi-fi default settings. For the East coast US, the below variables need to be changed:
  1. AUTO_SETUP_LOCALE=en_US.UTF-8
  2. AUTO_SETUP_KEYBOARD_LAYOUT=us
  3. AUTO_SETUP_TIMEZONE=America/New_York
  4. AUTO_SETUP_NET_ETHERNET_ENABLED=0
  5. AUTO_SETUP_NET_WIFI_ENABLED=1
  6. AUTO_SETUP_NET_WIFI_COUNTRY_CODE=US
  7. AUTO_SETUP_DHCP_TO_STATIC=1
  8. AUTO_SETUP_NET_HOSTNAME=DietPi_{YOUR_INITIALS}
  9. AUTO_SETUP_HEADLESS=1
  10. AUTO_SETUP_AUTOSTART_TARGET_INDEX=1
  11. SURVEY_OPTED_IN=0
  12. CONFIG_SERIAL_CONSOLE_ENABLE=1
8. Replace the dietpi-wifi.txt and dietpi.txt in the SD card drive with the modified files.
9. Take the SD card out from the laptop.
10. Insert the SD card into the Raspberry Pi and power it up using the power cord provided with the PI. 
  Red light will turn on and the green light will start flashing. (It flashed nearly for 10 minutes in my case after which it stopped flashing.)
11. Then check the Clients tab in the router’s admin panel. You could see a new device DietPi connected to the network. Copy its IP address.
12. Use SSH to login into PI using the below command in your command prompt:

  ssh root@IPADDR
  password: dietpi (default password)

  where, IPADDR is the IP address copied from Clients page.
13. The PI will start installing a lot of updates for about 2-3 minutes after which it disconnects the ssh connection.
14. Log in once again into the PI. This time you will be able to change the default password for ‘root’ and ‘dietpi’ users.

Challenges:

I am using a 64 GB micro SD card. I was a little apprehensive if the 64 GB SD would work or not because as per Professor’s prerequisite, 
the maximum being used is 32 GB. But I was successfully able to install the dietPi using the 64 GB card.

Help links:

