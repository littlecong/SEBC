# List the cloud provider you are using
  AWS

# List your instances by their IP address and DNS name

```
dns ec2-34-210-128-161.us-west-2.compute.amazonaws.com
internal ip 172.31.43.100

dns ec2-54-70-44-108.us-west-2.compute.amazonaws.com
internal ip 172-31-37-248

dns ec2-52-88-37-2.us-west-2.compute.amazonaws.com
internal ip 172-31-38-25

dns ec2-35-167-79-188.us-west-2.compute.amazonaws.com
internal 172-31-38-146

dns ec2-34-210-171-41.us-west-2.compute.amazonaws.com
internal 172-31-46-36

```

# List the Linux release you are using
```
[root@ip-172-31-43-100 ~]# cat /etc/redhat-release 
CentOS release 6.5 (Final)
```

# List the file system capacity for the first node
```
[root@ip-172-31-43-100 ~]# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/xvde        30G  686M   28G   3% /
tmpfs           7.4G     0  7.4G   0% /dev/shm
```

# List the command and output for yum repolist enabled
```
[root@ip-172-31-43-100 ~]# yum repolist
Loaded plugins: fastestmirror, presto
Loading mirror speeds from cached hostfile
 * base: linux.mirrors.es.net
 * extras: mirrors.sonic.net
 * updates: mirror.scalabledns.com
repo id                                                                                repo name                                                                                         status
base                                                                                   CentOS-6 - Base                                                                                   6,706
extras                                                                                 CentOS-6 - Extras                                                                                    64
updates                                                                                CentOS-6 - Updates                                                                                  270
repolist: 7,040
```