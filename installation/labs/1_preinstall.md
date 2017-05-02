## Checking and Setting VM Swappiness
```
For checking the VM Swappiness value
	: cat /proc/sys/vm/swappiness
    For setting the value to 1: 
    sudo su root
    sudo echo 1 > /proc/sys/vm/swappiness
```

## Mount Attributes of Volumes:
```
Mounted the volumes using the following steps:
	first checking what devices are available using:
	lsblk
	checking if file system is installed on the device:
	sudo file -s /dev/xvdb
	if it shows data in output, it means no filesystem is installed thus:
	sudo mkfs -t ext4 /dev/xvdb
	sudo mkdir /data_xvdb
	sudo mount /dev/xvdb /data_xvdb

	to check UUID of the mounted volume:
	 
	ls -al /dev/disk/by-uuid/

	then: vi /etc/fstab so that volume is mounted on bootup:
	to check the properties:
	used df -k and lsblk to output physical volumes attributes
``` 

## Ext4 File System reserved space:
```
	Using the following command to list reserved space:
	tune2fs -l /dev/xvdb
	Sample output screenshot is attached.
```

## Transparent HugePage:
``` 
	To check if its enabled:
	 cat /sys/kernel/mm/transparent_hugepage/enabled
	[always] madvise never
	The currently active option is in brackets. In my case, its [always].
	To change it to never:
	echo never >/sys/kernel/mm/transparent_hugepage/enabled
```

## Network Interface Configuration:
```
used ifconfig command to list network configuration. 
   Attached the screenshot as well.
```

## Correct forward and reverse host lookups:
```
	Changed the hostname of all nodes to their respective public DNS.
	Edited the /etc/hosts file and added the following entries:
	172.31.1.97   ec2-52-65-127-89.ap-southeast-2.compute.amazonaws.com
	172.31.11.249  ec2-52-65-127-52.ap-southeast-2.compute.amazonaws.com
	172.31.12.213   ec2-52-65-85-107.ap-southeast-2.compute.amazonaws.com
	172.31.13.166   ec2-52-65-124-145.ap-southeast-2.compute.amazonaws.com
	172.31.10.19   ec2-13-55-91-183.ap-southeast-2.compute.amazonaws.com

	and then confirming with getent as:
	getent hosts 52.65.127.89
	and it shows the output. Screenshot is attached.
```

## NSCD Service:
```
	Firstly need to check if its running:
	sudo service nscd status
	if its not present,  need to install it using
	sudo yum install nscd 
	then to start:
	sudo service nscd start

	and then to check the status:
	sudo service nscd status

	Screenshot is attached as well.
```
## NTPD Service:
```
	Firstly need to check if its running:
	sudo service ntpd status
	if its not present,  need to install it using
	sudo yum install ntp 
	then to start:
	sudo service ntpd start

	and then to check the status:
	sudo service ntpd status

	Screenshot is attached as well.