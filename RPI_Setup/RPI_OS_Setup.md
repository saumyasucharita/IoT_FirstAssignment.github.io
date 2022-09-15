**Raspberry PI set up via wifi**

**Laptop information**<br />
System manufacturer: Dell Inc<br />
System Model: XPS 13 7390<br />
OS Name: Microsoft Windows 10 Home<br />
Having micro SD card slot<br />

**Router information**<br />
Type: Travel Router<br />
Brand:	GL.iNet<br />
Model Name:	GL-MT300N-V2<br />
Wireless Communication Standard:	802.11n<br />
Compatible Devices:	Laptop<br />
Frequency:	2.4 GHz<br />
Connectivity Technology:	Wireless, Ethernet<br />
Operating System:	OpenWrt<br />
Number of Ports:	2<br />
Data Transfer Rate:	300 Megabytes Per Second<br />

**Device information**<br />
Brand:	Raspberry<br />
Ram Memory Installed Size:	2 GB<br />
Memory Storage Capacity:	2 GB<br />
CPU Model:	Cortex<br />
Connectivity Technology:	Bluetooth, Wi-Fi, USB, Ethernet, HDMI, GPIO<br />
Broadcom BCM2711, quad-core Cortex-A72 (ARM v8) 64-bit SoC @ 1. 5GHz<br />
2. 4 GHz and 5. 0 GHz IEEE 802. 11b/g/n/ac wireless LAN, Bluetooth 5. 0, BLE<br />
2 × USB 3. 0 ports, 2 x USB 2. 0 Ports<br />
2 × micro HDMI ports supproting up to 4Kp60 video resolution<br />
Micro SD card slot for loading operating system and data storage<br />

**Steps to set up DietPI image on Raspberry PI**

1. Download the below before class:<br />
  i) BreeZip extractor as I have a windows laptop.<br />
  ii) BalenaEtcher<br />
  iii) DietPI ARMv8 64-bit image using the download link:<br />
  https://dietpi.com/downloads/images/DietPi_RPi-ARMv8-Bullseye.7z

2. Extract the DietPi_RPi-ARMv8-Bullseye.7z using BreeZip extractor.
3. Insert the micro SD card into the micro SD drive.
4. Using BalenaEtcher, flash the DietPi image onto the SD card.<br />
  i) Open BalenaEtcher.<br />
  ii) Select Flash from file.<br />
  iii) Select the dietpi image from your computer.<br />
  iv) Select target(the inserted card).<br />
  v) Press flash.<br />
  vi) Wait until flashing is finished.<br />
  vii) Close BalenaEtcher.<br />
5. A separate drive(E drive in my case) was accessible in my computer from which I could access the SD card contents. 
  Copy the dietpi.txt and dietpi-wifi.txt to a separate location on the computer.
6. Edit the dietpi-wifi.txt with the router SSID and credentials( as shown on the Wireless tab of the router’s admin panel).
7. Edit the dietpi.txt with the location and wi-fi default settings. For the East coast US, the below variables need to be changed:<br />
  i) AUTO_SETUP_LOCALE=en_US.UTF-8<br />
  ii) AUTO_SETUP_KEYBOARD_LAYOUT=us<br />
  iii) AUTO_SETUP_TIMEZONE=America/New_York<br />
  iv) AUTO_SETUP_NET_ETHERNET_ENABLED=0<br />
  v) AUTO_SETUP_NET_WIFI_ENABLED=1<br />
  vi) AUTO_SETUP_NET_WIFI_COUNTRY_CODE=US<br />
  vii) AUTO_SETUP_DHCP_TO_STATIC=1<br />
  viii) AUTO_SETUP_NET_HOSTNAME=DietPi_{YOUR_INITIALS}<br />
  ix) AUTO_SETUP_HEADLESS=1<br />
  x) AUTO_SETUP_AUTOSTART_TARGET_INDEX=1<br />
  xi) SURVEY_OPTED_IN=0<br />
  xii) CONFIG_SERIAL_CONSOLE_ENABLE=1<br />
8. Replace the dietpi-wifi.txt and dietpi.txt in the SD card drive with the modified files.
9. Take the SD card out from the laptop.
10. Insert the SD card into the Raspberry Pi and power it up using the power cord provided with the PI. 
  Red light will turn on and the green light will start flashing. (It flashed nearly for 10 minutes in my case after which it stopped flashing.)<br/>
11. Then check the Clients tab in the router’s admin panel. You could see a new device DietPi connected to the network. Copy its IP address.
  ![DietPIonRoutersAdmin](/RPI_Setup/image/DietPIonRoutersAdmin.png)
12. Use SSH to login into PI using the below command in your command prompt:

  ssh root@IPADDR
  password: dietpi (default password)

  where, IPADDR is the IP address copied from Clients page.<br/>
13. The PI will start installing a lot of updates for about 2-3 minutes after which it disconnects the ssh connection.<br/>
![Installing updates](/RPI_Setup/image/Update_installs.png)<br/>
14. Log in once again into the PI. This time you will be able to change the default password for ‘root’ and ‘dietpi’ users.<br/>
![password_reset](/RPI_Setup/image/Password_reset.png)<br/>
Diet PI Config Menu<br/>
![SSHConnectionDietPI](/RPI_Setup/image/SSHConnectionDietPI.png)<br/>
Succesful connection established<br/>
![successful](/RPI_Setup/image/ConnectionSuccessful.png)

Challenges:

I am using a 64 GB micro SD card. I was a little apprehensive if the 64 GB SD would work or not because as per Professor’s prerequisite, 
the maximum being used is 32 GB. But I was successfully able to install the dietPi using the 64 GB card.

Blog comments:<br/>
Here is the link to my blog for Raspberry Pi set up:<br/>
https://computing-sciences.yellowdig.app/community/62e2eacc-366d-319c-a96d-cf1e0b1d27ef?postId=47424135917005487<br/>

I was able to help few other students through my screenhots included in the blog. The links to comments are:<br/>
https://computing-sciences.yellowdig.app/community/62e2eacc-366d-319c-a96d-cf1e0b1d27ef?postId=47424135919937471<br/>

https://computing-sciences.yellowdig.app/community/62e2eacc-366d-319c-a96d-cf1e0b1d27ef?postId=47424135918693094

Additional tests:<br/>
I tried to establish and SCP connection between my desktop and the Pi but the connection was not successful. I believe this may be due to absence of
any files in the Pi.<br/>
![SCP](/RPI_Setup/image/SCP.JPG)

