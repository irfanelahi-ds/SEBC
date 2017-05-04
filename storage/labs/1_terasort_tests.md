## Using Teragen:
Used the following command to use teragen:
time hadoop jar \
/opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar \
teragen \
-Ddfs.blocksize=32M \
-Dmapreduce.job.maps=4 \
1073741824  \
/irfanelahi-ds/two


because of space limitations, creating 1GB file instead of two.
