# before grant 
```
beeline> !connect jdbc:hive2://ip-172-31-37-146:10000/default;principal=hive/ip-172-31-37-146.us-west-2.compute.internal@CONG.COM
scan complete in 2ms
Connecting to jdbc:hive2://ip-172-31-37-146:10000/default;principal=hive/ip-172-31-37-146.us-west-2.compute.internal@CONG.COM
Connected to: Apache Hive (version 1.1.0-cdh5.9.2)
Driver: Hive JDBC (version 1.1.0-cdh5.9.2)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-31-37-146:10000/defaul> show tables;
INFO  : Compiling command(queryId=hive_20170510091818_0ed34fb2-f09c-45bd-86ba-86950d8f01a6): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170510091818_0ed34fb2-f09c-45bd-86ba-86950d8f01a6); Time taken: 0.839 seconds
INFO  : Executing command(queryId=hive_20170510091818_0ed34fb2-f09c-45bd-86ba-86950d8f01a6): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170510091818_0ed34fb2-f09c-45bd-86ba-86950d8f01a6); Time taken: 0.458 seconds
INFO  : OK
+-----------+--+
| tab_name  |
+-----------+--+
+-----------+--+
No rows selected (2.687 seconds)
```

# kinit as george, then login to beeline
```
[root@ip-172-31-37-12 process]# kinit george
Password for george@CONG.COM: 
[root@ip-172-31-37-12 process]# beeline
Beeline version 1.1.0-cdh5.9.2 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-31-37-146:10000/default;principal=hive/ip-172-31-37-146.us-west-2.compute.internal@CONG.COM
scan complete in 2ms
Connecting to jdbc:hive2://ip-172-31-37-146:10000/default;principal=hive/ip-172-31-37-146.us-west-2.compute.internal@CONG.COM
Connected to: Apache Hive (version 1.1.0-cdh5.9.2)
Driver: Hive JDBC (version 1.1.0-cdh5.9.2)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-31-37-146:10000/defaul> show tables;
INFO  : Compiling command(queryId=hive_20170510104747_0856467e-bf93-4a9a-a888-93bdd7c0c9c2): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170510104747_0856467e-bf93-4a9a-a888-93bdd7c0c9c2); Time taken: 0.256 seconds
INFO  : Executing command(queryId=hive_20170510104747_0856467e-bf93-4a9a-a888-93bdd7c0c9c2): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170510104747_0856467e-bf93-4a9a-a888-93bdd7c0c9c2); Time taken: 0.217 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| customers  |
| sample_07  |
| sample_08  |
| web_logs   |
+------------+--+
4 rows selected (0.662 seconds)
0: jdbc:hive2://ip-172-31-37-146:10000/defaul> !quit
Closing: 0: jdbc:hive2://ip-172-31-37-146:10000/default;principal=hive/ip-172-31-37-146.us-west-2.compute.internal@CONG.COM
[root@ip-172-31-37-12 process]# kdestroy
[root@ip-172-31-37-12 process]# kinit ferdinand
Password for ferdinand@CONG.COM: 
[root@ip-172-31-37-12 process]# beeline
Beeline version 1.1.0-cdh5.9.2 by Apache Hive
beeline> !connect jdbc:hive2://ip-172-31-37-146:10000/default;principal=hive/ip-172-31-37-146.us-west-2.compute.internal@CONG.COM
scan complete in 2ms
Connecting to jdbc:hive2://ip-172-31-37-146:10000/default;principal=hive/ip-172-31-37-146.us-west-2.compute.internal@CONG.COM
Connected to: Apache Hive (version 1.1.0-cdh5.9.2)
Driver: Hive JDBC (version 1.1.0-cdh5.9.2)
Transaction isolation: TRANSACTION_REPEATABLE_READ
0: jdbc:hive2://ip-172-31-37-146:10000/defaul> show tables;
INFO  : Compiling command(queryId=hive_20170510104848_47d965d2-af8b-4e66-b633-fb1dc7f04fbe): show tables
INFO  : Semantic Analysis Completed
INFO  : Returning Hive schema: Schema(fieldSchemas:[FieldSchema(name:tab_name, type:string, comment:from deserializer)], properties:null)
INFO  : Completed compiling command(queryId=hive_20170510104848_47d965d2-af8b-4e66-b633-fb1dc7f04fbe); Time taken: 0.093 seconds
INFO  : Executing command(queryId=hive_20170510104848_47d965d2-af8b-4e66-b633-fb1dc7f04fbe): show tables
INFO  : Starting task [Stage-0:DDL] in serial mode
INFO  : Completed executing command(queryId=hive_20170510104848_47d965d2-af8b-4e66-b633-fb1dc7f04fbe); Time taken: 0.157 seconds
INFO  : OK
+------------+--+
|  tab_name  |
+------------+--+
| sample_07  |
+------------+--+
1 row selected (0.36 seconds)
0: jdbc:hive2://ip-172-31-37-146:10000/defaul> 
```