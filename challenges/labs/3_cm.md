## output for hdfs dfs -ls /user
```
[root@ip-172-31-7-102 ec2-user]# hdfs dfs -ls /user
Found 7 items
drwxr-xr-x   - hdfs   supergroup          0 2017-05-04 21:31 /user/cate
drwxrwxrwx   - mapred hadoop              0 2017-05-04 21:26 /user/history
drwxrwxr-t   - hive   hive                0 2017-05-04 21:26 /user/hive
drwxrwxr-x   - hue    hue                 0 2017-05-04 21:27 /user/hue
drwxrwxr-x   - impala impala              0 2017-05-04 21:27 /user/impala
drwxr-xr-x   - hdfs   supergroup          0 2017-05-04 21:31 /user/jemaine
drwxrwxr-x   - oozie  oozie               0 2017-05-04 21:27 /user/oozie
```

## API Command output:
```
curl -X GET -u "admin:admin" -i http://ec2-13-54-76-174.ap-southeast-2.compute.amazonaws.com:7180/api/v14/hosts 

output:
```
[root@ip-172-31-7-102 ec2-user]#  curl -X GET -u "admin:admin" -i http://ec2-13-54-76-174.ap-southeast-2.compute.amazonaws.com:7180/api/v14/hosts
HTTP/1.1 200 OK
Expires: Thu, 01-Jan-1970 00:00:00 GMT
Set-Cookie: CLOUDERA_MANAGER_SESSIONID=m3a0bjb28oehcdiyr2mje2re;Path=/;HttpOnly
Content-Type: application/json
Date: Fri, 05 May 2017 01:35:28 GMT
Transfer-Encoding: chunked
Server: Jetty(6.1.26.cloudera.4)

{
  "items" : [ {
    "hostId" : "2fdda0ca-42c3-4b88-bc2b-d116fad74400",
    "ipAddress" : "172.31.7.102",
    "hostname" : "ec2-13-54-76-174.ap-southeast-2.compute.amazonaws.com",
    "rackId" : "/default",
    "hostUrl" : "http://ec2-13-54-76-174.ap-southeast-2.compute.amazonaws.com:7180/cmf/hostRedirect/2fdda0ca-42c3-4b88-bc2b-d116fad74400",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332438016
  }, {
    "hostId" : "f235a2f4-0c7c-4018-a6a7-887b5f35317e",
    "ipAddress" : "172.31.5.143",
    "hostname" : "ec2-13-55-141-169.ap-southeast-2.compute.amazonaws.com",
    "rackId" : "/default",
    "hostUrl" : "http://ec2-13-54-76-174.ap-southeast-2.compute.amazonaws.com:7180/cmf/hostRedirect/f235a2f4-0c7c-4018-a6a7-887b5f35317e",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332438016
  }, {
    "hostId" : "f47e48c9-18a5-4e3f-bea6-790c7aba067f",
    "ipAddress" : "172.31.1.7",
    "hostname" : "ec2-13-55-147-75.ap-southeast-2.compute.amazonaws.com",
    "rackId" : "/default",
    "hostUrl" : "http://ec2-13-54-76-174.ap-southeast-2.compute.amazonaws.com:7180/cmf/hostRedirect/f47e48c9-18a5-4e3f-bea6-790c7aba067f",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332438016
  }, {
    "hostId" : "bb2cc1e8-141a-4635-882c-e8d8a50ae556",
    "ipAddress" : "172.31.14.119",
    "hostname" : "ec2-52-62-213-29.ap-southeast-2.compute.amazonaws.com",
    "rackId" : "/default",
    "hostUrl" : "http://ec2-13-54-76-174.ap-southeast-2.compute.amazonaws.com:7180/cmf/hostRedirect/bb2cc1e8-141a-4635-882c-e8d8a50ae556",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332438016
  }, {
    "hostId" : "1a07486c-ce7a-445b-bd3d-307a25e99e07",
    "ipAddress" : "172.31.4.195",
    "hostname" : "ec2-52-63-10-115.ap-southeast-2.compute.amazonaws.com",
    "rackId" : "/default",
    "hostUrl" : "http://ec2-13-54-76-174.ap-southeast-2.compute.amazonaws.com:7180/cmf/hostRedirect/1a07486c-ce7a-445b-bd3d-307a25e99e07",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "commissionState" : "COMMISSIONED",
    "numCores" : 4,
    "numPhysicalCores" : 2,
    "totalPhysMemBytes" : 15332438016
  } ]

```
## API call for Services:

```
[root@ip-172-31-7-102 ec2-user]# curl -X GET -u "admin:admin" -i http://ec2-13-54-76-174.ap-southeast-2.compute.amazonaws.com:7180/api/v6/clusters/irfanelahi-ds/services
HTTP/1.1 200 OK
Expires: Thu, 01-Jan-1970 00:00:00 GMT
Set-Cookie: CLOUDERA_MANAGER_SESSIONID=sa54npmbzcqq8yuejg7dgp6a;Path=/;HttpOnly
Content-Type: application/json
Date: Fri, 05 May 2017 02:10:19 GMT
Transfer-Encoding: chunked
Server: Jetty(6.1.26.cloudera.4)

{
  "items" : [ {
    "name" : "hive",
    "type" : "HIVE",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://ec2-13-54-76-174.ap-southeast-2.compute.amazonaws.com:7180/cmf/serviceRedirect/hive",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "HIVE_HIVEMETASTORES_HEALTHY",
      "summary" : "GOOD"
    }, {
      "name" : "HIVE_HIVESERVER2S_HEALTHY",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Hive"
  }, {
    "name" : "zookeeper",
    "type" : "ZOOKEEPER",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://ec2-13-54-76-174.ap-southeast-2.compute.amazonaws.com:7180/cmf/serviceRedirect/zookeeper",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "ZOOKEEPER_CANARY_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "ZOOKEEPER_SERVERS_HEALTHY",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "ZooKeeper"
  }, {
    "name" : "hue",
    "type" : "HUE",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://ec2-13-54-76-174.ap-southeast-2.compute.amazonaws.com:7180/cmf/serviceRedirect/hue",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "HUE_HUE_SERVERS_HEALTHY",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Hue"
  }, {
    "name" : "oozie",
    "type" : "OOZIE",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://ec2-13-54-76-174.ap-southeast-2.compute.amazonaws.com:7180/cmf/serviceRedirect/oozie",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "OOZIE_OOZIE_SERVERS_HEALTHY",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Oozie"
  }, {
    "name" : "impala",
    "type" : "IMPALA",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://ec2-13-54-76-174.ap-southeast-2.compute.amazonaws.com:7180/cmf/serviceRedirect/impala",
    "serviceState" : "STARTED",
    "healthSummary" : "BAD",
    "healthChecks" : [ {
      "name" : "IMPALA_ASSIGNMENT_LOCALITY",
      "summary" : "DISABLED"
    }, {
      "name" : "IMPALA_CATALOGSERVER_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "IMPALA_IMPALADS_HEALTHY",
      "summary" : "GOOD"
    }, {
      "name" : "IMPALA_STATESTORE_HEALTH",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "Impala"
  }, {
    "name" : "yarn",
    "type" : "YARN",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://ec2-13-54-76-174.ap-southeast-2.compute.amazonaws.com:7180/cmf/serviceRedirect/yarn",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "YARN_JOBHISTORY_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "YARN_NODE_MANAGERS_HEALTHY",
      "summary" : "GOOD"
    }, {
      "name" : "YARN_RESOURCEMANAGERS_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "YARN_USAGE_AGGREGATION_HEALTH",
      "summary" : "DISABLED"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "YARN (MR2 Included)"
  }, {
    "name" : "hdfs",
    "type" : "HDFS",
    "clusterRef" : {
      "clusterName" : "cluster"
    },
    "serviceUrl" : "http://ec2-13-54-76-174.ap-southeast-2.compute.amazonaws.com:7180/cmf/serviceRedirect/hdfs",
    "serviceState" : "STARTED",
    "healthSummary" : "GOOD",
    "healthChecks" : [ {
      "name" : "HDFS_BLOCKS_WITH_CORRUPT_REPLICAS",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_CANARY_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_DATA_NODES_HEALTHY",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_FREE_SPACE_REMAINING",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_HA_NAMENODE_HEALTH",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_MISSING_BLOCKS",
      "summary" : "GOOD"
    }, {
      "name" : "HDFS_UNDER_REPLICATED_BLOCKS",
      "summary" : "GOOD"
    } ],
    "configStalenessStatus" : "FRESH",
    "clientConfigStalenessStatus" : "FRESH",
    "maintenanceMode" : false,
    "maintenanceOwners" : [ ],
    "displayName" : "HDFS"
  } ]



  ```