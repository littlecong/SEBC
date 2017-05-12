# Host name of my mysql server

```
[root@ip-172-31-43-100 java]# hostname -f
ip-172-31-43-100.us-west-2.compute.internal
[root@ip-172-31-43-100 java]# hostname
ip-172-31-43-100
```

# The command and output for showing the database server version
```
[root@ip-172-31-43-100 java]# mysqld --version
mysqld  Ver 5.6.36 for Linux on x86_64 (MySQL Community Server (GPL))
```

# The command and output for listing the databases created above

```
mysql> show databases;
+--------------------+
| Database           |
+--------------------+
| information_schema |
| hive               |
| hue                |
| mysql              |
| oozie              |
| performance_schema |
| rman               |
| scm                |
| sentry             |
+--------------------+
9 rows in set (0.00 sec)

mysql> 
```