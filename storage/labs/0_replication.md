1. HDFS Lab: Replicate to another cluster
When I distcp between my own cluster, it works
<pre>
[hdfs@ip-172-31-37-146 jars]$ hadoop distcp hdfs://ip-172-31-37-146.us-west-2.compute.internal/user/littlecong/teragen hdfs://ec2-35-161-179-128.us-west-2.compute.amazonaws.com/littlecong/copyfromgeragen
17/05/09 05:26:50 INFO tools.DistCp: Input Options: DistCpOptions{atomicCommit=false, syncFolder=false, deleteMissing=false, ignoreFailures=false, overwrite=false, append=false, useDiff=false, useRdiff=false, fromSnapshot=null, toSnapshot=null, skipCRC=false, blocking=true, numListstatusThreads=0, maxMaps=20, mapBandwidth=100, sslConfigurationFile='null', copyStrategy='uniformsize', preserveStatus=[], preserveRawXattrs=false, atomicWorkPath=null, logPath=null, sourceFileListing=null, sourcePaths=[hdfs://ip-172-31-37-146.us-west-2.compute.internal/user/littlecong/teragen], targetPath=hdfs://ec2-35-161-179-128.us-west-2.compute.amazonaws.com/littlecong/copyfromgeragen, targetPathExists=false, filtersFile='null'}
17/05/09 05:26:50 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-37-146.us-west-2.compute.internal/172.31.37.146:8032
17/05/09 05:26:50 INFO tools.SimpleCopyListing: Paths (files+dirs) cnt = 4; dirCnt = 1
17/05/09 05:26:50 INFO tools.SimpleCopyListing: Build file listing completed.
17/05/09 05:26:50 INFO Configuration.deprecation: io.sort.mb is deprecated. Instead, use mapreduce.task.io.sort.mb
17/05/09 05:26:50 INFO Configuration.deprecation: io.sort.factor is deprecated. Instead, use mapreduce.task.io.sort.factor
17/05/09 05:26:50 INFO tools.DistCp: Number of paths in the copy list: 4
17/05/09 05:26:50 INFO tools.DistCp: Number of paths in the copy list: 4
17/05/09 05:26:51 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-37-146.us-west-2.compute.internal/172.31.37.146:8032
17/05/09 05:26:51 INFO mapreduce.JobSubmitter: number of splits:3
17/05/09 05:26:51 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1494301647320_0005
17/05/09 05:26:51 INFO impl.YarnClientImpl: Submitted application application_1494301647320_0005
17/05/09 05:26:51 INFO mapreduce.Job: The url to track the job: http://ip-172-31-37-146.us-west-2.compute.internal:8088/proxy/application_1494301647320_0005/
17/05/09 05:26:51 INFO tools.DistCp: DistCp job-id: job_1494301647320_0005
17/05/09 05:26:51 INFO mapreduce.Job: Running job: job_1494301647320_0005
17/05/09 05:26:59 INFO mapreduce.Job: Job job_1494301647320_0005 running in uber mode : false
17/05/09 05:26:59 INFO mapreduce.Job:  map 0% reduce 0%
17/05/09 05:27:07 INFO mapreduce.Job:  map 33% reduce 0%
17/05/09 05:27:08 INFO mapreduce.Job:  map 67% reduce 0%
17/05/09 05:27:10 INFO mapreduce.Job:  map 100% reduce 0%
17/05/09 05:27:11 INFO mapreduce.Job: Job job_1494301647320_0005 completed successfully
17/05/09 05:27:11 INFO mapreduce.Job: Counters: 33
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=379746
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=524289768
		HDFS: Number of bytes written=524288000
		HDFS: Number of read operations=56
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=13
	Job Counters 
		Launched map tasks=3
		Other local map tasks=3
		Total time spent by all maps in occupied slots (ms)=23093
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=23093
		Total vcore-seconds taken by all map tasks=23093
		Total megabyte-seconds taken by all map tasks=23647232
	Map-Reduce Framework
		Map input records=4
		Map output records=0
		Input split bytes=342
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=238
		CPU time spent (ms)=12550
		Physical memory (bytes) snapshot=677814272
		Virtual memory (bytes) snapshot=4735336448
		Total committed heap usage (bytes)=1081606144
	File Input Format Counters 
		Bytes Read=1426
	File Output Format Counters 
		Bytes Written=0
	org.apache.hadoop.tools.mapred.CopyMapper$Counter
		BYTESCOPIED=524288000
		BYTESEXPECTED=524288000
		COPY=4
[hdfs@ip-172-31-37-146 jars]$ hdfs fsck /user/littlecong/teragen -files -blocks
Connecting to namenode via http://ip-172-31-37-146.us-west-2.compute.internal:50070
FSCK started by hdfs (auth:SIMPLE) from /172.31.37.146 for path /user/littlecong/teragen at Tue May 09 05:30:16 UTC 2017
/user/littlecong/teragen <dir>
/user/littlecong/teragen/_SUCCESS 0 bytes, 0 block(s):  OK

/user/littlecong/teragen/part-m-00000 262144000 bytes, 2 block(s):  OK
0. BP-1153443846-172.31.37.146-1494243204689:blk_1073744262_3438 len=134217728 Live_repl=3
1. BP-1153443846-172.31.37.146-1494243204689:blk_1073744265_3441 len=127926272 Live_repl=3

/user/littlecong/teragen/part-m-00001 262144000 bytes, 2 block(s):  OK
0. BP-1153443846-172.31.37.146-1494243204689:blk_1073744263_3439 len=134217728 Live_repl=3
1. BP-1153443846-172.31.37.146-1494243204689:blk_1073744264_3440 len=127926272 Live_repl=3

Status: HEALTHY
 Total size:	524288000 B
 Total dirs:	1
 Total files:	3
 Total symlinks:		0
 Total blocks (validated):	4 (avg. block size 131072000 B)
 Minimally replicated blocks:	4 (100.0 %)
 Over-replicated blocks:	0 (0.0 %)
 Under-replicated blocks:	0 (0.0 %)
 Mis-replicated blocks:		0 (0.0 %)
 Default replication factor:	3
 Average block replication:	3.0
 Corrupt blocks:		0
 Missing replicas:		0 (0.0 %)
 Number of data-nodes:		3
 Number of racks:		1
FSCK ended at Tue May 09 05:30:16 UTC 2017 in 3 milliseconds


The filesystem under path '/user/littlecong/teragen' is HEALTHY
[hdfs@ip-172-31-37-146 jars]$ netstat -an |grep 14000
[hdfs@ip-172-31-37-146 jars]$ hdfs fsck /user/littlecong/teragen -files -blocks
Connecting to namenode via http://ip-172-31-37-146.us-west-2.compute.internal:50070
FSCK started by hdfs (auth:SIMPLE) from /172.31.37.146 for path /user/littlecong/teragen at Tue May 09 06:55:41 UTC 2017
/user/littlecong/teragen <dir>
/user/littlecong/teragen/_SUCCESS 0 bytes, 0 block(s):  OK

/user/littlecong/teragen/part-m-00000 262144000 bytes, 2 block(s):  OK
0. BP-1153443846-172.31.37.146-1494243204689:blk_1073744262_3438 len=134217728 Live_repl=3
1. BP-1153443846-172.31.37.146-1494243204689:blk_1073744265_3441 len=127926272 Live_repl=3

/user/littlecong/teragen/part-m-00001 262144000 bytes, 2 block(s):  OK
0. BP-1153443846-172.31.37.146-1494243204689:blk_1073744263_3439 len=134217728 Live_repl=3
1. BP-1153443846-172.31.37.146-1494243204689:blk_1073744264_3440 len=127926272 Live_repl=3

Status: HEALTHY
 Total size:	524288000 B
 Total dirs:	1
 Total files:	3
 Total symlinks:		0
 Total blocks (validated):	4 (avg. block size 131072000 B)
 Minimally replicated blocks:	4 (100.0 %)
 Over-replicated blocks:	0 (0.0 %)
 Under-replicated blocks:	0 (0.0 %)
 Mis-replicated blocks:		0 (0.0 %)
 Default replication factor:	3
 Average block replication:	3.0
 Corrupt blocks:		0
 Missing replicas:		0 (0.0 %)
 Number of data-nodes:		3
 Number of racks:		1
FSCK ended at Tue May 09 06:55:41 UTC 2017 in 2 milliseconds


The filesystem under path '/user/littlecong/teragen' is HEALTHY
[hdfs@ip-172-31-37-146 jars]$ hdfs fsck /littlecong/copyfromteragen -files -blocks
Connecting to namenode via http://ip-172-31-37-146.us-west-2.compute.internal:50070
FSCK started by hdfs (auth:SIMPLE) from /172.31.37.146 for path /littlecong/copyfromteragen at Tue May 09 06:57:29 UTC 2017
/littlecong/copyfromteragen <dir>
/littlecong/copyfromteragen/_SUCCESS 0 bytes, 0 block(s):  OK

/littlecong/copyfromteragen/part-m-00000 262144000 bytes, 2 block(s):  OK
0. BP-1153443846-172.31.37.146-1494243204689:blk_1073744300_3476 len=134217728 Live_repl=3
1. BP-1153443846-172.31.37.146-1494243204689:blk_1073744302_3478 len=127926272 Live_repl=3

/littlecong/copyfromteragen/part-m-00001 262144000 bytes, 2 block(s):  OK
0. BP-1153443846-172.31.37.146-1494243204689:blk_1073744298_3474 len=134217728 Live_repl=3
1. BP-1153443846-172.31.37.146-1494243204689:blk_1073744299_3475 len=127926272 Live_repl=3

Status: HEALTHY
 Total size:	524288000 B
 Total dirs:	1
 Total files:	3
 Total symlinks:		0
 Total blocks (validated):	4 (avg. block size 131072000 B)
 Minimally replicated blocks:	4 (100.0 %)
 Over-replicated blocks:	0 (0.0 %)
 Under-replicated blocks:	0 (0.0 %)
 Mis-replicated blocks:		0 (0.0 %)
 Default replication factor:	3
 Average block replication:	3.0
 Corrupt blocks:		0
 Missing replicas:		0 (0.0 %)
 Number of data-nodes:		3
 Number of racks:		1
FSCK ended at Tue May 09 06:57:29 UTC 2017 in 2 milliseconds


The filesystem under path '/littlecong/copyfromteragen' is HEALTHY
</pre>
When I distcp from my own cluster to my partner's cluster it fails. Perhaps it is something about network issue 
<pre>
hadoop distcp hdfs://ip-172-31-37-146.us-west-2.compute.internal/user/littlecong/teragen hdfs://ec2-54-193-126-200.us-west-1.compute.amazonaws.com/littlecong/copyfromgeragen
17/05/09 05:34:35 INFO tools.DistCp: Input Options: DistCpOptions{atomicCommit=false, syncFolder=false, deleteMissing=false, ignoreFailures=false, overwrite=false, append=false, useDiff=false, useRdiff=false, fromSnapshot=null, toSnapshot=null, skipCRC=false, blocking=true, numListstatusThreads=0, maxMaps=20, mapBandwidth=100, sslConfigurationFile='null', copyStrategy='uniformsize', preserveStatus=[], preserveRawXattrs=false, atomicWorkPath=null, logPath=null, sourceFileListing=null, sourcePaths=[hdfs://ip-172-31-37-146.us-west-2.compute.internal/user/littlecong/teragen], targetPath=hdfs://ec2-54-193-126-200.us-west-1.compute.amazonaws.com/littlecong/copyfromgeragen, targetPathExists=false, filtersFile='null'}
17/05/09 05:34:35 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-37-146.us-west-2.compute.internal/172.31.37.146:8032
17/05/09 05:34:36 INFO tools.SimpleCopyListing: Paths (files+dirs) cnt = 4; dirCnt = 1
17/05/09 05:34:36 INFO tools.SimpleCopyListing: Build file listing completed.
17/05/09 05:34:36 INFO Configuration.deprecation: io.sort.mb is deprecated. Instead, use mapreduce.task.io.sort.mb
17/05/09 05:34:36 INFO Configuration.deprecation: io.sort.factor is deprecated. Instead, use mapreduce.task.io.sort.factor
17/05/09 05:34:36 INFO tools.DistCp: Number of paths in the copy list: 4
17/05/09 05:34:36 INFO tools.DistCp: Number of paths in the copy list: 4
17/05/09 05:34:36 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-37-146.us-west-2.compute.internal/172.31.37.146:8032
17/05/09 05:34:37 INFO mapreduce.JobSubmitter: number of splits:3
17/05/09 05:34:37 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1494301647320_0006
17/05/09 05:34:37 INFO impl.YarnClientImpl: Submitted application application_1494301647320_0006
17/05/09 05:34:37 INFO mapreduce.Job: The url to track the job: http://ip-172-31-37-146.us-west-2.compute.internal:8088/proxy/application_1494301647320_0006/
17/05/09 05:34:37 INFO tools.DistCp: DistCp job-id: job_1494301647320_0006
17/05/09 05:34:37 INFO mapreduce.Job: Running job: job_1494301647320_0006
17/05/09 05:34:44 INFO mapreduce.Job: Job job_1494301647320_0006 running in uber mode : false
17/05/09 05:34:44 INFO mapreduce.Job:  map 0% reduce 0%
17/05/09 05:34:52 INFO mapreduce.Job:  map 33% reduce 0%
17/05/09 05:34:56 INFO mapreduce.Job:  map 67% reduce 0%
17/05/09 05:34:57 INFO mapreduce.Job:  map 100% reduce 0%


17/05/09 05:46:57 INFO mapreduce.Job: Task Id : attempt_1494301647320_0006_m_000002_0, Status : FAILED
Error: java.io.IOException: File copy failed: hdfs://ip-172-31-37-146.us-west-2.compute.internal/user/littlecong/teragen/part-m-00001 --> hdfs://ec2-54-193-126-200.us-west-1.compute.amazonaws.com/littlecong/copyfromgeragen/part-m-00001
	at org.apache.hadoop.tools.mapred.CopyMapper.copyFileWithRetry(CopyMapper.java:284)
	at org.apache.hadoop.tools.mapred.CopyMapper.map(CopyMapper.java:252)
	at org.apache.hadoop.tools.mapred.CopyMapper.map(CopyMapper.java:50)
	at org.apache.hadoop.mapreduce.Mapper.run(Mapper.java:145)
	at org.apache.hadoop.mapred.MapTask.runNewMapper(MapTask.java:787)
	at org.apache.hadoop.mapred.MapTask.run(MapTask.java:341)
	at org.apache.hadoop.mapred.YarnChild$2.run(YarnChild.java:164)
	at java.security.AccessController.doPrivileged(Native Method)
	at javax.security.auth.Subject.doAs(Subject.java:415)
	at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1912)
	at org.apache.hadoop.mapred.YarnChild.main(YarnChild.java:158)
Caused by: java.io.IOException: Couldn't run retriable-command: Copying hdfs://ip-172-31-37-146.us-west-2.compute.internal/user/littlecong/teragen/part-m-00001 to hdfs://ec2-54-193-126-200.us-west-1.compute.amazonaws.com/littlecong/copyfromgeragen/part-m-00001
	at org.apache.hadoop.tools.util.RetriableCommand.execute(RetriableCommand.java:101)
	at org.apache.hadoop.tools.mapred.CopyMapper.copyFileWithRetry(CopyMapper.java:280)
	... 10 more
Caused by: org.apache.hadoop.net.ConnectTimeoutException: 60000 millis timeout while waiting for channel to be ready for connect. ch : java.nio.channels.SocketChannel[connection-pending remote=/172.31.0.228:50010]
	at org.apache.hadoop.net.NetUtils.connect(NetUtils.java:533)
	at org.apache.hadoop.hdfs.DFSOutputStream.createSocketForPipeline(DFSOutputStream.java:1923)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.createBlockOutputStream(DFSOutputStream.java:1666)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.nextBlockOutputStream(DFSOutputStream.java:1619)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.run(DFSOutputStream.java:771)

17/05/09 05:46:58 INFO mapreduce.Job:  map 67% reduce 0%
17/05/09 05:47:01 INFO mapreduce.Job: Task Id : attempt_1494301647320_0006_m_000001_0, Status : FAILED
Error: java.io.IOException: File copy failed: hdfs://ip-172-31-37-146.us-west-2.compute.internal/user/littlecong/teragen/part-m-00000 --> hdfs://ec2-54-193-126-200.us-west-1.compute.amazonaws.com/littlecong/copyfromgeragen/part-m-00000
	at org.apache.hadoop.tools.mapred.CopyMapper.copyFileWithRetry(CopyMapper.java:284)
	at org.apache.hadoop.tools.mapred.CopyMapper.map(CopyMapper.java:252)
	at org.apache.hadoop.tools.mapred.CopyMapper.map(CopyMapper.java:50)
	at org.apache.hadoop.mapreduce.Mapper.run(Mapper.java:145)
	at org.apache.hadoop.mapred.MapTask.runNewMapper(MapTask.java:787)
	at org.apache.hadoop.mapred.MapTask.run(MapTask.java:341)
	at org.apache.hadoop.mapred.YarnChild$2.run(YarnChild.java:164)
	at java.security.AccessController.doPrivileged(Native Method)
	at javax.security.auth.Subject.doAs(Subject.java:415)
	at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1912)
	at org.apache.hadoop.mapred.YarnChild.main(YarnChild.java:158)
Caused by: java.io.IOException: Couldn't run retriable-command: Copying hdfs://ip-172-31-37-146.us-west-2.compute.internal/user/littlecong/teragen/part-m-00000 to hdfs://ec2-54-193-126-200.us-west-1.compute.amazonaws.com/littlecong/copyfromgeragen/part-m-00000
	at org.apache.hadoop.tools.util.RetriableCommand.execute(RetriableCommand.java:101)
	at org.apache.hadoop.tools.mapred.CopyMapper.copyFileWithRetry(CopyMapper.java:280)
	... 10 more
Caused by: org.apache.hadoop.net.ConnectTimeoutException: 60000 millis timeout while waiting for channel to be ready for connect. ch : java.nio.channels.SocketChannel[connection-pending remote=/172.31.14.172:50010]
	at org.apache.hadoop.net.NetUtils.connect(NetUtils.java:533)
	at org.apache.hadoop.hdfs.DFSOutputStream.createSocketForPipeline(DFSOutputStream.java:1923)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.createBlockOutputStream(DFSOutputStream.java:1666)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.nextBlockOutputStream(DFSOutputStream.java:1619)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.run(DFSOutputStream.java:771)

17/05/09 05:47:02 INFO mapreduce.Job:  map 33% reduce 0%
17/05/09 05:47:09 INFO mapreduce.Job:  map 67% reduce 0%
17/05/09 05:47:14 INFO mapreduce.Job:  map 100% reduce 0%
17/05/09 05:59:11 INFO mapreduce.Job: Task Id : attempt_1494301647320_0006_m_000002_1, Status : FAILED
Error: java.io.IOException: File copy failed: hdfs://ip-172-31-37-146.us-west-2.compute.internal/user/littlecong/teragen/part-m-00001 --> hdfs://ec2-54-193-126-200.us-west-1.compute.amazonaws.com/littlecong/copyfromgeragen/part-m-00001
	at org.apache.hadoop.tools.mapred.CopyMapper.copyFileWithRetry(CopyMapper.java:284)
	at org.apache.hadoop.tools.mapred.CopyMapper.map(CopyMapper.java:252)
	at org.apache.hadoop.tools.mapred.CopyMapper.map(CopyMapper.java:50)
	at org.apache.hadoop.mapreduce.Mapper.run(Mapper.java:145)
	at org.apache.hadoop.mapred.MapTask.runNewMapper(MapTask.java:787)
	at org.apache.hadoop.mapred.MapTask.run(MapTask.java:341)
	at org.apache.hadoop.mapred.YarnChild$2.run(YarnChild.java:164)
	at java.security.AccessController.doPrivileged(Native Method)
	at javax.security.auth.Subject.doAs(Subject.java:415)
	at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1912)
	at org.apache.hadoop.mapred.YarnChild.main(YarnChild.java:158)
Caused by: java.io.IOException: Couldn't run retriable-command: Copying hdfs://ip-172-31-37-146.us-west-2.compute.internal/user/littlecong/teragen/part-m-00001 to hdfs://ec2-54-193-126-200.us-west-1.compute.amazonaws.com/littlecong/copyfromgeragen/part-m-00001
	at org.apache.hadoop.tools.util.RetriableCommand.execute(RetriableCommand.java:101)
	at org.apache.hadoop.tools.mapred.CopyMapper.copyFileWithRetry(CopyMapper.java:280)
	... 10 more
Caused by: org.apache.hadoop.net.ConnectTimeoutException: 60000 millis timeout while waiting for channel to be ready for connect. ch : java.nio.channels.SocketChannel[connection-pending remote=/172.31.9.243:50010]
	at org.apache.hadoop.net.NetUtils.connect(NetUtils.java:533)
	at org.apache.hadoop.hdfs.DFSOutputStream.createSocketForPipeline(DFSOutputStream.java:1923)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.createBlockOutputStream(DFSOutputStream.java:1666)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.nextBlockOutputStream(DFSOutputStream.java:1619)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.run(DFSOutputStream.java:771)

17/05/09 05:59:12 INFO mapreduce.Job:  map 67% reduce 0%
17/05/09 05:59:15 INFO mapreduce.Job: Task Id : attempt_1494301647320_0006_m_000001_1, Status : FAILED
Error: java.io.IOException: File copy failed: hdfs://ip-172-31-37-146.us-west-2.compute.internal/user/littlecong/teragen/part-m-00000 --> hdfs://ec2-54-193-126-200.us-west-1.compute.amazonaws.com/littlecong/copyfromgeragen/part-m-00000
	at org.apache.hadoop.tools.mapred.CopyMapper.copyFileWithRetry(CopyMapper.java:284)
	at org.apache.hadoop.tools.mapred.CopyMapper.map(CopyMapper.java:252)
	at org.apache.hadoop.tools.mapred.CopyMapper.map(CopyMapper.java:50)
	at org.apache.hadoop.mapreduce.Mapper.run(Mapper.java:145)
	at org.apache.hadoop.mapred.MapTask.runNewMapper(MapTask.java:787)
	at org.apache.hadoop.mapred.MapTask.run(MapTask.java:341)
	at org.apache.hadoop.mapred.YarnChild$2.run(YarnChild.java:164)
	at java.security.AccessController.doPrivileged(Native Method)
	at javax.security.auth.Subject.doAs(Subject.java:415)
	at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1912)
	at org.apache.hadoop.mapred.YarnChild.main(YarnChild.java:158)
Caused by: java.io.IOException: Couldn't run retriable-command: Copying hdfs://ip-172-31-37-146.us-west-2.compute.internal/user/littlecong/teragen/part-m-00000 to hdfs://ec2-54-193-126-200.us-west-1.compute.amazonaws.com/littlecong/copyfromgeragen/part-m-00000
	at org.apache.hadoop.tools.util.RetriableCommand.execute(RetriableCommand.java:101)
	at org.apache.hadoop.tools.mapred.CopyMapper.copyFileWithRetry(CopyMapper.java:280)
	... 10 more
Caused by: org.apache.hadoop.net.ConnectTimeoutException: 60000 millis timeout while waiting for channel to be ready for connect. ch : java.nio.channels.SocketChannel[connection-pending remote=/172.31.10.129:50010]
	at org.apache.hadoop.net.NetUtils.connect(NetUtils.java:533)
	at org.apache.hadoop.hdfs.DFSOutputStream.createSocketForPipeline(DFSOutputStream.java:1923)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.createBlockOutputStream(DFSOutputStream.java:1666)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.nextBlockOutputStream(DFSOutputStream.java:1619)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.run(DFSOutputStream.java:771)

17/05/09 05:59:16 INFO mapreduce.Job:  map 33% reduce 0%
17/05/09 05:59:23 INFO mapreduce.Job:  map 67% reduce 0%
17/05/09 05:59:27 INFO mapreduce.Job:  map 100% reduce 0%
17/05/09 06:11:24 INFO mapreduce.Job: Task Id : attempt_1494301647320_0006_m_000002_2, Status : FAILED
Error: java.io.IOException: File copy failed: hdfs://ip-172-31-37-146.us-west-2.compute.internal/user/littlecong/teragen/part-m-00001 --> hdfs://ec2-54-193-126-200.us-west-1.compute.amazonaws.com/littlecong/copyfromgeragen/part-m-00001
	at org.apache.hadoop.tools.mapred.CopyMapper.copyFileWithRetry(CopyMapper.java:284)
	at org.apache.hadoop.tools.mapred.CopyMapper.map(CopyMapper.java:252)
	at org.apache.hadoop.tools.mapred.CopyMapper.map(CopyMapper.java:50)
	at org.apache.hadoop.mapreduce.Mapper.run(Mapper.java:145)
	at org.apache.hadoop.mapred.MapTask.runNewMapper(MapTask.java:787)
	at org.apache.hadoop.mapred.MapTask.run(MapTask.java:341)
	at org.apache.hadoop.mapred.YarnChild$2.run(YarnChild.java:164)
	at java.security.AccessController.doPrivileged(Native Method)
	at javax.security.auth.Subject.doAs(Subject.java:415)
	at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1912)
	at org.apache.hadoop.mapred.YarnChild.main(YarnChild.java:158)
Caused by: java.io.IOException: Couldn't run retriable-command: Copying hdfs://ip-172-31-37-146.us-west-2.compute.internal/user/littlecong/teragen/part-m-00001 to hdfs://ec2-54-193-126-200.us-west-1.compute.amazonaws.com/littlecong/copyfromgeragen/part-m-00001
	at org.apache.hadoop.tools.util.RetriableCommand.execute(RetriableCommand.java:101)
	at org.apache.hadoop.tools.mapred.CopyMapper.copyFileWithRetry(CopyMapper.java:280)
	... 10 more
Caused by: org.apache.hadoop.net.ConnectTimeoutException: 60000 millis timeout while waiting for channel to be ready for connect. ch : java.nio.channels.SocketChannel[connection-pending remote=/172.31.0.114:50010]
	at org.apache.hadoop.net.NetUtils.connect(NetUtils.java:533)
	at org.apache.hadoop.hdfs.DFSOutputStream.createSocketForPipeline(DFSOutputStream.java:1923)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.createBlockOutputStream(DFSOutputStream.java:1666)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.nextBlockOutputStream(DFSOutputStream.java:1619)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.run(DFSOutputStream.java:771)

17/05/09 06:11:25 INFO mapreduce.Job:  map 67% reduce 0%
17/05/09 06:11:29 INFO mapreduce.Job: Task Id : attempt_1494301647320_0006_m_000001_2, Status : FAILED
Error: java.io.IOException: File copy failed: hdfs://ip-172-31-37-146.us-west-2.compute.internal/user/littlecong/teragen/part-m-00000 --> hdfs://ec2-54-193-126-200.us-west-1.compute.amazonaws.com/littlecong/copyfromgeragen/part-m-00000
	at org.apache.hadoop.tools.mapred.CopyMapper.copyFileWithRetry(CopyMapper.java:284)
	at org.apache.hadoop.tools.mapred.CopyMapper.map(CopyMapper.java:252)
	at org.apache.hadoop.tools.mapred.CopyMapper.map(CopyMapper.java:50)
	at org.apache.hadoop.mapreduce.Mapper.run(Mapper.java:145)
	at org.apache.hadoop.mapred.MapTask.runNewMapper(MapTask.java:787)
	at org.apache.hadoop.mapred.MapTask.run(MapTask.java:341)
	at org.apache.hadoop.mapred.YarnChild$2.run(YarnChild.java:164)
	at java.security.AccessController.doPrivileged(Native Method)
	at javax.security.auth.Subject.doAs(Subject.java:415)
	at org.apache.hadoop.security.UserGroupInformation.doAs(UserGroupInformation.java:1912)
	at org.apache.hadoop.mapred.YarnChild.main(YarnChild.java:158)
Caused by: java.io.IOException: Couldn't run retriable-command: Copying hdfs://ip-172-31-37-146.us-west-2.compute.internal/user/littlecong/teragen/part-m-00000 to hdfs://ec2-54-193-126-200.us-west-1.compute.amazonaws.com/littlecong/copyfromgeragen/part-m-00000
	at org.apache.hadoop.tools.util.RetriableCommand.execute(RetriableCommand.java:101)
	at org.apache.hadoop.tools.mapred.CopyMapper.copyFileWithRetry(CopyMapper.java:280)
	... 10 more
Caused by: org.apache.hadoop.net.ConnectTimeoutException: 60000 millis timeout while waiting for channel to be ready for connect. ch : java.nio.channels.SocketChannel[connection-pending remote=/172.31.14.172:50010]
	at org.apache.hadoop.net.NetUtils.connect(NetUtils.java:533)
	at org.apache.hadoop.hdfs.DFSOutputStream.createSocketForPipeline(DFSOutputStream.java:1923)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.createBlockOutputStream(DFSOutputStream.java:1666)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.nextBlockOutputStream(DFSOutputStream.java:1619)
	at org.apache.hadoop.hdfs.DFSOutputStream$DataStreamer.run(DFSOutputStream.java:771)

17/05/09 06:11:30 INFO mapreduce.Job:  map 33% reduce 0%
17/05/09 06:11:36 INFO mapreduce.Job:  map 67% reduce 0%
17/05/09 06:11:41 INFO mapreduce.Job:  map 100% reduce 0%
17/05/09 06:23:38 INFO mapreduce.Job: Job job_1494301647320_0006 failed with state FAILED due to: Task failed task_1494301647320_0006_m_000002
Job failed as tasks failed. failedMaps:1 failedReduces:0

17/05/09 06:23:38 INFO mapreduce.Job: Counters: 35
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=126586
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=727
		HDFS: Number of bytes written=0
		HDFS: Number of read operations=19
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=5
	Job Counters 
		Failed map tasks=7
		Killed map tasks=1
		Launched map tasks=9
		Other local map tasks=9
		Total time spent by all maps in occupied slots (ms)=5859225
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=5859225
		Total vcore-seconds taken by all map tasks=5859225
		Total megabyte-seconds taken by all map tasks=5999846400
	Map-Reduce Framework
		Map input records=2
		Map output records=0
		Input split bytes=116
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=33
		CPU time spent (ms)=560
		Physical memory (bytes) snapshot=179560448
		Virtual memory (bytes) snapshot=1578688512
		Total committed heap usage (bytes)=235929600
	File Input Format Counters 
		Bytes Read=611
	File Output Format Counters 
		Bytes Written=0
	org.apache.hadoop.tools.mapred.CopyMapper$Counter
		BYTESCOPIED=0
		BYTESEXPECTED=0
		COPY=2
17/05/09 06:23:38 ERROR tools.DistCp: Exception encountered 
java.io.IOException: DistCp failure: Job job_1494301647320_0006 has failed: Task failed task_1494301647320_0006_m_000002
Job failed as tasks failed. failedMaps:1 failedReduces:0

	at org.apache.hadoop.tools.DistCp.execute(DistCp.java:193)
	at org.apache.hadoop.tools.DistCp.run(DistCp.java:141)
	at org.apache.hadoop.util.ToolRunner.run(ToolRunner.java:70)
	at org.apache.hadoop.tools.DistCp.main(DistCp.java:441)
</pre>

2. HDFS Lab: Test HDFS throughput  
On all node exeute
<pre>
useradd -d /home/littlecong -m littlecong
</pre>
On hdfs gateway node execute
<pre>
 sudo -u hdfs hdfs dfs -mkdir /user/littlecong
 sudo -u hdfs hdfs dfs -chown -R littlecong /user/littlecong
</pre>

 
