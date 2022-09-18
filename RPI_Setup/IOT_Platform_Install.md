**Setting up IOT Platform on Raspberry Pi**

1. Establish an SSH connection to Raspberry Pi using dietpi user.
  ssh dietpi@192.168.8.229
  Enter the password you set while initially setting up.
2. Install the below softwares using the dietpi software menu.
 i) MQTT
 ii) Node-red
 iii) PostgreSQL
 Search for these softwares using Search Software option. Hit the spacebar for selecting that software and then select ok.
 Move to the Install option and press tab to select ok.
 ![]
 It will take around 10 minutes to install.
 ![]
 Reboot the pi using command:
 $sudo reboot
 ![]
 
**Configuring Postgres**
1. Make postgres as the superuser.
$sudo su postgres
2. Create a 'pi' user
$createuser pi -P --interactive
Set a password for this new user and then re-enter it.
![]
3. Connect to postgres SQL and create a new 'test' database using the below command:
$psql
$create database test;
4. Press Ctrl+D twice to exit from the psql and again from Postgres user. Create a new table 'people' in the 'test' database using the sudo user postgres.
5. Insert data into the table.
![]
6. Allow postgres to receive all ip traffic by using:
$ALTER SYSTEM SET LISTEN_ADDRESSES = '*';
7. Press Ctrl+D twice to exit to the dietpi user. Then restart postgresql using:
$dietpi-services restart postgresql
8. Check the postgresql log to see if the service started successfully.
![]

**Configuring Node-Red**
1. Access the node-red UI using the below address in a web-browser.
http://IPADDR:1880
where, IPADDR is the ip address of your pi.
![]
2. Install node-red-contrib-re-postgres using the below command:
$npm install node-red-contrib-re-postgres
3. Restart the node-red service:
 $dietpi-services restart node-red
4. Go the node-red UI and select Manage Pallet from the options and install node-red-contrib-postgresql.
![]
5.Drag a Postgres node into the blank flow diagram. Double-click the node and configure the host and port of the database instance.
6. Also pull in a trigger, template and debug node and connect every element with a wire.
![]


