# Run the terasort program as zhou using the output target /user/zhou/tsort

```
[root@ip-172-31-37-248 krb5kdc]# cd /opt/cloudera/parcels/CDH/jars
[root@ip-172-31-37-248 jars]# time hadoop jar  hadoop-examples.jar terasort  /user/zhou/tgen /user/zhou/tsort
17/05/12 03:37:23 INFO terasort.TeraSort: starting
17/05/12 03:37:25 INFO hdfs.DFSClient: Created token for zhou: HDFS_DELEGATION_TOKEN owner=zhou@LITTLECONG.CN, renewer=yarn, realUser=, issueDate=1494560245345, maxDate=1495165045345, sequenceNumber=1, masterKeyId=2 on 172.31.43.100:8020
17/05/12 03:37:25 INFO security.TokenCache: Got dt for hdfs://ip-172-31-43-100.us-west-2.compute.internal:8020; Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.43.100:8020, Ident: (token for zhou: HDFS_DELEGATION_TOKEN owner=zhou@LITTLECONG.CN, renewer=yarn, realUser=, issueDate=1494560245345, maxDate=1495165045345, sequenceNumber=1, masterKeyId=2)
17/05/12 03:37:25 INFO input.FileInputFormat: Total input paths to process : 6
Spent 400ms computing base-splits.
Spent 3ms computing TeraScheduler splits.
Computing input splits took 404ms
Sampling 10 splits of 102
Making 8 from 100000 sampled records
Computing parititions took 978ms
Spent 1386ms computing partitions.
17/05/12 03:37:26 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-37-248.us-west-2.compute.internal/172.31.37.248:8032
17/05/12 03:37:27 INFO mapreduce.JobSubmitter: number of splits:102
17/05/12 03:37:27 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1494559970217_0001
17/05/12 03:37:27 INFO mapreduce.JobSubmitter: Kind: HDFS_DELEGATION_TOKEN, Service: 172.31.43.100:8020, Ident: (token for zhou: HDFS_DELEGATION_TOKEN owner=zhou@LITTLECONG.CN, renewer=yarn, realUser=, issueDate=1494560245345, maxDate=1495165045345, sequenceNumber=1, masterKeyId=2)
17/05/12 03:37:28 INFO impl.YarnClientImpl: Submitted application application_1494559970217_0001
17/05/12 03:37:28 INFO mapreduce.Job: The url to track the job: http://ip-172-31-37-248.us-west-2.compute.internal:8088/proxy/application_1494559970217_0001/
17/05/12 03:37:28 INFO mapreduce.Job: Running job: job_1494559970217_0001
17/05/12 03:37:38 INFO mapreduce.Job: Job job_1494559970217_0001 running in uber mode : false
17/05/12 03:37:38 INFO mapreduce.Job:  map 0% reduce 0%
17/05/12 03:37:53 INFO mapreduce.Job:  map 4% reduce 0%
17/05/12 03:37:57 INFO mapreduce.Job:  map 7% reduce 0%
17/05/12 03:38:03 INFO mapreduce.Job:  map 11% reduce 0%
17/05/12 03:38:08 INFO mapreduce.Job:  map 12% reduce 0%
17/05/12 03:38:09 INFO mapreduce.Job:  map 14% reduce 0%
17/05/12 03:38:12 INFO mapreduce.Job:  map 16% reduce 0%
17/05/12 03:38:13 INFO mapreduce.Job:  map 18% reduce 0%
17/05/12 03:38:20 INFO mapreduce.Job:  map 19% reduce 0%
17/05/12 03:38:21 INFO mapreduce.Job:  map 22% reduce 0%
17/05/12 03:38:22 INFO mapreduce.Job:  map 23% reduce 0%
17/05/12 03:38:23 INFO mapreduce.Job:  map 25% reduce 0%
17/05/12 03:38:30 INFO mapreduce.Job:  map 26% reduce 0%
17/05/12 03:38:32 INFO mapreduce.Job:  map 29% reduce 0%
17/05/12 03:38:33 INFO mapreduce.Job:  map 31% reduce 0%
17/05/12 03:38:39 INFO mapreduce.Job:  map 32% reduce 0%
17/05/12 03:38:40 INFO mapreduce.Job:  map 33% reduce 0%
17/05/12 03:38:43 INFO mapreduce.Job:  map 35% reduce 0%
17/05/12 03:38:45 INFO mapreduce.Job:  map 36% reduce 0%
17/05/12 03:38:46 INFO mapreduce.Job:  map 38% reduce 0%
17/05/12 03:38:48 INFO mapreduce.Job:  map 39% reduce 0%
17/05/12 03:38:49 INFO mapreduce.Job:  map 40% reduce 0%
17/05/12 03:38:52 INFO mapreduce.Job:  map 41% reduce 0%
17/05/12 03:38:53 INFO mapreduce.Job:  map 42% reduce 0%
17/05/12 03:38:57 INFO mapreduce.Job:  map 44% reduce 0%
17/05/12 03:38:58 INFO mapreduce.Job:  map 47% reduce 0%
17/05/12 03:39:01 INFO mapreduce.Job:  map 48% reduce 0%
17/05/12 03:39:02 INFO mapreduce.Job:  map 49% reduce 0%
17/05/12 03:39:07 INFO mapreduce.Job:  map 50% reduce 0%
17/05/12 03:39:08 INFO mapreduce.Job:  map 52% reduce 0%
17/05/12 03:39:09 INFO mapreduce.Job:  map 55% reduce 0%
17/05/12 03:39:10 INFO mapreduce.Job:  map 56% reduce 0%
17/05/12 03:39:17 INFO mapreduce.Job:  map 58% reduce 0%
17/05/12 03:39:19 INFO mapreduce.Job:  map 60% reduce 0%
17/05/12 03:39:20 INFO mapreduce.Job:  map 62% reduce 0%
17/05/12 03:39:21 INFO mapreduce.Job:  map 63% reduce 0%
17/05/12 03:39:26 INFO mapreduce.Job:  map 65% reduce 0%
17/05/12 03:39:28 INFO mapreduce.Job:  map 66% reduce 0%
17/05/12 03:39:29 INFO mapreduce.Job:  map 68% reduce 0%
17/05/12 03:39:32 INFO mapreduce.Job:  map 70% reduce 0%
17/05/12 03:39:34 INFO mapreduce.Job:  map 71% reduce 0%
17/05/12 03:39:35 INFO mapreduce.Job:  map 72% reduce 0%
17/05/12 03:39:37 INFO mapreduce.Job:  map 73% reduce 0%
17/05/12 03:39:38 INFO mapreduce.Job:  map 74% reduce 0%
17/05/12 03:39:40 INFO mapreduce.Job:  map 75% reduce 0%
17/05/12 03:39:44 INFO mapreduce.Job:  map 78% reduce 0%
17/05/12 03:39:46 INFO mapreduce.Job:  map 79% reduce 0%
17/05/12 03:39:47 INFO mapreduce.Job:  map 80% reduce 0%
17/05/12 03:39:51 INFO mapreduce.Job:  map 81% reduce 0%
17/05/12 03:39:52 INFO mapreduce.Job:  map 82% reduce 0%
17/05/12 03:39:53 INFO mapreduce.Job:  map 83% reduce 0%
17/05/12 03:39:55 INFO mapreduce.Job:  map 86% reduce 0%
17/05/12 03:39:56 INFO mapreduce.Job:  map 87% reduce 0%
17/05/12 03:40:02 INFO mapreduce.Job:  map 89% reduce 0%
17/05/12 03:40:04 INFO mapreduce.Job:  map 90% reduce 0%
17/05/12 03:40:05 INFO mapreduce.Job:  map 90% reduce 3%
17/05/12 03:40:07 INFO mapreduce.Job:  map 90% reduce 9%
17/05/12 03:40:08 INFO mapreduce.Job:  map 90% reduce 13%
17/05/12 03:40:10 INFO mapreduce.Job:  map 90% reduce 14%
17/05/12 03:40:11 INFO mapreduce.Job:  map 92% reduce 15%
17/05/12 03:40:13 INFO mapreduce.Job:  map 93% reduce 15%
17/05/12 03:40:16 INFO mapreduce.Job:  map 94% reduce 15%
17/05/12 03:40:17 INFO mapreduce.Job:  map 94% reduce 16%
17/05/12 03:40:18 INFO mapreduce.Job:  map 95% reduce 16%
17/05/12 03:40:19 INFO mapreduce.Job:  map 96% reduce 16%
17/05/12 03:40:22 INFO mapreduce.Job:  map 97% reduce 16%
17/05/12 03:40:23 INFO mapreduce.Job:  map 98% reduce 16%
17/05/12 03:40:27 INFO mapreduce.Job:  map 99% reduce 16%
17/05/12 03:40:29 INFO mapreduce.Job:  map 99% reduce 17%
17/05/12 03:40:31 INFO mapreduce.Job:  map 100% reduce 17%
17/05/12 03:40:32 INFO mapreduce.Job:  map 100% reduce 22%
17/05/12 03:40:33 INFO mapreduce.Job:  map 100% reduce 26%
17/05/12 03:40:34 INFO mapreduce.Job:  map 100% reduce 30%
17/05/12 03:40:35 INFO mapreduce.Job:  map 100% reduce 39%
17/05/12 03:40:36 INFO mapreduce.Job:  map 100% reduce 40%
17/05/12 03:40:37 INFO mapreduce.Job:  map 100% reduce 44%
17/05/12 03:40:38 INFO mapreduce.Job:  map 100% reduce 46%
17/05/12 03:40:39 INFO mapreduce.Job:  map 100% reduce 49%
17/05/12 03:40:40 INFO mapreduce.Job:  map 100% reduce 51%
17/05/12 03:40:41 INFO mapreduce.Job:  map 100% reduce 53%
17/05/12 03:40:42 INFO mapreduce.Job:  map 100% reduce 54%
17/05/12 03:40:43 INFO mapreduce.Job:  map 100% reduce 55%
17/05/12 03:40:44 INFO mapreduce.Job:  map 100% reduce 61%
17/05/12 03:40:45 INFO mapreduce.Job:  map 100% reduce 62%
17/05/12 03:40:46 INFO mapreduce.Job:  map 100% reduce 67%
17/05/12 03:40:47 INFO mapreduce.Job:  map 100% reduce 70%
17/05/12 03:40:48 INFO mapreduce.Job:  map 100% reduce 71%
17/05/12 03:40:49 INFO mapreduce.Job:  map 100% reduce 72%
17/05/12 03:40:50 INFO mapreduce.Job:  map 100% reduce 77%
17/05/12 03:40:51 INFO mapreduce.Job:  map 100% reduce 79%
17/05/12 03:40:52 INFO mapreduce.Job:  map 100% reduce 80%
17/05/12 03:40:53 INFO mapreduce.Job:  map 100% reduce 81%
17/05/12 03:40:55 INFO mapreduce.Job:  map 100% reduce 82%
17/05/12 03:40:56 INFO mapreduce.Job:  map 100% reduce 83%
17/05/12 03:40:58 INFO mapreduce.Job:  map 100% reduce 87%
17/05/12 03:40:59 INFO mapreduce.Job:  map 100% reduce 88%
17/05/12 03:41:01 INFO mapreduce.Job:  map 100% reduce 90%
17/05/12 03:41:02 INFO mapreduce.Job:  map 100% reduce 91%
17/05/12 03:41:03 INFO mapreduce.Job:  map 100% reduce 92%
17/05/12 03:41:04 INFO mapreduce.Job:  map 100% reduce 96%
17/05/12 03:41:07 INFO mapreduce.Job:  map 100% reduce 97%
17/05/12 03:41:10 INFO mapreduce.Job:  map 100% reduce 99%
17/05/12 03:41:13 INFO mapreduce.Job:  map 100% reduce 100%
17/05/12 03:41:13 INFO mapreduce.Job: Job job_1494559970217_0001 completed successfully
17/05/12 03:41:13 INFO mapreduce.Job: Counters: 50
	File System Counters
		FILE: Number of bytes read=2931118471
		FILE: Number of bytes written=5818032206
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=6553615096
		HDFS: Number of bytes written=6553600000
		HDFS: Number of read operations=330
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=16
	Job Counters 
		Launched map tasks=102
		Launched reduce tasks=8
		Data-local map tasks=100
		Rack-local map tasks=2
		Total time spent by all maps in occupied slots (ms)=934046
		Total time spent by all reduces in occupied slots (ms)=335624
		Total time spent by all map tasks (ms)=934046
		Total time spent by all reduce tasks (ms)=335624
		Total vcore-seconds taken by all map tasks=934046
		Total vcore-seconds taken by all reduce tasks=335624
		Total megabyte-seconds taken by all map tasks=956463104
		Total megabyte-seconds taken by all reduce tasks=343678976
	Map-Reduce Framework
		Map input records=65536000
		Map output records=65536000
		Map output bytes=6684672000
		Map output materialized bytes=2873061739
		Input split bytes=15096
		Combine input records=0
		Combine output records=0
		Reduce input groups=65536000
		Reduce shuffle bytes=2873061739
		Reduce input records=65536000
		Reduce output records=65536000
		Spilled Records=131072000
		Shuffled Maps =816
		Failed Shuffles=0
		Merged Map outputs=816
		GC time elapsed (ms)=15608
		CPU time spent (ms)=735340
		Physical memory (bytes) snapshot=58117173248
		Virtual memory (bytes) snapshot=172157865984
		Total committed heap usage (bytes)=67541401600
	Shuffle Errors
		BAD_ID=0
		CONNECTION=0
		IO_ERROR=0
		WRONG_LENGTH=0
		WRONG_MAP=0
		WRONG_REDUCE=0
	File Input Format Counters 
		Bytes Read=6553600000
	File Output Format Counters 
		Bytes Written=6553600000
17/05/12 03:41:13 INFO terasort.TeraSort: done

real	3m51.841s
user	0m9.102s
sys	0m0.960s
```