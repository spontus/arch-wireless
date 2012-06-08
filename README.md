arch-wireless
=============
rc.d-script for archlinux to simplify connecting to wireless networks


what is it?
-----------
A script to automate connecting your beloved archlaptop to wireless networks, it even allows you to prioritize certain networks above others.

installation :)
-------------
1. clone the repo
2. symlink "wireless" into /etc/rc.d using "ln -s"
3. make sure "wireless" is executable using "chmod +x"
4. create a new file called "/etc/essids" and list the essids of your networks there, eg.
	homewifi
	eduroam
	workwifi
if homewifi and eduroam are both in range it will connect to homewifi
5. add your authentication-details to /etc/wpa_supplicant.conf, see https://wiki.archlinux.org/index.php/WPA_supplicant for instructions
6. open "rc.conf" with your favorite editor, eg "sudo vim /etc/rc.conf"
7. Paste this somewhere in the file, preferably below the "NETWORKS"-section
	# Wireless setup
																	     
	# Wireless interface, (default wlan0)                                                                                                
	WIRELESS_INTERFACE=wlan0                                                                                                             
			
	# List of essids to recognise, in descending priority order (default /etc/essids)                                                    
	ESSID_LIST=/etc/essids
			
	# wpa_supplicant configuration file, (default /etc/wpa_supplicant.conf)                                                              
	WPA_SUPPLICANT_CONF=/etc/wpa_supplicant.conf
				
	# Kernel module to insert and remove (optional)
	WIRELESS_MODULE=iwlagn       
8. change the above variables to conform to your system
9. test it by running "sudo rc.d start wireless"
10. add "@wireless" to the "DAEMONS" array in "rc.conf" to autoconnect to a known network in range upon boot

(un-)supported features!
------------------------
* WPA/WPA2 is supported
* Open networks are supported
* WEP is not supported (yet?)
* DHCP is supported
* static network settings are not supported yet
* load/unload driver-modules for wifi-chip is supported, useful when dealing with annoying wifi-chips such as certain broadcom models
* more things that i forgot




		
