**Installing Leshan Server/Client on Raspberry Pi**

**Reference:**<br/>
https://github.com/pschragger/IOT_Tutorials_for_VU/tree/main/RPI_DEVICE_MANAGEMENT_INSTALL_tutorial

**Tell what you did differently from the explanation.**

I followed the instructions on professor's github page referenced above for git and java jdk installation.<br/>

Then I tried installing maven on the raspberry pi but I was unsuccessful.<br/>
i) Created a download directory using command – sudo mkdir download<br/>
ii) Changed directory into download directory using –sudo cd download<br/>
iii)Downloaded the latest maven using wget command.<br/>
sudo wget https://dlcdn.apache.org/maven/maven-3/3.8.6/binaries/apache-maven-3.8.6-bin.tar.gz<br/>
iv) Unpacked the tarball<br/>
sudo tar xzvf apache-maven-3.8.6-bin.tar.gz<br/>
When I checked if I had successfully installed maven, it said ‘mvn’ command not found.<br/>

Professor Schragger pointed out that I was trying to install maven through the root user.<br/> 
He rectified the mistake by changing the ownership of the download folder to the dietpi user:<br/>

**$sudo chown -R dietpi download**<br/>

![Changing_ownership](/LWM2M/image/Changing_ownership.png)<br/>
After which, I was able to check the version of maven installed.<br/>

$mvn -v<br/>
Apache Maven 3.8.6 (84538c9988a25aec085021c365c560670ad80f63)
Maven home: /home/dietpi/download/apache-maven-3.8.6
Java version: 17.0.4, vendor: Debian, runtime: /usr/lib/jvm/java-17-openjdk-arm64
Default locale: en_US, platform encoding: UTF-8
OS name: "linux", version: "5.15.61-v8+", arch: "aarch64", family: "unix"

Then I followed the instructions to add the 'PATH' and 'JAVA_HOME' variables in bashrc configuration file.<br/>
echo 'PATH="${PATH}:~/download/apache-maven-3.8.6/bin"' >> ~/.bashrc<br/>
$sudo echo 'JAVA_HOME="/usr/lib/jvm/java-17-openjdk-arm64"' >> ~/.bashrc<br/>

I created a projects directory and then cloned leshan repo using git command. <br/>
I built the leshan project using maven. The build took around 22 minutes for me.<br/>
![LeshanBuildSuccess](/LWM2M/image/LeshanBuildSuccess.png)<br/>
I started the leshan server using:<br/>

$java -jar leshan-server-demo/target/leshan-server-demo-*-SNAPSHOT-jar-with-dependencies.jar &<br/>

Accessed Leshan demo UI on browser:<br/>
http://192.168.8.229:8080<br/>


I could see that there were no registered clients on the UI.<br/><br/>
![NoClientLeshan](/LWM2M/image/NoClientLeshan.png)<br/>

I executed the leshan client jar file and then checked the UI page again. I could see the DietPi as a registered client.<br/>
![RegisteredClientLeshan](/LWM2M/image/RegisteredClientLeshan.png)<br/>
Finally, used Ctlr-C to stop the Leshan client.<br/>

**Blog link:**<br/>
https://computing-sciences.yellowdig.app/community/62e2eacc-366d-319c-a96d-cf1e0b1d27ef?postId=47424135922738852<br/>

**Overview of an additional experiment of the LWM2M**<br/>
Test the bootstrap service 

  1. Start the bootstrap server using:<br/>
  cd ~/projects/leshan<br/>
  $java -jar leshan-bsserver-demo/target/leshan-bsserver-demo-2.0.0-SNAPSHOT-jar-with-dependencies.jar<br/>
  ![Bootstrap_start_log](/LWM2M/image/Bootstrap_start_log.JPG)<br/>

  2. Access the bootstrap server UI at:<br/>
  http://192.168.8.229:8080/#/bootstrap<br/>
  ![BootstrapUI](/LWM2M/image/BootstrapUI.png)<br/>
  
  You can copy the server URL, Server Public key and server certificate from the server tab of this page.<br/>
  ![Bootstrap_server_details](/LWM2M/image/Bootstrap_server_details.png)<br/>

**Different types of lwm2m client code testing**<br/>

I tried installing Zephyr project lwm2m following the instructions at below page:<br/>
https://developer.nordicsemi.com/nRF_Connect_SDK/doc/latest/zephyr/samples/net/lwm2m_client/README.html<br/>
https://developer.nordicsemi.com/nRF_Connect_SDK/doc/latest/zephyr/connectivity/networking/qemu_setup.html#networking-with-qemu<br/>
(Networking with QEMU)<br/>

But I was unable to perform the Step-3(Start app in QEMU) in the Networking with QEMU page. <br/>
Also before reaching that step there were a lot of dependent softwares which needed to be installed.<br/>
I am unaware of what each command did. Therefore, I could not succeed in testing the client code.<br/>

Commands I used:<br/>
1. I cloned the Zephyr project from github using:<br/>
$ git clone https://github.com/zephyrproject-rtos/net-tools<br/>
2. $ cd net-tools<br/>
3. dietpi@DietPi:~/net-tools$ make<br/>
The command threw the below error:<br/>
/bin/sh: 1: pkg-config: not found<br/>
fatal error: glib.h: No such file or directory<br/>
4. dietpi@DietPi:~/net-tools$ sudo apt-get update -y<br/>
dietpi@DietPi:~/net-tools$ sudo apt-get install -y autoconf-archive<br/>
5.$sudo apt-get install libglib2.0-dev<br/>
$sudo apt-get install libpcap0.8-devY<br/>
$sudo apt-get install libtool<br/>
$sudo apt-get -y install socat<br/>
6.$pip3 install --user -U west
$echo 'export PATH=~/.local/bin:"$PATH"' >> ~/.bashrc<br/>
$source ~/.bashrc<br/>
7.$west init ~/zephyrproject<br/>

![FailedAttempt](/LWM2M/image/FailedAttempt.png)<br/>
