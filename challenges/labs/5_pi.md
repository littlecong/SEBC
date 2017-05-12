# Run the Hadoop pi program as the user chen
```
[root@ip-172-31-37-248 jars]# time hadoop jar  hadoop-examples.jar pi   2 2
Number of Maps  = 2
Samples per Map = 2
Wrote input for Map #0
Wrote input for Map #1
Starting Job
17/05/12 03:44:13 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-37-248.us-west-2.compute.internal/172.31.37.248:8032
17/05/12 03:44:13 INFO hdfs.DFSClient: Created token for chen: HDFS_DELEGATION_TOKEN owner=chen@LITTLECONG.CN, renewer=yarn, realUser=, issueDate=1494560653619, maxDate=1495165453619, sequenceNumber=3, masterKeyId=2 on 172.31.43.100:8020
17/05/12 03:44:13 INFO security.TokenCache: Got dt for hdfs://ip-172-31-43-100.us-west-2.compute.internal:8020; Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.43.100:8020, Ident: (token for chen: HDFS_DELEGATION_TOKEN owner=chen@LITTLECONG.CN, renewer=yarn, realUser=, issueDate=1494560653619, maxDate=1495165453619, sequenceNumber=3, masterKeyId=2)
17/05/12 03:44:13 INFO input.FileInputFormat: Total input paths to process : 2
17/05/12 03:44:13 INFO mapreduce.JobSubmitter: number of splits:2
17/05/12 03:44:14 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1494559970217_0003
17/05/12 03:44:14 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.43.100:8020, Ident: (token for chen: HDFS_DELEGATION_TOKEN owner=chen@LITTLECONG.CN, renewer=yarn, realUser=, issueDate=1494560653619, maxDate=1495165453619, sequenceNumber=3, masterKeyId=2)
17/05/12 03:44:14 INFO impl.YarnClientImpl: Submitted application application_1494559970217_0003
17/05/12 03:44:14 INFO mapreduce.Job: The url to track the job: http://ip-172-31-37-248.us-west-2.compute.internal:8088/proxy/application_1494559970217_0003/
17/05/12 03:44:14 INFO mapreduce.Job: Running job: job_1494559970217_0003
17/05/12 03:44:24 INFO mapreduce.Job: Job job_1494559970217_0003 running in uber mode : false
17/05/12 03:44:24 INFO mapreduce.Job:  map 0% reduce 0%
17/05/12 03:44:29 INFO mapreduce.Job:  map 50% reduce 0%
17/05/12 03:44:32 INFO mapreduce.Job:  map 100% reduce 0%
17/05/12 03:44:38 INFO mapreduce.Job:  map 100% reduce 100%
17/05/12 03:44:38 INFO mapreduce.Job: Job job_1494559970217_0003 completed successfully
17/05/12 03:44:39 INFO mapreduce.Job: Counters: 50
	File System Counters
		FILE: Number of bytes read=45
		FILE: Number of bytes written=375458
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=596
		HDFS: Number of bytes written=215
		HDFS: Number of read operations=11
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=3
	Job Counters 
		Launched map tasks=2
		Launched reduce tasks=1
		Data-local map tasks=1
		Rack-local map tasks=1
		Total time spent by all maps in occupied slots (ms)=10290
		Total time spent by all reduces in occupied slots (ms)=3904
		Total time spent by all map tasks (ms)=10290
		Total time spent by all reduce tasks (ms)=3904
		Total vcore-seconds taken by all map tasks=10290
		Total vcore-seconds taken by all reduce tasks=3904
		Total megabyte-seconds taken by all map tasks=10536960
		Total megabyte-seconds taken by all reduce tasks=3997696
	Map-Reduce Framework
		Map input records=2
		Map output records=4
		Map output bytes=36
		Map output materialized bytes=66
		Input split bytes=360
		Combine input records=0
		Combine output records=0
		Reduce input groups=2
		Reduce shuffle bytes=66
		Reduce input records=4
		Reduce output records=0
		Spilled Records=8
		Shuffled Maps =2
		Failed Shuffles=0
		Merged Map outputs=2
		GC time elapsed (ms)=73
		CPU time spent (ms)=2460
		Physical memory (bytes) snapshot=1118339072
		Virtual memory (bytes) snapshot=4730470400
		Total committed heap usage (bytes)=1308098560
	Shuffle Errors
		BAD_ID=0
		CONNECTION=0
		IO_ERROR=0
		WRONG_LENGTH=0
		WRONG_MAP=0
		WRONG_REDUCE=0
	File Input Format Counters 
		Bytes Read=236
	File Output Format Counters 
		Bytes Written=97
Job Finished in 25.743 seconds
Estimated value of Pi is 4.00000000000000000000

real	0m29.418s
user	0m6.127s
sys	0m0.691s
```