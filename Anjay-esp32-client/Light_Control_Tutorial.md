**Light Control Tutorial using Anjay ESP-32 LwM2M client**

**Links Referenced:**
1. C_Tutorial of Freenove Ultimate Starter Kit
2. https://github.com/pschragger/IOT_Tutorials_for_VU/tree/main/RPI_BUILD_LWM2M_DEVICE
3. Blog posted by Ian
 https://computing-sciences.yellowdig.app/community/62e2eacc-366d-319c-a96d-cf1e0b1d27ef?postId=47424135935826700

**Circuit Diagram**<br/>
LED:<br/>
A LED will only work (light up) if the longer pin (+) of LED is connected to the positive output from a power
source and the shorter pin is connected to the negative (-). Negative output is also referred to as Ground
(GND).<br/>
LEDs cannot be directly connected to a power supply, which usually ends in a damaged component. A
resistor with a specified resistance value must be connected in series to the LED you plan to use.<br/>
(Referencd from C_Tutorial of Freenove Ultimate Starter Kit)

![Schematic_Diagram](/Anjay-esp32-client/image/Schematic_Diagram.JPG)<br/>
![Hardware_Connection](/Anjay-esp32-client/image/Hardware_Connection.JPG)<br/>
Working circuit connections:<br/>
![Circuit_Diagram_Light_Control](/Anjay-esp32-client/image/Circuit_Diagram_Light_Control.jpeg)<br/>

**Configuration changes needed:**
1. Change directory to the anjay-esp32-client directory.<br/>
$cd ~/projects/Anjay-esp32-client<br/>
2. Setup the local enironment for using the esp tools.<br/>
$cd ~/projects/Anjay-esp32-client<br/>
$. $HOME/esp/esp-idf/export.sh<br/>
$idf.py set-target esp32 <br/>
3. Start the leshan server in a separate command prompt window using:<br/>
$cd ~/projects/leshan<br/>
$java -jar leshan-server-demo/target/leshan-server-demo-*-SNAPSHOT-jar-with-dependencies.jar &<br/>
4. Access the leshan server dashboard at:<br/>
http://192.168.8.229:8080/#/server<br/>
Copy the CoAP over UDP url: coap://192.168.8.229:5683<br/>
5. Access the menu configuration in the previous command prompt using:<br/>
$idf.py menuconfig<br/>
6. Go to Component Config -> anjay-esp32-client<br/>
i) Navigate to Board options --> <br/>
Set the Device manufacturer as 'Espressif'<br/>
Set the Model number as 'ESP-WROVER-KIT'<br/>
Select the 'Light control enabled'<br/>
![Board_options](/Anjay-esp32-client/image/Board_options.JPG)<br/>
Enter Light control options: Select 'Enable red color'<br/>
Set the Red color pin as 2.<br/>
![Light_control_options](/Anjay-esp32-client/image/Light_control_options.JPG)<br/>
ii) Navigate to Client options --><br/>
Change Server URI to coap://192.168.8.229:5683.<br/>
Change 'Choose security mode' to 'Non-secure connection'.<br/>
![Client_options](/Anjay-esp32-client/image/Client_options.JPG)<br/>
iii) Navigate to Connection Configuration --> <br/>
Change the Wifi SSID and Wifi Password to your travel router's SSID and password.<br/>
![Wifi_SSID](/Anjay-esp32-client/image/Wifi_SSID.JPG)<br/>
Save the configurations by pressing 'S' and enter.<br/>
Escape the menu configuration.<br/>

7. Build the Anjay-client code.<br/>
$ idf.py build<br/>
8. Find the USB port to which the ESP32-WROVER is connected.<br/>
dietpi@DietPi:~/projects/Anjay-esp32-client$ ls -l /dev/ttyUSB*<br/>
crw-rw---- 1 root dialout 188, 0 Sep 30 01:08 /dev/ttyUSB0<br/>
9. Flash the device:<br/>
$sudo chmod 666 /dev/ttyUSB0<br/>
$idf.py -p 0 flash<br/>
10. Check the leshan server dashboard for the registration of the anjay-esp32-client.<br/>
![Anjay-esp32-client](/Anjay-esp32-client/image/Anjay-esp32-client.JPG)<br/>
11. Go to the Light control tab.<br/>
Click on the write('W') option for On/Off operation and enter the boolean value to 'true'.<br/>
Click on the write('W') option for Dimmer and enter an integer value from 0 to 100. For example, enter 20.<br/>
![Light_control_settings](/Anjay-esp32-client/image/Light_control_settings.JPG)<br/>
You can see the LED turned on now.<br/>








