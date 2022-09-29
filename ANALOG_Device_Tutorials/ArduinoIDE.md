**Temperature and Humidity DHT11 Sensor Tutorial using Arduino IDE **

**Hardware required:**

1. Breadboard with ESP32-Wrover
2. Four jumper cables(the ones having pins at both ends)
3.DHT11 sensor
4.One 10 kiloohm resistor

**Software required:**
Arduino IDE

**Hardware set-up:**

1. Refer the circuit diagram provided on page 268 of the C_Tutorial of the Freenove starter kit.
![DHT11_Specs](/ANALOG_Device_Tutorials/image/DHT11_Specs.JPG)<br/>
2. Place the DHT11 sensor firmly on the breadboard.
3. Connect the Pin 1(1 starting from left) to the 3.3 V power supply using two jumper cables.(Please refer the image file of the circuit attached with this blog.)
4. Connect one end of the resistor with the 3.3 V power supply and one end with Pin 2 of sensor.
5. Connect Pin 2 of sensor with the 13th pin of the GPIO extension of ESP32.
6. No connection is required for the Pin 3.
7. Connect Pin 4 of the sensor with the 13th pin of the GPIO extension of ESP32.
![DHT11_Specs](/ANALOG_Device_Tutorials/image/DHT11_Specs.JPG)<br/>

**IDE set-up:**
1. Download and install the Arduino IDE from:
https://www.arduino.cc/en/software
2. In Arduino IDE, go to File -> Preferences.
3. Add the below url to the Additional boards manager Urls:
https://dl.espressif.com/dl/package_esp32_index.json
4. Go to Tools -> Board -> Boards Manager. Search for esp32 and install the “ESP32 by Espressif Systems”
5. Select the relevant board. Tools -> Board -> esp32 -> ESP32 Wrover Module.

**Test the ESP32 circuit:**

1. Connect the ESP32 board to your laptop/computer with the USB cable provided with the Freenove kit.
2. Go to Tools -> Port. Select the COM4 port.
3. Download the Zip file of the external library from: https://github.com/beegee-tokyo/DHTesp
4. Go to Sketch -> Include Library -> Add .ZIP Library…. Select the .zip file from your computer.
5. Copy the code from page 271 of the C_Tutorial and paste in a .ino file. You can save the file as a new sketch.
![DHT11_Specs](/ANALOG_Device_Tutorials/image/DHT11_Specs.JPG)<br/>
6. Press the Upload button(right-arrow) at the top in Arduino IDE. Let the code compile and upload to your board.
7. After you see the ‘Done uploading’ message at the bottom, check the Serial Monitor tab.
8. Set the baud rate to be 115200 baud as per the C program.
9. You can see the temperature and humidity readings in the Serial Monitor.
![DHT11_Specs](/ANALOG_Device_Tutorials/image/DHT11_Specs.JPG)<br/>

**References:**

https://randomnerdtutorials.com/solved-arduino-ide-esp32-esp8266-installation/
https://freenove.com/fnk0047/
https://www.circuitbasics.com/how-to-set-up-the-dht11-humidity-sensor-on-the-raspberry-pi/
