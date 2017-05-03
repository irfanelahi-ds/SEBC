## Cloudera Manager Downloading and Installation:
	Firstly, download Cloudera Manager repo file as:
```
wget https://archive.cloudera.com/cm5/redhat/7/x86_64/cm/cloudera-manager.repo
```
Need to the cloudera-manager.repo file to download CM 5.9.2 instead of the latest version (5.11)
````
sudo vi cloudera-manager.repo 

*appended the cloudera manager version at the end of the baseurl key value pair.*
sudo cp cloudera-manager.repo /etc/yum.repos.d/
```

## Cloudera Manager installation using yum:
```
sudo yum install cloudera-manager-daemons cloudera-manager-server

*once done, need to configure the databases that Cloudera manager will use:
/usr/share/cmf/schema/scm_prepare_database.sh mysql cloudera cloudera cloudera -uroot -pcloudera 
```
Upon starting Cloudera Manager Server host using the following command resulted in failure:
```
sudo service cloudera-scm-server start
```
Upon parsing the log files, found that the possible cause was related to SELinux which was enabled, by default, so disabled that using the following command
```
sudo vi /etc/selinux/config
edit SELINUX=enforcing to disabled
reboot
```
This still did not fix the error. Parsed the logs again and found that JAVA_HOME wasn't initialized. Opened the following file and added JAVA_HOME to it.
```
sudo vi /etc/default/cloudera-scm-server
export JAVA_HOME=/opt/jdk1.8.0_121
```
Also exported JAVA_HOME environment variable.
MariaDB was not set to start on reboot so there was still an error in starting Cloudera Manager. Also set JAVA_HOME again
```
sudo service mariadb stop
sudo service mariadb start
sudo service mariadb status
export JAVA_HOME=/opt/jdk1.8.0_121

export JRE_HOME=/opt/jdk1.8.0_121/jre

export PATH=$PATH:/opt/jdk1.8.0_121/bin:/opt/jdk1.8.0_121/jre/bin:/bin

sudo vi /etc/environment
JAVA_HOME=/opt/jdk1.8.0_121
JRE_HOME=/opt/jdk1.8.0_121/jre
PATH=$PATH:/opt/jdk1.8.0_121/bin:/opt/jdk1.8.0_121/jre/bin:/bin

```
The Cloudera Manager process started however the web interface wasn't showing up. Upon troubleshooting, found that the AWS security group was blocking 7180 port that Cloudera Manager. I added the inbound rule to allow 7180 port in the EC2 instances security group.
```

Started Cloudera Manager Wizard using
```
http://52.65.127.89:7180
using username: admin password: admin
```
As a part of Cloudera Manager installation, it requires root SSH access. By default, EC2 instances don't allow root SSH access. This required the following changes to enable root SSH access.

```
vi /root/.ssh/authorized_keys
```
Deleted the lines at the begining of the file till "ssh-rsa".
```
vi /etc/ssh/sshd_config
```
Uncommented `PermitRootLogin` and replaced with `PermitRootLogin without-password`
Once done then did the following:
```
sudo service sshd reload
```
Used the same .ppk file. Didn't install JDK during installation wizard.
Once done, added all the hosts to the cluster from Cloudera Manager wizard and selected services to run on various nodes. Screenshot of services is attached.
Ensure that all services (HUE, Oozie, Activity Monitor, Resource Monitor) using database are installed on the respective node as this caused issues when testing connection for the databases.
Once installed, from Cloudera Manager configuration, changed Host Monitor, Service Monitor Storage and Zookeeper directories to /data_xvdb

During the process, Zookeeper threw an error of missing JDK directory because Cloudera Manager Wizard installed a different version of JDK than the one installed manually.
Also, Cloudera Manager 5.9 didn't support JDK 1.8 that I previously installed. 
This required installing  JDKs 1.7u80 using the following steps
```
Used WINSCP to transfer the download tar file on local windows machine to each EC2 node and then:
tar xzf jdk-7u80-linux-x64.tar.gz -C /usr/java/
export JAVA_HOME=/usr/java/jdk.1.7.0_80
vi /etc/default/cloudera-scm-server
change JAVA_HOME to export JAVA_HOME=/usr/java/jdk.1.7.0_80
sudo vi /etc/environment
JAVA_HOME=/usr/java/jdk.1.7.0_80
JRE_HOME=/usr/java/jdk.1.7.0_80/jre
PATH=$PATH:/usr/java/jdk.1.7.0_80/bin:/usr/java/jdk.1.7.0_80/jre/bin:/bin
```

Recommendation: manually install the same and compliant JDK to all the nodes in a cluster instead of having CM install it for you so that all versions are the same.

Also, there is an option to enter Java Home Directory in Hosts Configuration section using Cloudera Manager but avoid it as it causes conflicts with the environment settings.
For nodes not having Cloudera Manager Server edit the cloudera-scm-agent file 
to export the JAVA_HOME.
Changed all the log directories in services and cloudera management services to /data_xvdb and also change Cloudera Management Service Command Storage Directory.

I was getting Agent Log Directory space error and I tried the following but didn't work:
Changing the config.ini for agent to data_xvdb
 https://www.cloudera.com/documentation/enterprise/5-4-x/topics/cm_ag_view_server_logs.html

sudo vi /etc/cloudera-scm-agent/config.ini
uncomment log_file add /data_xvdb
mkdir -p /data_xvdb/var/log/cloudera-scm-agent
chown cloudera-scm:cloudera-scm /data_xvdb/var/log/cloudera-scm-agent
service cloudera-scm-agent restart

## DNS Resolution Error:
During the process, I was getting DNS Resolution error in hosts. I used the following command to resolve them:

vi /etc/sysconfig/network
added the following line:
HOSTNAME=<public DNS address>
save and then:
hostnamectl set-hostname "ec2-52-65-127-89.ap-southeast-2.compute.amazonaws.com" --static


and then restart cloudera scm agent. Also, while doing restart, stop all of them sequentially and then start in the same order.

service cloudera-scm-agent stop
service cloudera-scm-agent start


