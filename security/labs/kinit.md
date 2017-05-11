The kinit command you use to authenticate your test user  
My test user is hdfs who start NameNode  
```
cd /var/run/cloudera-scm-agent/process/390-hdfs-NAMENODE
kinit -k -t hdfs.keytab hdfs/ip-172-31-37-12.us-west-2.compute.internal@CONG.COM

klist
Ticket cache: FILE:/tmp/krb5cc_0
Default principal: hdfs/ip-172-31-37-12.us-west-2.compute.internal@CONG.COM

Valid starting     Expires            Service principal
05/10/17 08:39:43  05/11/17 08:39:43  krbtgt/CONG.COM@CONG.COM
        renew until 05/17/17 08:39:43
```