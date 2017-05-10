#Report the latest available version of the API

```
[root@ip-172-31-37-12 etc]# curl -X GET -u "littlecong:cloudera" -i http://ec2-34-208-80-199.us-west-2.compute.amazonaws.com:7180/api/version
HTTP/1.1 200 OK
Expires: Thu, 01-Jan-1970 00:00:00 GMT
Set-Cookie: CLOUDERA_MANAGER_SESSIONID=16hqjwg0t2bv6cgp7ci2kx3od;Path=/;HttpOnly
Content-Type: application/json
Date: Wed, 10 May 2017 06:33:10 GMT
Content-Length: 3
Server: Jetty(6.1.26.cloudera.4)

v16
```

#Report the CM version
```
[root@ip-172-31-37-12 etc]# curl -X GET -u "littlecong:cloudera" -i http://ec2-34-208-80-199.us-west-2.compute.amazonaws.com:7180/api/v16/cm/version
HTTP/1.1 200 OK
Expires: Thu, 01-Jan-1970 00:00:00 GMT
Set-Cookie: CLOUDERA_MANAGER_SESSIONID=1u0sm5b1thmufs9o538c0hgxv;Path=/;HttpOnly
Content-Type: application/json
Date: Wed, 10 May 2017 06:39:33 GMT
Transfer-Encoding: chunked
Server: Jetty(6.1.26.cloudera.4)

{
  "version" : "5.11.0",
  "buildUser" : "jenkins",
  "buildTimestamp" : "20170412-1249",
  "gitHash" : "70cb1442626406432a6e7af5bdf206a384ca3f98",
  "snapshot" : false
}
```

#List all CM users
```
[root@ip-172-31-37-12 etc]# curl -X GET -u "littlecong:cloudera" -i http://ec2-34-208-80-199.us-west-2.compute.amazonaws.com:7180/api/v16/users
HTTP/1.1 200 OK
Expires: Thu, 01-Jan-1970 00:00:00 GMT
Set-Cookie: CLOUDERA_MANAGER_SESSIONID=sjgyq6i84rf166voaeztvcsj;Path=/;HttpOnly
Content-Type: application/json
Date: Wed, 10 May 2017 06:41:37 GMT
Transfer-Encoding: chunked
Server: Jetty(6.1.26.cloudera.4)

{
  "items" : [ {
    "name" : "admin",
    "roles" : [ "ROLE_LIMITED" ]
  }, {
    "name" : "littlecong",
    "roles" : [ "ROLE_ADMIN" ]
  }, {
    "name" : "minotaur",
    "roles" : [ "ROLE_CONFIGURATOR" ]
  } ]
}
```
#Report the database server in use by CM

```
[root@ip-172-31-37-12 etc]# curl -X GET -u "littlecong:cloudera" -i http://ec2-34-208-80-199.us-west-2.compute.amazonaws.com:7180/api/v16/cm/scmDbInfo
HTTP/1.1 200 OK
Expires: Thu, 01-Jan-1970 00:00:00 GMT
Set-Cookie: CLOUDERA_MANAGER_SESSIONID=gozt7w88287p8i1cckft1337;Path=/;HttpOnly
Content-Type: application/json
Date: Wed, 10 May 2017 06:54:43 GMT
Transfer-Encoding: chunked
Server: Jetty(6.1.26.cloudera.4)

{
  "scmDbType" : "MYSQL",
  "embeddedDbUsed" : false
}
```