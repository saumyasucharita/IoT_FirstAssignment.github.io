**Temperature and Humidity DHT11 Sensor Tutorial using Raspberry Pi**

**Hardware required:**
1. Breadboard
2. Three jumber cables
3. DHT11 sensor
4. One 10 kiloohm resistor

**Specifications of the DHT11 sensor:**
![DHT11_Specs](/ANALOG_Device_Tutorials/image/DHT11_Specs.JPG)<br/>
1. Its operating voltage is within the range of 3.3V-5.5V.
2. The SDA pin is a data pin, which is used to communicate with other devices.
3. The NC pin (Not Connected Pin) has no functional purpose to the outside circuit (but may have an unknown functionality during
manufacture and test). This pin should not be connected to any of the circuit connections.

**Circuit diagram of Pi to DHT11 sensor**
![Operational_Circuit_Pi](/ANALOG_Device_Tutorials/image/Operational_Circuit_Pi.jpeg)<br/>
![CircuitDiagram2](/ANALOG_Device_Tutorials/image/CircuitDiagram2.JPG)<br/>
![Raspberry_Pi_Pins](/ANALOG_Device_Tutorials/image/Raspberry_Pi_Pins.JPG)<br/>

**Software snippet showing GPIO setup and runtime looping and temperature reading and writing results to output**
![C_program_snippet1](/ANALOG_Device_Tutorials/image/C_program_snippet1.JPG)<br/>
![C_program_snippet2](/ANALOG_Device_Tutorials/image/C_program_snippet2.JPG)<br/>

**Images of resulting console and operation**
![Temperature_data_Pi](/ANALOG_Device_Tutorials/image/Temperature_data_Pi.JPG)<br/>

Blog Link:
https://computing-sciences.yellowdig.app/community/62e2eacc-366d-319c-a96d-cf1e0b1d27ef?postId=47424135932489441


