**Setting up IOT Platform on Raspberry Pi**

1. Establish an SSH connection to Raspberry Pi using dietpi user.<br/>
  ssh dietpi@192.168.8.229<br/>
  Enter the password you set while initially setting up.
2. Install the below softwares using the dietpi software menu.<br/>
 i) MQTT<br/>
 ii) Node-red<br/>
 iii) PostgreSQL<br/>
 Search for these softwares using Search Software option. Hit the spacebar for selecting that software and then select ok.<br/>
 Move to the Install option and press tab to select ok.<br/>
 ![InstallSoftwares](/RPI_Setup/image/IoTPlatform/InstallSoftwares.png)<br/>
 It will take around 10 minutes to install these 3 softwares.<br/>
 3. Reboot the pi using command:<br/>
 $sudo reboot<br/>
 ![RebootPi](/RPI_Setup/image/IoTPlatform/RebootPi.JPG)<br/>
 Make an ssh connection again.<br/>
 
**Configuring Postgres**
1. Make postgres as the superuser.<br/>
$sudo su postgres<br/>
2. Create a 'pi' user<br/>
$createuser pi -P --interactive<br/>
Set a password for this new user and then re-enter it.<br/>
![Postgres_user](/RPI_Setup/image/IoTPlatform/Postgres_user.JPG)<br/>
3. Connect to postgres SQL and create a new 'test' database using the below command:<br/>
$psql<br/>
$create database test;<br/>
4. Press Ctrl+D twice to exit from the psql and again from Postgres user. <br/>
   Create a new table 'people' in the 'test' database using the sudo user postgres.<br/>
   $sudo su postgres<br/>
   $psql test<br/>
   $create table people (name text, company text);<br/>
5. Insert data into the table.<br/>
![CreateInsertPeople](/RPI_Setup/image/IoTPlatform/CreateInsertPeople.JPG)<br/>
6. Allow postgres to receive all ip traffic by using:<br/>
$ALTER SYSTEM SET LISTEN_ADDRESSES = '*';<br/>
![ReceiveIPTraffic](/RPI_Setup/image/IoTPlatform/ReceiveIPTraffic.JPG)<br/>
7. Press Ctrl+D twice to exit to the dietpi user. Then restart postgresql using:<br/>
$sudo dietpi-services restart postgresql<br/>
![PostgresRestart](/RPI_Setup/image/IoTPlatform/PostgresRestart.JPG)<br/>
8. Check the postgresql log to see if the service started successfully.<br/>
![RestartPostgres](/RPI_Setup/image/IoTPlatform/RestartPostgres.JPG)<br/>

**Configuring Node-Red**
1. Access the node-red UI using the below address in a web-browser.<br/>
http://IPADDR:1880<br/>
where, IPADDR is the ip address of your pi.<br/>
2. Install node-red-contrib-re-postgres using the below command:<br/>
$npm install node-red-contrib-re-postgres<br/>
3. Restart the node-red service:<br/>
 $dietpi-services restart node-red<br/>
4. Go the node-red UI and select Manage Pallet from the options and install node-red-contrib-postgresql.<br/>
![ManagePallet](/RPI_Setup/image/IoTPlatform/ManagePallet.png)<br/>
5. Drag a Postgres node into the blank flow diagram. Double-click the node and configure the host and port of the database instance.<br/>
6. Also pull in a trigger, template and debug node and connect every element with a wire.<br/>
![NodeRedFlow.JPG](/RPI_Setup/image/IoTPlatform/NodeRedFlow.JPG)<br/>


