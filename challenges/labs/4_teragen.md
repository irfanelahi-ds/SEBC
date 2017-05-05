## teragen command:
```
[cate@ip-172-31-7-102 ec2-user]$ time hadoop jar \
> /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar \
> teragen \
> -Ddfs.blocksize=16M \
> -Dmapreduce.job.maps=8 \
> -Dmapreduce.map.java.opts.max.heap=512M \
> -Dmapreduce.job.reduces=8 \
> 65536000  \
> /user/cate/tgen

```

## teragen command output:
```
[cate@ip-172-31-7-102 ec2-user]$ time hadoop jar \
> /opt/cloudera/parcels/CDH/lib/hadoop-0.20-mapreduce/hadoop-examples.jar \
> teragen \
> -Ddfs.blocksize=16M \
> -Dmapreduce.job.maps=8 \
> -Dmapreduce.map.java.opts.max.heap=512M \
> -Dmapreduce.job.reduces=8 \
> 65536000  \
> /user/cate/tgen
17/05/04 21:59:08 INFO client.RMProxy: Connecting to ResourceManager at ec2-13-54-76-174.ap-southeast-2.compute.amazonaws.com/172.31.7.102:8032
17/05/04 21:59:09 INFO terasort.TeraGen: Generating 65536000 using 8
17/05/04 21:59:09 INFO mapreduce.JobSubmitter: number of splits:8
17/05/04 21:59:09 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1493947577867_0002
17/05/04 21:59:09 INFO impl.YarnClientImpl: Submitted application application_1493947577867_0002
17/05/04 21:59:09 INFO mapreduce.Job: The url to track the job: http://ec2-13-54-76-174.ap-southeast-2.compute.amazonaws.com:8088/proxy/application_1493947577867_0002/
17/05/04 21:59:09 INFO mapreduce.Job: Running job: job_1493947577867_0002
17/05/04 21:59:17 INFO mapreduce.Job: Job job_1493947577867_0002 running in uber mode : false
17/05/04 21:59:17 INFO mapreduce.Job:  map 0% reduce 0%
17/05/04 21:59:34 INFO mapreduce.Job:  map 5% reduce 0%
17/05/04 21:59:35 INFO mapreduce.Job:  map 33% reduce 0%
17/05/04 21:59:40 INFO mapreduce.Job:  map 34% reduce 0%
17/05/04 21:59:41 INFO mapreduce.Job:  map 38% reduce 0%
17/05/04 21:59:47 INFO mapreduce.Job:  map 41% reduce 0%
17/05/04 21:59:52 INFO mapreduce.Job:  map 43% reduce 0%
17/05/04 21:59:53 INFO mapreduce.Job:  map 55% reduce 0%
17/05/04 21:59:58 INFO mapreduce.Job:  map 57% reduce 0%
17/05/04 21:59:59 INFO mapreduce.Job:  map 63% reduce 0%
17/05/04 22:00:04 INFO mapreduce.Job:  map 64% reduce 0%
17/05/04 22:00:05 INFO mapreduce.Job:  map 67% reduce 0%
17/05/04 22:00:10 INFO mapreduce.Job:  map 70% reduce 0%
17/05/04 22:00:11 INFO mapreduce.Job:  map 80% reduce 0%
17/05/04 22:00:17 INFO mapreduce.Job:  map 83% reduce 0%
17/05/04 22:00:21 INFO mapreduce.Job:  map 84% reduce 0%
17/05/04 22:00:23 INFO mapreduce.Job:  map 85% reduce 0%
17/05/04 22:00:27 INFO mapreduce.Job:  map 87% reduce 0%
17/05/04 22:00:28 INFO mapreduce.Job:  map 88% reduce 0%
17/05/04 22:00:33 INFO mapreduce.Job:  map 96% reduce 0%
17/05/04 22:00:35 INFO mapreduce.Job:  map 100% reduce 0%
17/05/04 22:00:36 INFO mapreduce.Job: Job job_1493947577867_0002 completed successfully
17/05/04 22:00:36 INFO mapreduce.Job: Counters: 33
        File System Counters
                FILE: Number of bytes read=0
                FILE: Number of bytes written=1023416
                FILE: Number of read operations=0
                FILE: Number of large read operations=0
                FILE: Number of write operations=0
                HDFS: Number of bytes read=682
                HDFS: Number of bytes written=6553600000
                HDFS: Number of read operations=32
                HDFS: Number of large read operations=0
                HDFS: Number of write operations=16
        Job Counters
                Launched map tasks=8
                Other local map tasks=8
                Total time spent by all maps in occupied slots (ms)=473074
                Total time spent by all reduces in occupied slots (ms)=0
                Total time spent by all map tasks (ms)=473074
                Total vcore-milliseconds taken by all map tasks=473074
                Total megabyte-milliseconds taken by all map tasks=484427776
        Map-Reduce Framework
                Map input records=65536000
                Map output records=65536000
                Input split bytes=682
                Spilled Records=0
                Failed Shuffles=0
                Merged Map outputs=0
                GC time elapsed (ms)=1214
                CPU time spent (ms)=136120
                Physical memory (bytes) snapshot=2752229376
                Virtual memory (bytes) snapshot=12616417280
                Total committed heap usage (bytes)=2832203776
                Peak Map Physical memory (bytes)=382357504
                Peak Map Virtual memory (bytes)=1581101056
        org.apache.hadoop.examples.terasort.TeraGen$Counters
                CHECKSUM=140750829423462787
        File Input Format Counters
                Bytes Read=0
        File Output Format Counters
                Bytes Written=6553600000


## time command output:
```
real    1m31.093s
user    0m6.471s
sys     0m0.308s

```

## output of hdfs dfs -ls command:

```

[cate@ip-172-31-7-102 ec2-user]$ hadoop fs -ls /user/cate/tgen
Found 9 items
-rw-r--r--   3 cate supergroup          0 2017-05-04 22:00 /user/cate/tgen/_SUCCESS
-rw-r--r--   3 cate supergroup  819200000 2017-05-04 22:00 /user/cate/tgen/part-m-00000
-rw-r--r--   3 cate supergroup  819200000 2017-05-04 22:00 /user/cate/tgen/part-m-00001
-rw-r--r--   3 cate supergroup  819200000 2017-05-04 22:00 /user/cate/tgen/part-m-00002
-rw-r--r--   3 cate supergroup  819200000 2017-05-04 22:00 /user/cate/tgen/part-m-00003
-rw-r--r--   3 cate supergroup  819200000 2017-05-04 22:00 /user/cate/tgen/part-m-00004
-rw-r--r--   3 cate supergroup  819200000 2017-05-04 22:00 /user/cate/tgen/part-m-00005
-rw-r--r--   3 cate supergroup  819200000 2017-05-04 22:00 /user/cate/tgen/part-m-00006
-rw-r--r--   3 cate supergroup  819200000 2017-05-04 22:00 /user/cate/tgen/part-m-00007

```