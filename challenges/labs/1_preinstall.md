#System Configuration Checks
##Check vm.swappiness on all your nodes
<pre>
[root@ip-172-31-37-12 ~]# sysctl vm.swappiness  
vm.swappiness = 60  
[root@ip-172-31-37-12 ~]# sysctl -w vm.swappiness=1  
vm.swappiness = 1
</pre>
##Show the mount attributes of your volume(s)
<code>
[root@ip-172-31-37-12 ~]# mount
</code>
<pre>  
/dev/xvde on / type ext4 (rw)  
proc on /proc type proc (rw)  
sysfs on /sys type sysfs (rw)  
devpts on /dev/pts type devpts (rw,gid=5,mode=620)  
tmpfs on /dev/shm type tmpfs (rw,rootcontext="system_u:object_r:tmpfs_t:s0")  
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)  
</pre>
###It is ext4 file system
<code>
[root@ip-172-31-37-12 ~]# dumpe2fs -h /dev/xvde 2> /dev/null | awk -F ':' '{ if($1 == "Reserved block count") { rescnt=$2 } } { if($1 == "Block count") { blkcnt=$2 } } END { print "Reserved blocks: "(rescnt/blkcnt)*100"%" }'
</code>
<pre>  
Reserved blocks: 4.99997%  
</pre>
<code>
[root@ip-172-31-37-12 ~]# dumpe2fs -h /dev/xvde 
</code>
<pre> 
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
</pre>
##Disable transparent hugepage support
<pre>
[root@ip-172-31-37-12 mm]# pwd
/sys/kernel/mm
[root@ip-172-31-37-12 mm]# ls
hugepages  ksm
[root@ip-172-31-37-12 mm]# grep -i HugePages_Total /proc/meminfo 
HugePages_Total:       0
</pre>
So I think the THP has been disabled
##List your network interface configuration
<code>[root@ip-172-31-37-12 hugepages-2048kB]# ifconfig
</code>
<pre>
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
</pre>
##Show that forward and reverse host lookups are correctly resolved
ip-172-31-37-12 is my Master Host, ip-172-31-40-228 is one of my Slave Hosts 
<pre>
[root@ip-172-31-37-12 yum.repos.d]# hostname
ip-172-31-37-12
[root@ip-172-31-37-12 yum.repos.d]# nslookup ip-172-31-40-228
Server:		172.31.0.2
Address:	172.31.0.2#53

Non-authoritative answer:
Name:	ip-172-31-40-228.us-west-2.compute.internal
Address: 172.31.40.228
</pre>
##Show the nscd service is running
<pre>
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
</pre>
##Show the ntpd service is running
<pre>
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
</pre>
#MySQL/MariaDB Installation Lab


