Create a precious directory in HDFS; copy the ZIP course file into it
<pre>
[hdfs@ip-172-31-37-12 ~]$ hdfs dfs -mkdir /user/hdfs/precious
[hdfs@ip-172-31-37-12 ~]$ cd /tmp
[hdfs@ip-172-31-37-12 tmp]$ hdfs dfs -put SEBC-Shanghai.zip /user/hdfs/precious
</pre>
Enable snapshots for precious
<pre>
[hdfs@ip-172-31-37-12 tmp]$ hdfs dfsadmin -allowSnapshot /user/hdfs/precious
Allowing snaphot on /user/hdfs/precious succeeded
</pre>
Create a snapshot called sebc-hdfs-test
<pre>
[hdfs@ip-172-31-37-12 tmp]$ hdfs dfs -createSnapshot /user/hdfs/precious sebc-hdfs-test
Created snapshot /user/hdfs/precious/.snapshot/sebc-hdfs-test
</pre>
Delete the directory
<pre>
[hdfs@ip-172-31-37-12 tmp]$ hdfs dfs -rm -r /user/hdfs/precious
rm: Failed to move to trash: hdfs://ip-172-31-37-146.us-west-2.compute.internal:8020/user/hdfs/precious: The directory /user/hdfs/precious cannot be deleted since /user/hdfs/precious is snapshottable and already has snapshots
</pre>
Delete the ZIP file
<pre>
[hdfs@ip-172-31-37-12 tmp]$ hdfs dfs -rm -r /user/hdfs/precious/SEBC-Shanghai.zip
17/05/09 08:21:12 INFO fs.TrashPolicyDefault: Moved: 'hdfs://ip-172-31-37-146.us-west-2.compute.internal:8020/user/hdfs/precious/SEBC-Shanghai.zip' to trash at: hdfs://ip-172-31-37-146.us-west-2.compute.internal:8020/user/hdfs/.Trash/Current/user/hdfs/precious/SEBC-Shanghai.zip
</pre>
Restore the deleted file
<pre>
[hdfs@ip-172-31-37-12 tmp]$ hdfs dfs -ls /user/hdfs/precious/.snapshot/sebc-hdfs-test
Found 1 items
-rw-r--r--   3 hdfs supergroup     474957 2017-05-09 08:13 /user/hdfs/precious/.snapshot/sebc-hdfs-test/SEBC-Shanghai.zip
[hdfs@ip-172-31-37-12 tmp]$ hdfs dfs -cp /user/hdfs/precious/.snapshot/sebc-hdfs-test/SEBC-Shanghai.zip /user/hdfs/precious/
</pre>