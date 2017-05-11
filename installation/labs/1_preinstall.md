#System Configuration Checks
##Check vm.swappiness on all your nodes
```
[root@ip-172-31-37-12 ~]# sysctl vm.swappiness  
vm.swappiness = 60  
[root@ip-172-31-37-12 ~]# sysctl -w vm.swappiness=1  
vm.swappiness = 1
```


##Show the mount attributes of your volume(s)
```
[root@ip-172-31-37-12 ~]# mount
```
```  
/dev/xvde on / type ext4 (rw)  
proc on /proc type proc (rw)  
sysfs on /sys type sysfs (rw)  
devpts on /dev/pts type devpts (rw,gid=5,mode=620)  
tmpfs on /dev/shm type tmpfs (rw,rootcontext="system_u:object_r:tmpfs_t:s0")  
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)  
```
###It is ext4 file system
```
[root@ip-172-31-37-12 ~]# dumpe2fs -h /dev/xvde 2> /dev/null | awk -F ':' '{ if($1 == "Reserved block count") { rescnt=$2 } } { if($1 == "Block count") { blkcnt=$2 } } END { print "Reserved blocks: "(rescnt/blkcnt)*100"%" }'
```
```  
Reserved blocks: 4.99997%  
```
```
[root@ip-172-31-37-12 ~]# dumpe2fs -h /dev/xvde 
```
``` 
dumpe2fs 1.41.12 (17-May-2010)  
Filesystem volume name:   centos_root  
Last mounted on:          /  
Filesystem UUID:          44d27f92-d3df-4207-80ea-22830afccf03  
Filesystem magic number:  0xEF53  
Filesystem revision #:    1 (dynamic)  
Filesystem features:      has_journal ext_attr resize_inode dir_index filetype needs_recovery extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize  
Filesystem flags:         signed_directory_hash   
Default mount options:    (none)  
Filesystem state:         clean  
Errors behavior:          Continue  
Filesystem OS type:       Linux  
Inode count:              524288  
Block count:              2097152  
Reserved block count:     104857  
Free blocks:              1897885  
Free inodes:              509067  
First block:              0  
Block size:               4096  
Fragment size:            4096  
Reserved GDT blocks:      511  
Blocks per group:         32768  
Fragments per group:      32768  
Inodes per group:         8192  
Inode blocks per group:   512  
Flex block group size:    16  
Filesystem created:       Tue Feb  4 23:38:21 2014  
Last mount time:          Mon May  8 06:28:31 2017  
Last write time:          Tue Feb  4 23:40:03 2014  
Mount count:              3  
Maximum mount count:      -1  
Last checked:             Tue Feb  4 23:38:21 2014  
Check interval:           0 (<none>)  
Lifetime writes:          815 MB  
Reserved blocks uid:      0 (user root)  
Reserved blocks gid:      0 (group root)  
First inode:              11  
Inode size:	          256  
Required extra isize:     28  
Desired extra isize:      28  
Journal inode:            8  
Default directory hash:   half_md4  
Directory Hash Seed:      21a3ffda-3d91-4393-b173-60a625eae109  
Journal backup:           inode blocks  
Journal features:         journal_incompat_revoke  
Journal size:             128M  
Journal length:           32768  
Journal sequence:         0x00000120  
Journal start:            1  
```
##Disable transparent hugepage support
```
[root@ip-172-31-37-12 mm]# pwd
/sys/kernel/mm
[root@ip-172-31-37-12 mm]# ls
hugepages  ksm
[root@ip-172-31-37-12 mm]# grep -i HugePages_Total /proc/meminfo 
HugePages_Total:       0
```
So I think the THP has been disabled
##List your network interface configuration
```
[root@ip-172-31-37-12 hugepages-2048kB]# ifconfig
```
```
eth0      Link encap:Ethernet  HWaddr 06:FA:94:5F:04:FC  
          inet addr:172.31.37.12  Bcast:172.31.47.255  Mask:255.255.240.0
          inet6 addr: fe80::4fa:94ff:fe5f:4fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:9001  Metric:1
          RX packets:678 errors:0 dropped:0 overruns:0 frame:0
          TX packets:653 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:59200 (57.8 KiB)  TX bytes:83220 (81.2 KiB)
          Interrupt:24 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
```
##Show that forward and reverse host lookups are correctly resolved
ip-172-31-37-12 is my Master Host, ip-172-31-40-228 is one of my Slave Hosts 
```
[root@ip-172-31-37-12 yum.repos.d]# hostname
ip-172-31-37-12
[root@ip-172-31-37-12 yum.repos.d]# nslookup ip-172-31-40-228
Server:		172.31.0.2
Address:	172.31.0.2#53

Non-authoritative answer:
Name:	ip-172-31-40-228.us-west-2.compute.internal
Address: 172.31.40.228
```
##Show the nscd service is running
```
[root@ip-172-31-37-12 etc]# service nscd status
nscd: unrecognized service
[root@ip-172-31-37-12 etc]# yum install nscd
Loaded plugins: fastestmirror, presto
Loading mirror speeds from cached hostfile
 * base: mirrors.cat.pdx.edu
 * extras: mirrors.sonic.net
 * updates: mirror.sjc02.svwh.net
Setting up Install Process
Resolving Dependencies
--> Running transaction check
---> Package nscd.x86_64 0:2.12-1.209.el6_9.1 will be installed
--> Processing Dependency: glibc = 2.12-1.209.el6_9.1 for package: nscd-2.12-1.209.el6_9.1.x86_64
--> Running transaction check
---> Package glibc.x86_64 0:2.12-1.132.el6 will be updated
--> Processing Dependency: glibc = 2.12-1.132.el6 for package: glibc-common-2.12-1.132.el6.x86_64
---> Package glibc.x86_64 0:2.12-1.209.el6_9.1 will be an update
--> Running transaction check
---> Package glibc-common.x86_64 0:2.12-1.132.el6 will be updated
---> Package glibc-common.x86_64 0:2.12-1.209.el6_9.1 will be an update
--> Processing Dependency: tzdata >= 2015g-4 for package: glibc-common-2.12-1.209.el6_9.1.x86_64
--> Running transaction check
---> Package tzdata.noarch 0:2013g-1.el6 will be updated
---> Package tzdata.noarch 0:2017b-1.el6 will be an update
--> Finished Dependency Resolution

Dependencies Resolved

===============================================================================================================================================================================================
 Package                                        Arch                                     Version                                               Repository                                 Size
===============================================================================================================================================================================================
Installing:
 nscd                                           x86_64                                   2.12-1.209.el6_9.1                                    updates                                   232 k
Updating for dependencies:
 glibc                                          x86_64                                   2.12-1.209.el6_9.1                                    updates                                   3.8 M
 glibc-common                                   x86_64                                   2.12-1.209.el6_9.1                                    updates                                    14 M
 tzdata                                         noarch                                   2017b-1.el6                                           updates                                   455 k

Transaction Summary
===============================================================================================================================================================================================
Install       1 Package(s)
Upgrade       3 Package(s)

Total download size: 19 M
Is this ok [y/N]: y
Downloading Packages:
Setting up and reading Presto delta metadata
Processing delta metadata
Package(s) data still to download: 19 M
(1/4): glibc-2.12-1.209.el6_9.1.x86_64.rpm                                                                                                                              | 3.8 MB     00:00     
(2/4): glibc-common-2.12-1.209.el6_9.1.x86_64.rpm                                                                                                                       |  14 MB     00:00     
(3/4): nscd-2.12-1.209.el6_9.1.x86_64.rpm                                                                                                                               | 232 kB     00:00     
(4/4): tzdata-2017b-1.el6.noarch.rpm                                                                                                                                    | 455 kB     00:00     
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                                                           22 MB/s |  19 MB     00:00     
Running rpm_check_debug
Running Transaction Test
Transaction Test Succeeded
Running Transaction
  Updating   : tzdata-2017b-1.el6.noarch                                                                                                                                                   1/7 
  Updating   : glibc-2.12-1.209.el6_9.1.x86_64                                                                                                                                             2/7 
  Updating   : glibc-common-2.12-1.209.el6_9.1.x86_64                                                                                                                                      3/7 
  Installing : nscd-2.12-1.209.el6_9.1.x86_64                                                                                                                                              4/7 
  Cleanup    : glibc-common-2.12-1.132.el6.x86_64                                                                                                                                          5/7 
  Cleanup    : glibc-2.12-1.132.el6.x86_64                                                                                                                                                 6/7 
  Cleanup    : tzdata-2013g-1.el6.noarch                                                                                                                                                   7/7 
  Verifying  : tzdata-2017b-1.el6.noarch                                                                                                                                                   1/7 
  Verifying  : nscd-2.12-1.209.el6_9.1.x86_64                                                                                                                                              2/7 
  Verifying  : glibc-2.12-1.209.el6_9.1.x86_64                                                                                                                                             3/7 
  Verifying  : glibc-common-2.12-1.209.el6_9.1.x86_64                                                                                                                                      4/7 
  Verifying  : glibc-2.12-1.132.el6.x86_64                                                                                                                                                 5/7 
  Verifying  : tzdata-2013g-1.el6.noarch                                                                                                                                                   6/7 
  Verifying  : glibc-common-2.12-1.132.el6.x86_64                                                                                                                                          7/7 

Installed:
  nscd.x86_64 0:2.12-1.209.el6_9.1                                                                                                                                                             

Dependency Updated:
  glibc.x86_64 0:2.12-1.209.el6_9.1                              glibc-common.x86_64 0:2.12-1.209.el6_9.1                              tzdata.noarch 0:2017b-1.el6                             

Complete!
[root@ip-172-31-37-12 etc]# chkconfig nscd on
[root@ip-172-31-37-12 etc]# service nscd start
Starting nscd:                                             [  OK  ]
```
##Show the ntpd service is running
```
[root@ip-172-31-37-12 etc]# service ntpd status
ntpd: unrecognized service
[root@ip-172-31-37-12 etc]# yum install ntp ntpdate
Loaded plugins: fastestmirror, presto
Loading mirror speeds from cached hostfile
 * base: mirrors.cat.pdx.edu
 * extras: mirrors.sonic.net
 * updates: mirror.sjc02.svwh.net
Setting up Install Process
Resolving Dependencies
--> Running transaction check
---> Package ntp.x86_64 0:4.2.6p5-10.el6.centos.2 will be installed
---> Package ntpdate.x86_64 0:4.2.6p5-10.el6.centos.2 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

===============================================================================================================================================================================================
 Package                                    Arch                                      Version                                                    Repository                               Size
===============================================================================================================================================================================================
Installing:
 ntp                                        x86_64                                    4.2.6p5-10.el6.centos.2                                    base                                    599 k
 ntpdate                                    x86_64                                    4.2.6p5-10.el6.centos.2                                    base                                     78 k

Transaction Summary
===============================================================================================================================================================================================
Install       2 Package(s)

Total download size: 678 k
Installed size: 1.8 M
Is this ok [y/N]: y
Downloading Packages:
Setting up and reading Presto delta metadata
Processing delta metadata
Package(s) data still to download: 678 k
(1/2): ntp-4.2.6p5-10.el6.centos.2.x86_64.rpm                                                                                                                           | 599 kB     00:00     
(2/2): ntpdate-4.2.6p5-10.el6.centos.2.x86_64.rpm                                                                                                                       |  78 kB     00:00     
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                                                          5.2 MB/s | 678 kB     00:00     
Running rpm_check_debug
Running Transaction Test
Transaction Test Succeeded
Running Transaction
  Installing : ntpdate-4.2.6p5-10.el6.centos.2.x86_64                                                                                                                                      1/2 
  Installing : ntp-4.2.6p5-10.el6.centos.2.x86_64                                                                                                                                          2/2 
  Verifying  : ntp-4.2.6p5-10.el6.centos.2.x86_64                                                                                                                                          1/2 
  Verifying  : ntpdate-4.2.6p5-10.el6.centos.2.x86_64                                                                                                                                      2/2 

Installed:
  ntp.x86_64 0:4.2.6p5-10.el6.centos.2                                                         ntpdate.x86_64 0:4.2.6p5-10.el6.centos.2                                                        

Complete!
[root@ip-172-31-37-12 etc]# chkconfig ntpd on
[root@ip-172-31-37-12 etc]# service ntpd start
Starting ntpd:                                             [  OK  ]
```
#MySQL/MariaDB Installation Lab
##Download and implement the official MySQL repo
###Enable the repo to install MySQL 5.5
```
[root@ip-172-31-37-12 yum.repos.d]# yum repolist
Loaded plugins: fastestmirror, presto
Loading mirror speeds from cached hostfile
 * base: mirrors.cat.pdx.edu
 * extras: mirrors.sonic.net
 * updates: mirror.sjc02.svwh.net
mysql-connectors-community                                                                                                                                              | 2.5 kB     00:00     
mysql-tools-community                                                                                                                                                   | 2.5 kB     00:00     
mysql55-community                                                                                                                                                       | 2.5 kB     00:00     
repo id                                                                                     repo name                                                                                    status
base                                                                                        CentOS-6 - Base                                                                              6,706
extras                                                                                      CentOS-6 - Extras                                                                               64
mysql-connectors-community                                                                  MySQL Connectors Community                                                                      36
mysql-tools-community                                                                       MySQL Tools Community                                                                           47
mysql55-community                                                                           MySQL 5.5 Community Server                                                                     373
updates                                                                                     CentOS-6 - Updates                                                                             252
repolist: 7,478
```
###Install the mysql package on all nodes
```
[root@ip-172-31-37-12 yum.repos.d]# yum install mysql
Loaded plugins: fastestmirror, presto
Loading mirror speeds from cached hostfile
 * base: mirrors.cat.pdx.edu
 * extras: mirrors.sonic.net
 * updates: mirror.sjc02.svwh.net
Setting up Install Process
Package mysql is obsoleted by mysql-community-client, trying to install mysql-community-client-5.5.56-2.el6.x86_64 instead
Resolving Dependencies
--> Running transaction check
---> Package mysql.x86_64 0:5.1.73-8.el6_8 will be obsoleted
---> Package mysql-community-client.x86_64 0:5.5.56-2.el6 will be obsoleting
--> Processing Dependency: mysql-community-libs(x86-64) >= 5.5.8 for package: mysql-community-client-5.5.56-2.el6.x86_64
--> Running transaction check
---> Package mysql-community-libs.x86_64 0:5.5.56-2.el6 will be obsoleting
--> Processing Dependency: mysql-community-common(x86-64) >= 5.5.8 for package: mysql-community-libs-5.5.56-2.el6.x86_64
---> Package mysql-libs.x86_64 0:5.1.73-8.el6_8 will be obsoleted
--> Processing Dependency: libmysqlclient.so.16()(64bit) for package: 2:postfix-2.6.6-2.2.el6_1.x86_64
--> Processing Dependency: libmysqlclient.so.16()(64bit) for package: perl-DBD-MySQL-4.013-3.el6.x86_64
--> Processing Dependency: libmysqlclient.so.16(libmysqlclient_16)(64bit) for package: 2:postfix-2.6.6-2.2.el6_1.x86_64
--> Processing Dependency: libmysqlclient.so.16(libmysqlclient_16)(64bit) for package: perl-DBD-MySQL-4.013-3.el6.x86_64
--> Running transaction check
---> Package mysql-community-common.x86_64 0:5.5.56-2.el6 will be installed
---> Package mysql-community-libs-compat.x86_64 0:5.5.56-2.el6 will be obsoleting
---> Package postfix.x86_64 2:2.6.6-2.2.el6_1 will be updated
---> Package postfix.x86_64 2:2.6.6-8.el6 will be an update
--> Finished Dependency Resolution

Dependencies Resolved

===============================================================================================================================================================================================
 Package                                                  Arch                                Version                                     Repository                                      Size
===============================================================================================================================================================================================
Installing:
 mysql-community-client                                   x86_64                              5.5.56-2.el6                                mysql55-community                               15 M
     replacing  mysql.x86_64 5.1.73-8.el6_8
 mysql-community-libs                                     x86_64                              5.5.56-2.el6                                mysql55-community                              1.7 M
     replacing  mysql-libs.x86_64 5.1.73-8.el6_8
 mysql-community-libs-compat                              x86_64                              5.5.56-2.el6                                mysql55-community                              1.6 M
     replacing  mysql-libs.x86_64 5.1.73-8.el6_8
Installing for dependencies:
 mysql-community-common                                   x86_64                              5.5.56-2.el6                                mysql55-community                              277 k
Updating for dependencies:
 postfix                                                  x86_64                              2:2.6.6-8.el6                               base                                           2.0 M

Transaction Summary
===============================================================================================================================================================================================
Install       4 Package(s)
Upgrade       1 Package(s)

Total download size: 20 M
Is this ok [y/N]: y
Downloading Packages:
Setting up and reading Presto delta metadata
Processing delta metadata
Package(s) data still to download: 20 M
(1/5): mysql-community-client-5.5.56-2.el6.x86_64.rpm                                                                                                                   |  15 MB     00:00     
(2/5): mysql-community-common-5.5.56-2.el6.x86_64.rpm                                                                                                                   | 277 kB     00:00     
(3/5): mysql-community-libs-5.5.56-2.el6.x86_64.rpm                                                                                                                     | 1.7 MB     00:00     
(4/5): mysql-community-libs-compat-5.5.56-2.el6.x86_64.rpm                                                                                                              | 1.6 MB     00:00     
(5/5): postfix-2.6.6-8.el6.x86_64.rpm                                                                                                                                   | 2.0 MB     00:00     
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                                                           33 MB/s |  20 MB     00:00     
warning: rpmts_HdrFromFdno: Header V3 DSA/SHA1 Signature, key ID 5072e1f5: NOKEY
Retrieving key from file:///etc/pki/rpm-gpg/RPM-GPG-KEY-mysql
Importing GPG key 0x5072E1F5:
 Userid : MySQL Release Engineering <mysql-build@oss.oracle.com>
 Package: mysql57-community-release-el6-11.noarch (@/mysql57-community-release-el6-11.noarch)
 From   : /etc/pki/rpm-gpg/RPM-GPG-KEY-mysql
Is this ok [y/N]: y
Running rpm_check_debug
Running Transaction Test
Transaction Test Succeeded
Running Transaction
  Installing : mysql-community-common-5.5.56-2.el6.x86_64                                                                                                                                  1/8 
  Installing : mysql-community-libs-5.5.56-2.el6.x86_64                                                                                                                                    2/8 
  Installing : mysql-community-libs-compat-5.5.56-2.el6.x86_64                                                                                                                             3/8 
  Updating   : 2:postfix-2.6.6-8.el6.x86_64                                                                                                                                                4/8 
  Installing : mysql-community-client-5.5.56-2.el6.x86_64                                                                                                                                  5/8 
  Cleanup    : 2:postfix-2.6.6-2.2.el6_1.x86_64                                                                                                                                            6/8 
  Erasing    : mysql-5.1.73-8.el6_8.x86_64                                                                                                                                                 7/8 
  Erasing    : mysql-libs-5.1.73-8.el6_8.x86_64                                                                                                                                            8/8 
  Verifying  : mysql-community-libs-5.5.56-2.el6.x86_64                                                                                                                                    1/8 
  Verifying  : mysql-community-client-5.5.56-2.el6.x86_64                                                                                                                                  2/8 
  Verifying  : mysql-community-libs-compat-5.5.56-2.el6.x86_64                                                                                                                             3/8 
  Verifying  : 2:postfix-2.6.6-8.el6.x86_64                                                                                                                                                4/8 
  Verifying  : mysql-community-common-5.5.56-2.el6.x86_64                                                                                                                                  5/8 
  Verifying  : 2:postfix-2.6.6-2.2.el6_1.x86_64                                                                                                                                            6/8 
  Verifying  : mysql-5.1.73-8.el6_8.x86_64                                                                                                                                                 7/8 
  Verifying  : mysql-libs-5.1.73-8.el6_8.x86_64                                                                                                                                            8/8 

Installed:
  mysql-community-client.x86_64 0:5.5.56-2.el6                  mysql-community-libs.x86_64 0:5.5.56-2.el6                  mysql-community-libs-compat.x86_64 0:5.5.56-2.el6                 

Dependency Installed:
  mysql-community-common.x86_64 0:5.5.56-2.el6                                                                                                                                                 

Dependency Updated:
  postfix.x86_64 2:2.6.6-8.el6                                                                                                                                                                 

Replaced:
  mysql.x86_64 0:5.1.73-8.el6_8                                                               mysql-libs.x86_64 0:5.1.73-8.el6_8                                                              

Complete!
```
###Install mysql-server on the my Master host(ip-172-31-37-12) and Slave1 host(ip-172-31-40-228)
```
[root@ip-172-31-40-228 yum.repos.d]# yum intall mysql-server
Loaded plugins: fastestmirror, presto
No such command: intall. Please use /usr/bin/yum --help
[root@ip-172-31-40-228 yum.repos.d]# yum install mysql-server
Loaded plugins: fastestmirror, presto
Loading mirror speeds from cached hostfile
 * base: mirrors.cat.pdx.edu
 * extras: centos-distro.cavecreek.net
 * updates: mirror.sjc02.svwh.net
Setting up Install Process
Package mysql-server is obsoleted by mysql-community-server, trying to install mysql-community-server-5.5.56-2.el6.x86_64 instead
Resolving Dependencies
--> Running transaction check
---> Package mysql-community-server.x86_64 0:5.5.56-2.el6 will be installed
--> Processing Dependency: perl(DBI) for package: mysql-community-server-5.5.56-2.el6.x86_64
--> Processing Dependency: libaio.so.1(LIBAIO_0.4)(64bit) for package: mysql-community-server-5.5.56-2.el6.x86_64
--> Processing Dependency: libaio.so.1(LIBAIO_0.1)(64bit) for package: mysql-community-server-5.5.56-2.el6.x86_64
--> Processing Dependency: libaio.so.1()(64bit) for package: mysql-community-server-5.5.56-2.el6.x86_64
--> Running transaction check
---> Package libaio.x86_64 0:0.3.107-10.el6 will be installed
---> Package perl-DBI.x86_64 0:1.609-4.el6 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

===============================================================================================================================================================================================
 Package                                              Arch                                 Version                                       Repository                                       Size
===============================================================================================================================================================================================
Installing:
 mysql-community-server                               x86_64                               5.5.56-2.el6                                  mysql55-community                                38 M
Installing for dependencies:
 libaio                                               x86_64                               0.3.107-10.el6                                base                                             21 k
 perl-DBI                                             x86_64                               1.609-4.el6                                   base                                            705 k

Transaction Summary
===============================================================================================================================================================================================
Install       3 Package(s)

Total download size: 39 M
Installed size: 167 M
Is this ok [y/N]: y
Downloading Packages:
Setting up and reading Presto delta metadata
Processing delta metadata
Package(s) data still to download: 39 M
(1/3): libaio-0.3.107-10.el6.x86_64.rpm                                                                                                                                 |  21 kB     00:00     
(2/3): mysql-community-server-5.5.56-2.el6.x86_64.rpm                                                                                                                   |  38 MB     00:00     
(3/3): perl-DBI-1.609-4.el6.x86_64.rpm                                                                                                                                  | 705 kB     00:00     
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                                                                           48 MB/s |  39 MB     00:00     
Running rpm_check_debug
Running Transaction Test
Transaction Test Succeeded
Running Transaction
  Installing : perl-DBI-1.609-4.el6.x86_64                                                                                                                                                 1/3 
  Installing : libaio-0.3.107-10.el6.x86_64                                                                                                                                                2/3 
  Installing : mysql-community-server-5.5.56-2.el6.x86_64                                                                                                                                  3/3 
  Verifying  : libaio-0.3.107-10.el6.x86_64                                                                                                                                                1/3 
  Verifying  : mysql-community-server-5.5.56-2.el6.x86_64                                                                                                                                  2/3 
  Verifying  : perl-DBI-1.609-4.el6.x86_64                                                                                                                                                 3/3 

Installed:
  mysql-community-server.x86_64 0:5.5.56-2.el6                                                                                                                                                 

Dependency Installed:
  libaio.x86_64 0:0.3.107-10.el6                                                                 perl-DBI.x86_64 0:1.609-4.el6                                                                

Complete!
</pre>
###Download and copy the JDBC connector to all nodes.
Upload mysql-connector-java-5.1.42.tar.gz to the cluster and expand it.
<pre>
[root@ip-172-31-37-12 mysql-connector-java-5.1.42]# pwd
/opt/mysql-connector-java-5.1.42
[root@ip-172-31-37-12 mysql-connector-java-5.1.42]# ls
build.xml  CHANGES  COPYING  docs  mysql-connector-java-5.1.42-bin.jar  README  README.txt  src
[root@ip-172-31-37-12 mysql-connector-java-5.1.42]# 
```
##Modified /etc/my.cnf on Master and Slave
Master
```
log_bin=mysql-bin
server-id=1
```
Slave
```
server-id=2
```
##Start the mysqld service.
```
[root@ip-172-31-37-12 ~]# service mysqld start
Starting mysqld:                                           [  OK  ]
```
##Use /usr/bin/mysql_secure_installation secure mysql
```
[root@ip-172-31-37-12 log]# /usr/bin/mysql_secure_installation




NOTE: RUNNING ALL PARTS OF THIS SCRIPT IS RECOMMENDED FOR ALL MySQL
      SERVERS IN PRODUCTION USE!  PLEASE READ EACH STEP CAREFULLY!


In order to log into MySQL to secure it, we'll need the current
password for the root user.  If you've just installed MySQL, and
you haven't set the root password yet, the password will be blank,
so you should just press enter here.

Enter current password for root (enter for none): 
OK, successfully used password, moving on...

Setting the root password ensures that nobody can log into the MySQL
root user without the proper authorisation.

Set root password? [Y/n] Y
New password: 
Re-enter new password: 
Password updated successfully!
Reloading privilege tables..
 ... Success!


By default, a MySQL installation has an anonymous user, allowing anyone
to log into MySQL without having to have a user account created for
them.  This is intended only for testing, and to make the installation
go a bit smoother.  You should remove them before moving into a
production environment.

Remove anonymous users? [Y/n] Y
 ... Success!

Normally, root should only be allowed to connect from 'localhost'.  This
ensures that someone cannot guess at the root password from the network.

Disallow root login remotely? [Y/n] n
 ... skipping.

By default, MySQL comes with a database named 'test' that anyone can
access.  This is also intended only for testing, and should be removed
before moving into a production environment.

Remove test database and access to it? [Y/n] Y
 - Dropping test database...
 ... Success!
 - Removing privileges on test database...
 ... Success!

Reloading the privilege tables will ensure that all changes made so far
will take effect immediately.

Reload privilege tables now? [Y/n] Y
 ... Success!

Cleaning up...



All done!  If you've completed all of the above steps, your MySQL
installation should now be secure.

Thanks for using MySQL!
[root@ip-172-31-37-12 log]# service mysqld restart
Stopping mysqld:                                           [  OK  ]
Starting mysqld:                                           [  OK  ]
```
##On the master MySQL node, grant replication privileges for your replica node:
```
[root@ip-172-31-37-12 log]# mysql -uroot -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 3
Server version: 5.5.56 MySQL Community Server (GPL)

Copyright (c) 2000, 2017, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> GRANT REPLICATION SLAVE ON *.* TO 'root'@'ip-172-31-37-12.us-west-2.compute.internal' IDENTIFIED BY 'password';
Query OK, 0 rows affected (0.00 sec)

mysql> SET GLOBAL binlog_format = 'ROW';
Query OK, 0 rows affected (0.00 sec)

mysql> FLUSH TABLES WITH READ LOCK;
Query OK, 0 rows affected (0.00 sec)

mysql> 
```
##In a second terminal session, log into the MySQL master and show its status:
```
[root@ip-172-31-37-12 ~]# mysql -uroot -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 4
Server version: 5.5.56-log MySQL Community Server (GPL)

Copyright (c) 2000, 2017, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> SHOW MASTER STATUS;
+------------------+----------+--------------+------------------+
| File             | Position | Binlog_Do_DB | Binlog_Ignore_DB |
+------------------+----------+--------------+------------------+
| mysql-bin.000001 |      107 |              |                  |
+------------------+----------+--------------+------------------+
1 row in set (0.00 sec)

mysql> exit;
Bye
```
Logout of the second session; remove the lock on the first
```
mysql> UNLOCK TABLES
    -> ;
Query OK, 0 rows affected (0.00 sec)
```
##Login to the replica server(My Slave1) and configure a connection to the master
```
[root@ip-172-31-40-228 yum.repos.d]# mysql -uroot -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 2
Server version: 5.5.56 MySQL Community Server (GPL)

Copyright (c) 2000, 2017, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> CHANGE MASTER TO MASTER_HOST='ip-172-31-37-12.us-west-2.compute.internal', MASTER_USER='root', MASTER_PASSWORD='password', MASTER_LOG_FILE='mysql-bin.000001', MASTER_LOG_POS=107;
Query OK, 0 rows affected (0.07 sec)

mysql> 
```
##Initiate slave operations on the replica
close SELinux on all nodes
```
setenforce 0
```

```
mysql> SHOW SLAVE STATUS \G
*************************** 1. row ***************************
               Slave_IO_State: Waiting for master to send event
                  Master_Host: ip-172-31-37-12.us-west-2.compute.internal
                  Master_User: root
                  Master_Port: 3306
                Connect_Retry: 60
              Master_Log_File: mysql-bin.000001
          Read_Master_Log_Pos: 455
               Relay_Log_File: mysqld-relay-bin.000002
                Relay_Log_Pos: 601
        Relay_Master_Log_File: mysql-bin.000001
             Slave_IO_Running: Yes
            Slave_SQL_Running: Yes
              Replicate_Do_DB: 
          Replicate_Ignore_DB: 
           Replicate_Do_Table: 
       Replicate_Ignore_Table: 
      Replicate_Wild_Do_Table: 
  Replicate_Wild_Ignore_Table: 
                   Last_Errno: 0
                   Last_Error: 
                 Skip_Counter: 0
          Exec_Master_Log_Pos: 455
              Relay_Log_Space: 758
              Until_Condition: None
               Until_Log_File: 
                Until_Log_Pos: 0
           Master_SSL_Allowed: No
           Master_SSL_CA_File: 
           Master_SSL_CA_Path: 
              Master_SSL_Cert: 
            Master_SSL_Cipher: 
               Master_SSL_Key: 
        Seconds_Behind_Master: 0
Master_SSL_Verify_Server_Cert: No
                Last_IO_Errno: 0
                Last_IO_Error: 
               Last_SQL_Errno: 0
               Last_SQL_Error: 
  Replicate_Ignore_Server_Ids: 
             Master_Server_Id: 1
1 row in set (0.00 sec)
```