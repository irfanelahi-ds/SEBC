# HDFS Storage Labs
## Storage Replication

Created source folder in hdfs using the following commands:
```
sudo -u hdfs hadoop fs -mkdir /irfanelahi-ds
sudo -u hdfs hadoop fs -mkdir /fahad85
```

to run Teragen to generate 500MB data, used the following command:
```
sudo -u hdfs hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar teragen 524288000 /fahad85
```
This fails with the error that the directory already exists. Deleted the directory and ran the command above again which resulted in a mapreduce job.

## Test HDFS Performance

Create end-user and its HDFS home directory as follows:

```
sudo useradd
sudo -u hdfs hadoop fs -mkdir /user/fahad85 fahad85
sudo -u hdfs hadoop fs -chmod 777 /user/fahad85
``` 

## Replication using distcp:
To use distcp to copy file from local /irfanelahi-ds hdfs to destination, the command has to be executed from the destination cluster:

sudo -u hdfs hadoop distcp hdfs://ec2-54-252-147-158.ap-southeast-2.compute.amazonaws.com:8020/irfanelahi-ds hdfs:// \ec2-52-65-127-89.ap-southeast-2.compute.amazonaws.com:8020/irfanelahi-ds

## For BDR:
In the cloudera manager and in the backup cluster, go to Backup-> Peers and add PEER and specify cloudera manager details there. Once done, create a schedule by specifying the path to read from production/source cluster and writing to backup cluster.


## Enabling HDFS HA:
Add journal nodes from HDFS -> Actions -> Add Role instances. Its recommended that it should be installed on the master nodes. however decide as per available space.
Once done, go to HDFS -> Configuration and specify edit directories (/data_xvdb/journal). Once done, go to HDFS -> Enable HA. Follow the wizard. In the standby namenode section, select any node (other than primary node) and proceed.
