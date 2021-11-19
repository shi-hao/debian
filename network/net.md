# network interface    
    
## config file    
config file path:    
    
/etc/network/interfaces    
    
all the config content is in the above file, the file normally contains    
one comment : source-directory /etc/network/interfaces.d, so actually    
the interface config content is in diretory interfaces.d!    
    
    
## config network interface    
enter the dir /etc/network/interfaces.d/, open the interface file:    
**loopback interface**    
	auto lo    
	iface lo inet loopback    
    
**static config sample**    
	auto eth0    
	iface eth0 inet static    
	    address 192.168.159.62    
	    network 192.168.1.0    
	    netmask 255.255.255.0    
		up route add -net 192.168.100.0 netmask 255.255.255.0 gw 192.168.100.1    
		up route add default gw 192.168.200.1    
		down route del default gw 192.168.200.0    
		down route del -net -net 192.168.100.0 netmask 255.255.255.0 gw 192.168.10    
    
up route add   : when interface up, add route item.    
down route del : when interface down, del route item.    
    
**dhcp sample**    
	auto eth0    
	iface eth0 inet dhcp    
