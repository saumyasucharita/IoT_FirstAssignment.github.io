**Light Control Tutorial using Anjay ESP-32 LwM2M client**

**Links Referenced:**
1. C_Tutorial of Freenove Ultimate Starter Kit
2. https://github.com/pschragger/IOT_Tutorials_for_VU/tree/main/RPI_BUILD_LWM2M_DEVICE
3. Blog posted by Ian
 https://computing-sciences.yellowdig.app/community/62e2eacc-366d-319c-a96d-cf1e0b1d27ef?postId=47424135935826700

**Circuit Diagram**
LED:
A LED will only work (light up) if the longer pin (+) of LED is connected to the positive output from a power
source and the shorter pin is connected to the negative (-). Negative output is also referred to as Ground
(GND).
LEDs cannot be directly connected to a power supply, which usually ends in a damaged component. A
resistor with a specified resistance value must be connected in series to the LED you plan to use.
(Referencd from C_Tutorial of Freenove Ultimate Starter Kit)

![DHT11_Specs](/ANALOG_Device_Tutorials/image/DHT11_Specs.JPG)<br/>
![DHT11_Specs](/ANALOG_Device_Tutorials/image/DHT11_Specs.JPG)<br/>
![DHT11_Specs](/ANALOG_Device_Tutorials/image/DHT11_Specs.JPG)<br/>

**Configuration changes needed:**
1. Change directory to the anjay-esp32-client directory.
$cd ~/projects/Anjay-esp32-client
2. Setup the local enironment for using the esp tools.
$cd ~/projects/Anjay-esp32-client
$. $HOME/esp/esp-idf/export.sh
$idf.py set-target esp32 
3. Start the leshan server in a separate command prompt window using:
$cd ~/projects/leshan
$java -jar leshan-server-demo/target/leshan-server-demo-*-SNAPSHOT-jar-with-dependencies.jar &
4. Access the leshan server dashboard at:
http://192.168.8.229:8080/#/server
Copy the CoAP over UDP url: coap://192.168.8.229:5683
5. Access the menu configuration using:
$idf.py menuconfig
6. Go to Component Config -> anjay-esp32-client
i) Navigate to Board options --> 
Set the Device manufacturer as 'Espressif'
Set the Model number as 'ESP-WROVER-KIT'
Select the 'Light control enabled'
![DHT11_Specs](/ANALOG_Device_Tutorials/image/DHT11_Specs.JPG)<br/>
Enter Light control options: Select 'Enable red color'
Set the Red color pin as 2.
![DHT11_Specs](/ANALOG_Device_Tutorials/image/DHT11_Specs.JPG)<br/>
ii) Navigate to Client options -->
Change Server URI to coap://192.168.8.229:5683.
![DHT11_Specs](/ANALOG_Device_Tutorials/image/DHT11_Specs.JPG)<br/>
iii) Navigate to Connection Configuration --> 
Change the Wifi SSID and Wifi Password to your travel router's SSID and password.
![DHT11_Specs](/ANALOG_Device_Tutorials/image/DHT11_Specs.JPG)<br/>

7. Build the Anjay-client code.
$ idf.py build
8. Find the USB port to which the ESP32-WROVER is connected.
dietpi@DietPi:~/projects/Anjay-esp32-client$ ls -l /dev/ttyUSB*
crw-rw---- 1 root dialout 188, 0 Sep 30 01:08 /dev/ttyUSB0
9. Flash the device:
$sudo chmod 666 /dev/ttyUSB0
$idf.py -p 0 flash
10. Check the leshan server dashboard for the registration of the anjay-esp32-client.
![DHT11_Specs](/ANALOG_Device_Tutorials/image/DHT11_Specs.JPG)<br/>
11. Go to the Light control tab.
![DHT11_Specs](/ANALOG_Device_Tutorials/image/DHT11_Specs.JPG)<br/>








