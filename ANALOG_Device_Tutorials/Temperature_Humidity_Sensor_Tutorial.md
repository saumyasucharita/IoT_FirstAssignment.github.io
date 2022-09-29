**Temperature and Humidity DHT11 Sensor Tutorial using Raspberry Pi**

**Hardware required:**
1. Breadboard
2. Three jumber cables
3. DHT11 sensor
4. One 10 kiloohm resistor

**Specifications of the DHT11 sensor:<br/>**
![DHT11_Specs](/ANALOG_Device_Tutorials/image/DHT11_Specs.JPG)<br/>
1. Its operating voltage is within the range of 3.3V-5.5V.<br/>
2. The SDA pin is a data pin, which is used to communicate with other devices.<br/>
3. The NC pin (Not Connected Pin) has no functional purpose to the outside circuit (but may have an unknown functionality during<br/>
manufacture and test). This pin should not be connected to any of the circuit connections.<br/>

**Circuit diagram of Pi to DHT11 sensor**<br/>

Image of the operational circuit<br/>
![Operational_Circuit_Pi](/ANALOG_Device_Tutorials/image/Operational_Circuit_Pi.jpeg)<br/>

Circuit diagram referenced<br/>
![CircuitDiagram2](/ANALOG_Device_Tutorials/image/CircuitDiagram2.JPG)<br/>

I referenced the below pin diagram of raspberry Pi as I don't have any idea which pin represents the power, pin 7 and ground.<br/>
![Raspberry_Pi_Pins](/ANALOG_Device_Tutorials/image/Raspberry_Pi_Pins.JPG)<br/>

Hardware set up steps:<br/>
1. Place the DHT11 sensor firmly on the breadboard.<br/>
2. Connect the Pin 1 of sensor to the 5V power supply(Pin 2) of the raspberry pi.<br/>
3. Connect Pin 2 of sensor with the Pin 7 of the pi.<br/>
4. No connection is required for the Pin 3 of sensor.<br/>
5. Connect Pin 4 of the sensor with the 6th pin of pi(Ground).<br/>
6. Connect one end of the resistor with the Pin 1 and the other end with Pin 2 of sensor.<br/>


**Software snippet showing GPIO setup and runtime looping and temperature reading and writing results to output**<br/>
![C_program_snippet1](/ANALOG_Device_Tutorials/image/C_program_snippet1.JPG)<br/>

Code showing an infinite loop to read the sensor data<br/>
![C_program_snippet2](/ANALOG_Device_Tutorials/image/C_program_snippet2.JPG)<br/>

1. Clone the Wiring Pi code from the below link and build it:<br/>
$git clone https://github.com/WiringPi/WiringPi.git<br/>
$cd WiringPi<br/>
$./build<br/>
2. Check the version of gpio installed.<br/>
dietpi@DietPi:~/WiringPi$ gpio -v<br/>
gpio version: 2.70
Copyright (c) 2012-2018 Gordon Henderson<br/>
This is free software with ABSOLUTELY NO WARRANTY.
For details type: gpio -warranty

  Raspberry Pi Details:<br/>
  Type: Pi 4B, Revision: 05, Memory: 2048MB, Maker: Sony
  * Device tree is enabled.
  *--> Raspberry Pi 4 Model B Rev 1.5
  * This Raspberry Pi supports user-level GPIO access.
 3. Copy the C program from:<br/>
 https://www.circuitbasics.com/how-to-set-up-the-dht11-humidity-sensor-on-the-raspberry-pi/<br/>
 4. Create a new file in Pi using the below command and paste the C program here and save and exit:<br/>
 $nano temp_humidity_read.c<br/>
 5. Update the counter value from 16 to 50 in the C program as suggested by Sai Sushmita's blog comment:<br/>
 https://computing-sciences.yellowdig.app/community/62e2eacc-366d-319c-a96d-cf1e0b1d27ef?postId=47424135931403193<br/>
 6. Compile and execute the program using:<br/>
$ gcc -o  temp_humidity_read temp_humidity_read.c -lwiringPi -lwiringPiDev<br/>
$ sudo ./temp_humidity_read<br/>

**Images of resulting console and operation**<br/>
![Temperature_data_Pi](/ANALOG_Device_Tutorials/image/Temperature_data_Pi.JPG)<br/>

**Issues faced:<br/>**
I tried cloning the wiring Pi code from git://git.drogon.net/wiringPi. But I got connection refused.<br/>
dietpi@DietPi:~$ git clone git://git.drogon.net/wiringPi<br/>
Cloning into 'wiringPi'...
fatal: unable to connect to git.drogon.net:
git.drogon.net[0: 188.246.205.22]: errno=Connection refused
git.drogon.net[1: 2a03:9800:10:7b::2]: errno=Network is unreachable

There is an unofficial fork of the same code as mentioned here:<br/>
https://stackoverflow.com/questions/58360015/how-to-clone-wiringpi-after-git-drogon-net-got-inaccesible<br/>

$git clone https://github.com/WiringPi/WiringPi.git<br/>




**Blog Link:**<br/>
https://computing-sciences.yellowdig.app/community/62e2eacc-366d-319c-a96d-cf1e0b1d27ef?postId=47424135932489441<br/>

**Alternate Tutorial:**<br/>
[ArduinoIDE](/ANALOG_Device_Tutorials/ArduinoIDE.md)<br/>

**References:**<br/>
https://www.circuitbasics.com/how-to-set-up-the-dht11-humidity-sensor-on-the-raspberry-pi/<br/>
https://computing-sciences.yellowdig.app/community/62e2eacc-366d-319c-a96d-cf1e0b1d27ef?postId=47424135931403193<br/>
https://forums.raspberrypi.com/viewtopic.php?t=197331<br/>
https://pinout.xyz/<br/>
https://stackoverflow.com/questions/58360015/how-to-clone-wiringpi-after-git-drogon-net-got-inaccesible<br/>
Freenove C tutorial downloaded from:
https://freenove.com/fnk0047/



