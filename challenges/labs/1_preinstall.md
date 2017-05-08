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
#Disable transparent hugepage support

#List your network interface configuration
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

