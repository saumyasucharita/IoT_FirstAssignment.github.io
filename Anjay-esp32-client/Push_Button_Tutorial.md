**Push Button Tutorial using Anjay ESP-32 LwM2M client**

**Circuit Diagram**<br/>
This type of push button switch has 4 pins (2 Pole Switch). Two pins on the left are connected, and both left<br/>
and right sides are the same per the diagram:<br/>
![PushButton_component](/Anjay-esp32-client/image/PushButton_component.JPG)<br/>
When the button on the switch is pressed, the circuit is completed (your project is powered ON).<br/>
(Referencd from C_Tutorial of Freenove Ultimate Starter Kit)<br/>

Working circuit connections:<br/>
1. Connect the terminal 1 of push button to a 10 kilo ohm resistor.<br/>
2. Connect the other end of resistor to GPIO pin 13 using a jumper cable.<br/>
3. Connect the other side of terminal 1 of push button to another 10 kilo ohm resistor which is connected to 3.3 V power supply.
4. Connect terminal 2 of push button to the Ground using a jumper cable.
![Circuit_Diagram_Push_Button](/Anjay-esp32-client/image/Circuit_Diagram_Push_Button.jpeg)<br/>

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
Select the 'Push button enabled'<br/>
Set the push button pin to 13 as per the circuit diagram.<br/>
![PushButton_Board_options](/Anjay-esp32-client/image/PushButton_Board_options.JPG)<br/>

ii) Navigate to Client options --><br/>
Change Server URI to coap://192.168.8.229:5683.<br/>
Change 'Choose security mode' to 'Non-secure connection'.<br/>
![PushButton_Client_options](/Anjay-esp32-client/image/PushButton_Client_options.JPG)<br/>
iii) Navigate to Connection Configuration --> <br/>
Change the Wifi SSID and Wifi Password to your travel router's SSID and password.<br/>
![PushButton_Conn_Config](/Anjay-esp32-client/image/PushButton_Conn_Config.JPG)<br/>
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
11. Go to the Push Button tab.<br/>
Press the push button multiple times.<br/>
Click on the read('R') option for Digital Input State. You can see the value as false.<br/>
Click on the read('R') option for Digital Input Counter. You can see the number of times you have pressed the push button.<br/>
![PushButton_Output](/Anjay-esp32-client/image/PushButton_Output.JPG)<br/>



