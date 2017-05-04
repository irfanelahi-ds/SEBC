## List the cloud provider you are using (AWS, GCE, Azure, other)
```
AWS
```

## List the nodes you are using by IP address and name:
``` 
172.31.7.102 ec2-13-54-76-174.ap-southeast-2.compute.amazonaws.com
172.31.1.7 ec2-13-55-147-75.ap-southeast-2.compute.amazonaws.com
172.31.5.143 ec2-13-55-141-169.ap-southeast-2.compute.amazonaws.com
172.31.14.119 ec2-52-62-213-29.ap-southeast-2.compute.amazonaws.com
172.31.4.195 ec2-52-63-10-115.ap-southeast-2.compute.amazonaws.com

```

## List the Linux release you are using
```
Red Hat Enterprise Linux Server release 7.2 (Maipo)
```

##Demonstrate the disk capacity available on each node is >= 30 GB
```
[root@ip-172-31-7-102 ec2-user]# df -kh
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda2       50G  1.6G   49G   4% /
devtmpfs        7.3G     0  7.3G   0% /dev
tmpfs           7.2G     0  7.2G   0% /dev/shm
tmpfs           7.2G   17M  7.2G   1% /run
tmpfs           7.2G     0  7.2G   0% /sys/fs/cgroup
tmpfs           1.5G     0  1.5G   0% /run/user/1000


[root@ip-172-31-1-7 ec2-user]# df -kh
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda2       50G  1.6G   49G   4% /
devtmpfs        7.3G     0  7.3G   0% /dev
tmpfs           7.2G     0  7.2G   0% /dev/shm
tmpfs           7.2G   17M  7.2G   1% /run
tmpfs           7.2G     0  7.2G   0% /sys/fs/cgroup
tmpfs           1.5G     0  1.5G   0% /run/user/1000

[root@ip-172-31-5-143 ec2-user]# df -kh
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda2       50G  1.6G   49G   4% /
devtmpfs        7.3G     0  7.3G   0% /dev
tmpfs           7.2G     0  7.2G   0% /dev/shm
tmpfs           7.2G   17M  7.2G   1% /run
tmpfs           7.2G     0  7.2G   0% /sys/fs/cgroup
tmpfs           1.5G     0  1.5G   0% /run/user/1000


[root@ip-172-31-5-143 ec2-user]# df -kh
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda2       50G  1.6G   49G   4% /
devtmpfs        7.3G     0  7.3G   0% /dev
tmpfs           7.2G     0  7.2G   0% /dev/shm
tmpfs           7.2G   17M  7.2G   1% /run
tmpfs           7.2G     0  7.2G   0% /sys/fs/cgroup
tmpfs           1.5G     0  1.5G   0% /run/user/1000



[root@ip-172-31-14-119 ec2-user]# df -kh
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda2       50G  1.6G   49G   4% /
devtmpfs        7.3G     0  7.3G   0% /dev
tmpfs           7.2G     0  7.2G   0% /dev/shm
tmpfs           7.2G   17M  7.2G   1% /run
tmpfs           7.2G     0  7.2G   0% /sys/fs/cgroup
tmpfs           1.5G     0  1.5G   0% /run/user/1000

[root@ip-172-31-4-195 ec2-user]# df -kh
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvda2       50G  1.6G   49G   4% /
devtmpfs        7.3G     0  7.3G   0% /dev
tmpfs           7.2G     0  7.2G   0% /dev/shm
tmpfs           7.2G   17M  7.2G   1% /run
tmpfs           7.2G     0  7.2G   0% /sys/fs/cgroup
tmpfs           1.5G     0  1.5G   0% /run/user/1000



```

## List the command and output for yum repolist enabled
```
[root@ip-172-31-7-102 ec2-user]# yum repolist enabled
Loaded plugins: amazon-id, rhui-lb, search-disabled-repos
repo id                                           repo name               status
!rhui-REGION-client-config-server-7/x86_64        Red Hat Update Infrastr      6
!rhui-REGION-rhel-server-releases/7Server/x86_64  Red Hat Enterprise Linu 14,277
!rhui-REGION-rhel-server-rh-common/7Server/x86_64 Red Hat Enterprise Linu    228
repolist: 14,511

```
## /etc/passwd entries:
```
cate:x:2300:2300::/home/cate:/bin/bash
jemaine:x:2900:2900::/home/jemaine:/bin/bash

```

## /etc/group entries:
```

kiwis:x:2901:jemaine
aussies:x:2902:cate
```
