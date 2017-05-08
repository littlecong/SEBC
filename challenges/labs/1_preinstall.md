#System Configuration Checks
##Check vm.swappiness on all your nodes
<code>
[root@ip-172-31-37-12 ~]# sysctl vm.swappiness  
vm.swappiness = 60  
[root@ip-172-31-37-12 ~]# sysctl -w vm.swappiness=1  
vm.swappiness = 1
</code>
##Show the mount attributes of your volume(s)
<code>
[root@ip-172-31-37-12 ~]# mount  
/dev/xvde on / type ext4 (rw)  
proc on /proc type proc (rw)  
sysfs on /sys type sysfs (rw)  
devpts on /dev/pts type devpts (rw,gid=5,mode=620)  
tmpfs on /dev/shm type tmpfs (rw,rootcontext="system_u:object_r:tmpfs_t:s0")  
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)  
</code>

