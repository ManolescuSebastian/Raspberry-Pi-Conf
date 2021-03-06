First connection to raspberry pi using SSH, no monitor required.
----

This SSH connection after SD card boot requires three main steps in order to work, and also all the steps below were done using a mac OS operating system, but I really don't think that this will make a big difference.

Raspberry pi boot
-----

Download ***Raspberry Pi Imager*** from https://www.raspberrypi.org/downloads/ and install the desired version (if you plan never to use a monitor and connect via SSH I wouls sugget getting the Lite version).        
(Had a few SD cards that returned error when I tried to install the OS using the Imager, in that case we can use the option below).             
      
<img src="https://github.com/ManolescuSebastian/Raspberry-Pi-Conf/blob/master/res-img/rpi_imager_img.png" width="33%"></img>
<img src="https://github.com/ManolescuSebastian/Raspberry-Pi-Conf/blob/master/res-img/rpi_imager_img1.png" width="33%"></img>
<img src="https://github.com/ManolescuSebastian/Raspberry-Pi-Conf/blob/master/res-img/rpi_imager_img2.png" width="33%"></img>  
OR

Download the ***Raspberry Pi OS (32-bit) Lite*** from https://www.raspberrypi.org/downloads/raspberry-pi-os/        
After that install etcher from https://www.balena.io/etcher/, this used to flash the OS to the SD card.   

<img src="https://github.com/ManolescuSebastian/Raspberry-Pi-Conf/blob/master/res-img/etcher_img.png" width="50%"></img>

Since we have no monitor available we need 2 things.
1. Enable SSH on the device (sincer SSH is disabled by default for secutiry reasons, we need to enable it)
2. Connect to our local network


- To enable SSH we need to get the card and plug it in our computer then go to your SD card (Volumes/boot).      
           
<img src="https://github.com/ManolescuSebastian/Raspberry-Pi-SHH-NO-Monitor/blob/master/res-img/boot_finder_img.png" width="50%"></img>  

Then create a file named ***ssh*** on the SD card (**NO extension required**).      

```touch ssh```

Config WIFI connection
-----

And after we have the ssh file we need to create the WIFI configuration file, so that we are able to connect to our local network.        
For that we need to create the file ***wpa_supplicant.conf***          
Open file with an editor.     
```vim wpa_supplicant.conf```        

and add the following content:         

```
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
ssid="your-ssid"
scan_ssid=1
psk="your-password"
key_mgmt=WPA-PSK
}

```
       
Insert SD card in raspberry pi slot.
Open terminal and in order to find the raspberry pi IP addedss we need to add the follwoing command:
      
```arp -a```
         
<img src="https://github.com/ManolescuSebastian/Raspberry-Pi-Conf/blob/master/res-img/arp_a_raspberry_ip.jpg" width="100%"></img>

Connect to device via SSH
-----
After we found the IP address we connect to the rasperry pi using SSH command:

```ssh pi@192.168.X.X```

<img src="https://github.com/ManolescuSebastian/Raspberry-Pi-Conf/blob/master/res-img/ssh_connect_img.png" width="100%"></img>

The default password for your device is : ***raspberry***

And the final result should look like this:

<img src="https://github.com/ManolescuSebastian/Raspberry-Pi-Conf/blob/master/res-img/ssh_connected_img.jpg" width="100%"></img>
