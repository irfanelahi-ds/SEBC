## Using Teragen:
Used the following command to use teragen:
time hadoop jar \
/opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar \
teragen \
-Ddfs.blocksize=32M \
-Dmapreduce.job.maps=4 \
104857600  \
/irfanelahi-ds/two

to create 10GB file.

Here 104857600 represents number of rows. As one row is of 100bytes so it has to be carefully considered while producing file of a specific size. Multiply the specified value with 100 to get approximate size of file generated.


Due to space limitations i.e. the / directory is 100% full, its not running the tera-sort command on 10GB data.

Using the following command for terasort on 1GB data:

time hadoop jar /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar terasort /irfanelahi-ds/teragen_data /irfanelahi-ds/terasort_results

Reported time:

real    1m15.356s
user    1m24.799s
sys     0m6.211s
