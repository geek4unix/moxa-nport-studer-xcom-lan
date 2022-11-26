# moxa-nport-studer-xcom-lan

If you have reset your Moxa Nport serial to ethernet device and want to get it working again with Studer Xcom Lan .... 


Are you seeing Error 089 - Could not connect to Xom server

Then this guide is for you.

#Question

Why reset the Nport at all ?

#Answer
Because there was a UI and i didnt have the password. Any curious sysadmin who likes trouble would be curious ...

#How to reset the Nport Serial to ethernet converter

Moxa has great documentation, basically there is a reset pin on the top of the device, which sets it back to factory defaults.

Here is a [link to the process](https://manualmachine.com/moxatechnologies/nport5110/685385-user-manual/) and information on the default IP and network settings needed to reconnect to it.

1) Reset Devuce with paper clip or similar tool.
2) Connect to default IP / Network usually 192.168.127.254/255.255.255.0 , no gateway ( on your client pc ) 
3) Login as admin / moxa ( usually ) 
4) Set new admin password to something secure
5) Configure IP/Network settings for your LAN
6) Verify you can ping it.

**Question**

Is it done now ? 

**Answer**

Yes and No - Your Nport device is reset and is now back on the network, but there was a setting still needed for the Nport device to work with studer remote server.

**Configure Nport to send data to studer-innotec server**

Login to the Nport/Moxa interface:  

1) change operation mode to tcp client
2) change the 1st of 4 settings for destination IP 1 to : xcom.studer-innotec.com , port 83
3) change delimiter hex setting to d+a , enable
4) save and reboot nport
5) reapply SD card update in xcom 323i - See [Xcom-Lan configuration guide](https://www.studer-innotec.com/media/document/0/manuel-xcom-gsm-lan_v2.1_en.pdf)
6) Your RCC ( studer control panel ) should eventually ( 2-5 mins ) log an event with code 090 - Xom server conneceted

Here are some [screenshots of the settings](https://photos.app.goo.gl/RoWDTT1Ueq8ReUys8)

Now your system should be registered on the studer site and data should start flowing

