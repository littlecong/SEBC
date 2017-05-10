Stop Hive
```
[hdfs@ip-172-31-37-12 tmp]$ curl -X POST -u "littlecong:cloudera" -i http://ec2-34-208-80-199.us-west-2.compute.amazonaws.com:7180/api/v12/clusters/cluster/services/hive/commands/stop
HTTP/1.1 200 OK
Expires: Thu, 01-Jan-1970 00:00:00 GMT
Set-Cookie: CLOUDERA_MANAGER_SESSIONID=1irpwkbtuvv6pg16o7j23xoi7;Path=/;HttpOnly
Content-Type: application/json
Date: Wed, 10 May 2017 04:33:00 GMT
Transfer-Encoding: chunked
Server: Jetty(6.1.26.cloudera.4)

{
  "id" : 1103,
  "name" : "Stop",
  "startTime" : "2017-05-10T04:33:00.808Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}
```
Check Hive status

```
[hdfs@ip-172-31-37-12 tmp]$ curl -X GET -u "littlecong:cloudera" -i http://ec2-34-208-80-199.us-west-2.compute.amazonaws.com:7180/api/v12/clusters/cluster/services/hive
HTTP/1.1 200 OK
Expires: Thu, 01-Jan-1970 00:00:00 GMT
Set-Cookie: CLOUDERA_MANAGER_SESSIONID=1p5qt03q31r386qhg95ky1zfo;Path=/;HttpOnly
Content-Type: application/json
Date: Wed, 10 May 2017 04:33:39 GMT
Transfer-Encoding: chunked
Server: Jetty(6.1.26.cloudera.4)

{
  "name" : "hive",
  "type" : "HIVE",
  "clusterRef" : {
    "clusterName" : "cluster"
  },
  "serviceUrl" : "http://ip-172-31-37-12.us-west-2.compute.internal:7180/cmf/serviceRedirect/hive",
  "roleInstancesUrl" : "http://ip-172-31-37-12.us-west-2.compute.internal:7180/cmf/serviceRedirect/hive/instances",
  "serviceState" : "STOPPED",
  "healthSummary" : "DISABLED",
  "healthChecks" : [ {
    "name" : "HIVE_HIVEMETASTORES_HEALTHY",
    "summary" : "DISABLED",
    "suppressed" : false
  }, {
    "name" : "HIVE_HIVESERVER2S_HEALTHY",
    "summary" : "DISABLED",
    "suppressed" : false
  } ],
  "configStalenessStatus" : "FRESH",
  "clientConfigStalenessStatus" : "FRESH",
  "maintenanceMode" : false,
  "maintenanceOwners" : [ ],
  "displayName" : "Hive",
  "entityStatus" : "STOPPED"
```
Start Hive
```
[hdfs@ip-172-31-37-12 tmp]$ curl -X POST -u "littlecong:cloudera" -i http://ec2-34-208-80-199.us-west-2.compute.amazonaws.com:7180/api/v12/clusters/cluster/services/hive/commands/start
HTTP/1.1 200 OK
Expires: Thu, 01-Jan-1970 00:00:00 GMT
Set-Cookie: CLOUDERA_MANAGER_SESSIONID=wwbvvjhkhgth9uk5bed0oeeq;Path=/;HttpOnly
Content-Type: application/json
Date: Wed, 10 May 2017 04:34:12 GMT
Transfer-Encoding: chunked
Server: Jetty(6.1.26.cloudera.4)

{
  "id" : 1107,
  "name" : "Start",
  "startTime" : "2017-05-10T04:34:11.871Z",
  "active" : true,
  "serviceRef" : {
    "clusterName" : "cluster",
    "serviceName" : "hive"
  }
}
```
Check Hive status
```
[hdfs@ip-172-31-37-12 tmp]$ curl -X GET -u "littlecong:cloudera" -i http://ec2-34-208-80-199.us-west-2.compute.amazonaws.com:7180/api/v12/clusters/cluster/services/hive
HTTP/1.1 200 OK
Expires: Thu, 01-Jan-1970 00:00:00 GMT
Set-Cookie: CLOUDERA_MANAGER_SESSIONID=1d1th6wx4spcxneqyfxo4op3s;Path=/;HttpOnly
Content-Type: application/json
Date: Wed, 10 May 2017 04:34:43 GMT
Transfer-Encoding: chunked
Server: Jetty(6.1.26.cloudera.4)

{
  "name" : "hive",
  "type" : "HIVE",
  "clusterRef" : {
    "clusterName" : "cluster"
  },
  "serviceUrl" : "http://ip-172-31-37-12.us-west-2.compute.internal:7180/cmf/serviceRedirect/hive",
  "roleInstancesUrl" : "http://ip-172-31-37-12.us-west-2.compute.internal:7180/cmf/serviceRedirect/hive/instances",
  "serviceState" : "STARTED",
  "healthSummary" : "DISABLED",
  "healthChecks" : [ {
    "name" : "HIVE_HIVEMETASTORES_HEALTHY",
    "summary" : "DISABLED",
    "suppressed" : false
  }, {
    "name" : "HIVE_HIVESERVER2S_HEALTHY",
    "summary" : "DISABLED",
    "suppressed" : false
  } ],
  "configStalenessStatus" : "FRESH",
  "clientConfigStalenessStatus" : "FRESH",
  "maintenanceMode" : false,
  "maintenanceOwners" : [ ],
  "displayName" : "Hive",
  "entityStatus" : "DISABLED_HEALTH"
}
```