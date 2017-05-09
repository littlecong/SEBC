Create a 10 GB file using teragen
<pre>
[littlecong@ip-172-31-37-12 jars]$ time hadoop jar  hadoop-examples.jar teragen -Dmapreduce.job.maps=4 -Ddfs.blocksize=32m 104857600 /user/littlecong/10G
17/05/09 07:41:26 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-37-146.us-west-2.compute.internal/172.31.37.146:8032
17/05/09 07:41:27 INFO terasort.TeraSort: Generating 104857600 using 4
17/05/09 07:41:27 INFO mapreduce.JobSubmitter: number of splits:4
17/05/09 07:41:27 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1494301647320_0008
17/05/09 07:41:28 INFO impl.YarnClientImpl: Submitted application application_1494301647320_0008
17/05/09 07:41:28 INFO mapreduce.Job: The url to track the job: http://ip-172-31-37-146.us-west-2.compute.internal:8088/proxy/application_1494301647320_0008/
17/05/09 07:41:28 INFO mapreduce.Job: Running job: job_1494301647320_0008
17/05/09 07:41:35 INFO mapreduce.Job: Job job_1494301647320_0008 running in uber mode : false
17/05/09 07:41:35 INFO mapreduce.Job:  map 0% reduce 0%
17/05/09 07:41:48 INFO mapreduce.Job:  map 4% reduce 0%
17/05/09 07:41:49 INFO mapreduce.Job:  map 7% reduce 0%
17/05/09 07:41:51 INFO mapreduce.Job:  map 9% reduce 0%
17/05/09 07:41:52 INFO mapreduce.Job:  map 11% reduce 0%
17/05/09 07:41:54 INFO mapreduce.Job:  map 13% reduce 0%
17/05/09 07:41:55 INFO mapreduce.Job:  map 15% reduce 0%
17/05/09 07:41:57 INFO mapreduce.Job:  map 16% reduce 0%
17/05/09 07:41:58 INFO mapreduce.Job:  map 18% reduce 0%
17/05/09 07:42:00 INFO mapreduce.Job:  map 19% reduce 0%
17/05/09 07:42:01 INFO mapreduce.Job:  map 20% reduce 0%
17/05/09 07:42:08 INFO mapreduce.Job:  map 21% reduce 0%
17/05/09 07:42:11 INFO mapreduce.Job:  map 23% reduce 0%
17/05/09 07:42:17 INFO mapreduce.Job:  map 24% reduce 0%
17/05/09 07:42:21 INFO mapreduce.Job:  map 25% reduce 0%
17/05/09 07:42:27 INFO mapreduce.Job:  map 26% reduce 0%
17/05/09 07:42:30 INFO mapreduce.Job:  map 27% reduce 0%
17/05/09 07:42:33 INFO mapreduce.Job:  map 28% reduce 0%
17/05/09 07:42:42 INFO mapreduce.Job:  map 31% reduce 0%
17/05/09 07:42:48 INFO mapreduce.Job:  map 32% reduce 0%
17/05/09 07:42:54 INFO mapreduce.Job:  map 33% reduce 0%
17/05/09 07:42:57 INFO mapreduce.Job:  map 34% reduce 0%
17/05/09 07:43:03 INFO mapreduce.Job:  map 35% reduce 0%
17/05/09 07:43:06 INFO mapreduce.Job:  map 36% reduce 0%
17/05/09 07:43:12 INFO mapreduce.Job:  map 37% reduce 0%
17/05/09 07:43:15 INFO mapreduce.Job:  map 38% reduce 0%
17/05/09 07:43:21 INFO mapreduce.Job:  map 39% reduce 0%
17/05/09 07:43:26 INFO mapreduce.Job:  map 40% reduce 0%
17/05/09 07:43:30 INFO mapreduce.Job:  map 41% reduce 0%
17/05/09 07:43:33 INFO mapreduce.Job:  map 42% reduce 0%
17/05/09 07:43:39 INFO mapreduce.Job:  map 43% reduce 0%
17/05/09 07:43:42 INFO mapreduce.Job:  map 44% reduce 0%
17/05/09 07:43:45 INFO mapreduce.Job:  map 45% reduce 0%
17/05/09 07:43:51 INFO mapreduce.Job:  map 46% reduce 0%
17/05/09 07:43:57 INFO mapreduce.Job:  map 47% reduce 0%
17/05/09 07:44:00 INFO mapreduce.Job:  map 48% reduce 0%
17/05/09 07:44:04 INFO mapreduce.Job:  map 49% reduce 0%
17/05/09 07:44:07 INFO mapreduce.Job:  map 50% reduce 0%
17/05/09 07:44:13 INFO mapreduce.Job:  map 51% reduce 0%
17/05/09 07:44:19 INFO mapreduce.Job:  map 52% reduce 0%
17/05/09 07:44:22 INFO mapreduce.Job:  map 53% reduce 0%
17/05/09 07:44:28 INFO mapreduce.Job:  map 54% reduce 0%
17/05/09 07:44:31 INFO mapreduce.Job:  map 55% reduce 0%
17/05/09 07:44:40 INFO mapreduce.Job:  map 57% reduce 0%
17/05/09 07:44:46 INFO mapreduce.Job:  map 58% reduce 0%
17/05/09 07:44:52 INFO mapreduce.Job:  map 59% reduce 0%
17/05/09 07:44:55 INFO mapreduce.Job:  map 60% reduce 0%
17/05/09 07:45:07 INFO mapreduce.Job:  map 62% reduce 0%
17/05/09 07:45:19 INFO mapreduce.Job:  map 64% reduce 0%
17/05/09 07:45:22 INFO mapreduce.Job:  map 65% reduce 0%
17/05/09 07:45:25 INFO mapreduce.Job:  map 66% reduce 0%
17/05/09 07:45:28 INFO mapreduce.Job:  map 67% reduce 0%
17/05/09 07:45:37 INFO mapreduce.Job:  map 68% reduce 0%
17/05/09 07:45:40 INFO mapreduce.Job:  map 69% reduce 0%
17/05/09 07:45:43 INFO mapreduce.Job:  map 70% reduce 0%
17/05/09 07:45:53 INFO mapreduce.Job:  map 71% reduce 0%
17/05/09 07:45:56 INFO mapreduce.Job:  map 73% reduce 0%
17/05/09 07:46:03 INFO mapreduce.Job:  map 74% reduce 0%
17/05/09 07:46:06 INFO mapreduce.Job:  map 75% reduce 0%
17/05/09 07:46:10 INFO mapreduce.Job:  map 76% reduce 0%
17/05/09 07:46:21 INFO mapreduce.Job:  map 78% reduce 0%
17/05/09 07:46:33 INFO mapreduce.Job:  map 81% reduce 0%
17/05/09 07:46:39 INFO mapreduce.Job:  map 82% reduce 0%
17/05/09 07:46:42 INFO mapreduce.Job:  map 83% reduce 0%
17/05/09 07:46:49 INFO mapreduce.Job:  map 84% reduce 0%
17/05/09 07:46:55 INFO mapreduce.Job:  map 85% reduce 0%
17/05/09 07:47:00 INFO mapreduce.Job:  map 86% reduce 0%
17/05/09 07:47:04 INFO mapreduce.Job:  map 87% reduce 0%
17/05/09 07:47:07 INFO mapreduce.Job:  map 88% reduce 0%
17/05/09 07:47:14 INFO mapreduce.Job:  map 89% reduce 0%
17/05/09 07:47:16 INFO mapreduce.Job:  map 90% reduce 0%
17/05/09 07:47:20 INFO mapreduce.Job:  map 91% reduce 0%
17/05/09 07:47:28 INFO mapreduce.Job:  map 93% reduce 0%
17/05/09 07:47:35 INFO mapreduce.Job:  map 94% reduce 0%
17/05/09 07:47:38 INFO mapreduce.Job:  map 95% reduce 0%
17/05/09 07:47:44 INFO mapreduce.Job:  map 96% reduce 0%
17/05/09 07:47:53 INFO mapreduce.Job:  map 97% reduce 0%
17/05/09 07:47:56 INFO mapreduce.Job:  map 99% reduce 0%
17/05/09 07:48:02 INFO mapreduce.Job:  map 100% reduce 0%
17/05/09 07:48:08 INFO mapreduce.Job: Job job_1494301647320_0008 completed successfully
17/05/09 07:48:09 INFO mapreduce.Job: Counters: 31
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=494252
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=344
		HDFS: Number of bytes written=10485760000
		HDFS: Number of read operations=16
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=8
	Job Counters 
		Launched map tasks=4
		Other local map tasks=4
		Total time spent by all maps in occupied slots (ms)=1449276
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=1449276
		Total vcore-seconds taken by all map tasks=1449276
		Total megabyte-seconds taken by all map tasks=1484058624
	Map-Reduce Framework
		Map input records=104857600
		Map output records=104857600
		Input split bytes=344
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=1781
		CPU time spent (ms)=175950
		Physical memory (bytes) snapshot=689655808
		Virtual memory (bytes) snapshot=6278799360
		Total committed heap usage (bytes)=892862464
	org.apache.hadoop.examples.terasort.TeraGen$Counters
		CHECKSUM=225186913807133164
	File Input Format Counters 
		Bytes Read=0
	File Output Format Counters 
		Bytes Written=10485760000

real	6m45.644s
user	0m6.777s
sys	0m0.937s
</pre>
Run the terasort command on this file
<pre>
[littlecong@ip-172-31-37-12 jars]$ time hadoop jar  hadoop-examples.jar terasort  /user/littlecong/10G /user/littlecong/10G_sorted
17/05/09 09:44:12 INFO terasort.TeraSort: starting
17/05/09 09:44:14 INFO input.FileInputFormat: Total input paths to process : 4
Spent 305ms computing base-splits.
Spent 7ms computing TeraScheduler splits.
Computing input splits took 313ms
Sampling 10 splits of 316
Making 4 from 100000 sampled records
Computing parititions took 894ms
Spent 1210ms computing partitions.
17/05/09 09:44:15 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-37-146.us-west-2.compute.internal/172.31.37.146:8032
17/05/09 09:44:16 INFO mapreduce.JobSubmitter: number of splits:316
17/05/09 09:44:16 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1494319855232_0001
17/05/09 09:44:17 INFO impl.YarnClientImpl: Submitted application application_1494319855232_0001
17/05/09 09:44:17 INFO mapreduce.Job: The url to track the job: http://ip-172-31-37-146.us-west-2.compute.internal:8088/proxy/application_1494319855232_0001/
17/05/09 09:44:17 INFO mapreduce.Job: Running job: job_1494319855232_0001
17/05/09 09:44:25 INFO mapreduce.Job: Job job_1494319855232_0001 running in uber mode : false
17/05/09 09:44:25 INFO mapreduce.Job:  map 0% reduce 0%
17/05/09 09:44:36 INFO mapreduce.Job:  map 1% reduce 0%
17/05/09 09:44:38 INFO mapreduce.Job:  map 4% reduce 0%
17/05/09 09:44:44 INFO mapreduce.Job:  map 5% reduce 0%
17/05/09 09:44:49 INFO mapreduce.Job:  map 8% reduce 0%
17/05/09 09:44:50 INFO mapreduce.Job:  map 9% reduce 0%
17/05/09 09:44:59 INFO mapreduce.Job:  map 11% reduce 0%
17/05/09 09:45:00 INFO mapreduce.Job:  map 13% reduce 0%
17/05/09 09:45:02 INFO mapreduce.Job:  map 14% reduce 0%
17/05/09 09:45:10 INFO mapreduce.Job:  map 16% reduce 0%
17/05/09 09:45:11 INFO mapreduce.Job:  map 17% reduce 0%
17/05/09 09:45:13 INFO mapreduce.Job:  map 18% reduce 0%
17/05/09 09:45:20 INFO mapreduce.Job:  map 19% reduce 0%
17/05/09 09:45:21 INFO mapreduce.Job:  map 21% reduce 0%
17/05/09 09:45:22 INFO mapreduce.Job:  map 22% reduce 0%
17/05/09 09:45:26 INFO mapreduce.Job:  map 23% reduce 0%
17/05/09 09:45:32 INFO mapreduce.Job:  map 24% reduce 0%
17/05/09 09:45:33 INFO mapreduce.Job:  map 25% reduce 0%
17/05/09 09:45:34 INFO mapreduce.Job:  map 26% reduce 0%
17/05/09 09:45:35 INFO mapreduce.Job:  map 27% reduce 0%
17/05/09 09:45:39 INFO mapreduce.Job:  map 28% reduce 0%
17/05/09 09:45:43 INFO mapreduce.Job:  map 29% reduce 0%
17/05/09 09:45:44 INFO mapreduce.Job:  map 30% reduce 0%
17/05/09 09:45:45 INFO mapreduce.Job:  map 31% reduce 0%
17/05/09 09:45:48 INFO mapreduce.Job:  map 32% reduce 0%
17/05/09 09:45:53 INFO mapreduce.Job:  map 33% reduce 0%
17/05/09 09:45:55 INFO mapreduce.Job:  map 34% reduce 0%
17/05/09 09:45:56 INFO mapreduce.Job:  map 35% reduce 0%
17/05/09 09:45:57 INFO mapreduce.Job:  map 36% reduce 0%
17/05/09 09:46:00 INFO mapreduce.Job:  map 37% reduce 0%
17/05/09 09:46:03 INFO mapreduce.Job:  map 38% reduce 0%
17/05/09 09:46:08 INFO mapreduce.Job:  map 39% reduce 0%
17/05/09 09:46:09 INFO mapreduce.Job:  map 41% reduce 0%
17/05/09 09:46:16 INFO mapreduce.Job:  map 42% reduce 0%
17/05/09 09:46:17 INFO mapreduce.Job:  map 43% reduce 0%
17/05/09 09:46:19 INFO mapreduce.Job:  map 44% reduce 0%
17/05/09 09:46:20 INFO mapreduce.Job:  map 45% reduce 0%
17/05/09 09:46:22 INFO mapreduce.Job:  map 46% reduce 0%
17/05/09 09:46:26 INFO mapreduce.Job:  map 47% reduce 0%
17/05/09 09:46:30 INFO mapreduce.Job:  map 48% reduce 0%
17/05/09 09:46:31 INFO mapreduce.Job:  map 49% reduce 0%
17/05/09 09:46:33 INFO mapreduce.Job:  map 50% reduce 0%
17/05/09 09:46:36 INFO mapreduce.Job:  map 51% reduce 0%
17/05/09 09:46:37 INFO mapreduce.Job:  map 52% reduce 0%
17/05/09 09:46:41 INFO mapreduce.Job:  map 53% reduce 0%
17/05/09 09:46:42 INFO mapreduce.Job:  map 54% reduce 0%
17/05/09 09:46:45 INFO mapreduce.Job:  map 55% reduce 0%
17/05/09 09:46:47 INFO mapreduce.Job:  map 56% reduce 0%
17/05/09 09:46:50 INFO mapreduce.Job:  map 57% reduce 0%
17/05/09 09:46:54 INFO mapreduce.Job:  map 59% reduce 0%
17/05/09 09:46:56 INFO mapreduce.Job:  map 60% reduce 0%
17/05/09 09:46:59 INFO mapreduce.Job:  map 61% reduce 0%
17/05/09 09:47:03 INFO mapreduce.Job:  map 62% reduce 0%
17/05/09 09:47:05 INFO mapreduce.Job:  map 63% reduce 0%
17/05/09 09:47:06 INFO mapreduce.Job:  map 64% reduce 0%
17/05/09 09:47:10 INFO mapreduce.Job:  map 65% reduce 0%
17/05/09 09:47:12 INFO mapreduce.Job:  map 66% reduce 0%
17/05/09 09:47:15 INFO mapreduce.Job:  map 67% reduce 0%
17/05/09 09:47:17 INFO mapreduce.Job:  map 68% reduce 0%
17/05/09 09:47:20 INFO mapreduce.Job:  map 69% reduce 0%
17/05/09 09:47:22 INFO mapreduce.Job:  map 70% reduce 0%
17/05/09 09:47:24 INFO mapreduce.Job:  map 71% reduce 0%
17/05/09 09:47:26 INFO mapreduce.Job:  map 72% reduce 0%
17/05/09 09:47:30 INFO mapreduce.Job:  map 73% reduce 0%
17/05/09 09:47:33 INFO mapreduce.Job:  map 74% reduce 0%
17/05/09 09:47:34 INFO mapreduce.Job:  map 75% reduce 0%
17/05/09 09:47:37 INFO mapreduce.Job:  map 76% reduce 0%
17/05/09 09:47:38 INFO mapreduce.Job:  map 77% reduce 0%
17/05/09 09:47:41 INFO mapreduce.Job:  map 78% reduce 0%
17/05/09 09:47:44 INFO mapreduce.Job:  map 79% reduce 0%
17/05/09 09:47:45 INFO mapreduce.Job:  map 80% reduce 0%
17/05/09 09:47:49 INFO mapreduce.Job:  map 81% reduce 0%
17/05/09 09:47:51 INFO mapreduce.Job:  map 82% reduce 0%
17/05/09 09:47:52 INFO mapreduce.Job:  map 83% reduce 0%
17/05/09 09:47:54 INFO mapreduce.Job:  map 84% reduce 0%
17/05/09 09:47:58 INFO mapreduce.Job:  map 85% reduce 0%
17/05/09 09:48:03 INFO mapreduce.Job:  map 85% reduce 2%
17/05/09 09:48:04 INFO mapreduce.Job:  map 86% reduce 6%
17/05/09 09:48:05 INFO mapreduce.Job:  map 86% reduce 7%
17/05/09 09:48:08 INFO mapreduce.Job:  map 87% reduce 11%
17/05/09 09:48:09 INFO mapreduce.Job:  map 88% reduce 11%
17/05/09 09:48:11 INFO mapreduce.Job:  map 88% reduce 14%
17/05/09 09:48:13 INFO mapreduce.Job:  map 89% reduce 14%
17/05/09 09:48:14 INFO mapreduce.Job:  map 89% reduce 15%
17/05/09 09:48:17 INFO mapreduce.Job:  map 89% reduce 19%
17/05/09 09:48:18 INFO mapreduce.Job:  map 90% reduce 19%
17/05/09 09:48:20 INFO mapreduce.Job:  map 91% reduce 23%
17/05/09 09:48:23 INFO mapreduce.Job:  map 91% reduce 24%
17/05/09 09:48:24 INFO mapreduce.Job:  map 92% reduce 24%
17/05/09 09:48:26 INFO mapreduce.Job:  map 92% reduce 28%
17/05/09 09:48:28 INFO mapreduce.Job:  map 93% reduce 28%
17/05/09 09:48:29 INFO mapreduce.Job:  map 94% reduce 29%
17/05/09 09:48:30 INFO mapreduce.Job:  map 94% reduce 30%
17/05/09 09:48:32 INFO mapreduce.Job:  map 94% reduce 31%
17/05/09 09:48:33 INFO mapreduce.Job:  map 95% reduce 31%
17/05/09 09:48:34 INFO mapreduce.Job:  map 96% reduce 31%
17/05/09 09:48:35 INFO mapreduce.Job:  map 96% reduce 32%
17/05/09 09:48:43 INFO mapreduce.Job:  map 97% reduce 32%
17/05/09 09:49:08 INFO mapreduce.Job:  map 99% reduce 32%
17/05/09 09:49:11 INFO mapreduce.Job:  map 99% reduce 33%
17/05/09 09:49:13 INFO mapreduce.Job:  map 100% reduce 33%
17/05/09 09:49:14 INFO mapreduce.Job:  map 100% reduce 34%
17/05/09 09:49:17 INFO mapreduce.Job:  map 100% reduce 67%
17/05/09 09:49:20 INFO mapreduce.Job:  map 100% reduce 68%
17/05/09 09:49:23 INFO mapreduce.Job:  map 100% reduce 70%
17/05/09 09:49:30 INFO mapreduce.Job:  map 100% reduce 72%
17/05/09 09:49:33 INFO mapreduce.Job:  map 100% reduce 75%
17/05/09 09:49:39 INFO mapreduce.Job:  map 100% reduce 78%
17/05/09 09:49:42 INFO mapreduce.Job:  map 100% reduce 80%
17/05/09 09:49:45 INFO mapreduce.Job:  map 100% reduce 81%
17/05/09 09:49:52 INFO mapreduce.Job:  map 100% reduce 82%
17/05/09 09:49:55 INFO mapreduce.Job:  map 100% reduce 83%
17/05/09 09:49:58 INFO mapreduce.Job:  map 100% reduce 84%
17/05/09 09:50:01 INFO mapreduce.Job:  map 100% reduce 85%
17/05/09 09:50:07 INFO mapreduce.Job:  map 100% reduce 86%
17/05/09 09:50:13 INFO mapreduce.Job:  map 100% reduce 88%
17/05/09 09:50:28 INFO mapreduce.Job:  map 100% reduce 89%
17/05/09 09:50:31 INFO mapreduce.Job:  map 100% reduce 90%
17/05/09 09:50:34 INFO mapreduce.Job:  map 100% reduce 91%
17/05/09 09:50:37 INFO mapreduce.Job:  map 100% reduce 92%
17/05/09 09:50:55 INFO mapreduce.Job:  map 100% reduce 93%
17/05/09 09:51:17 INFO mapreduce.Job:  map 100% reduce 94%
17/05/09 09:51:20 INFO mapreduce.Job:  map 100% reduce 95%
17/05/09 09:51:47 INFO mapreduce.Job:  map 100% reduce 97%
17/05/09 09:51:56 INFO mapreduce.Job:  map 100% reduce 98%
17/05/09 09:52:10 INFO mapreduce.Job:  map 100% reduce 99%
17/05/09 09:52:17 INFO mapreduce.Job:  map 100% reduce 100%
17/05/09 09:52:23 INFO mapreduce.Job: Job job_1494319855232_0001 completed successfully
17/05/09 09:52:23 INFO mapreduce.Job: Counters: 50
	File System Counters
		FILE: Number of bytes read=4714380417
		FILE: Number of bytes written=9341624749
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=10485808348
		HDFS: Number of bytes written=10485760000
		HDFS: Number of read operations=960
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=8
	Job Counters 
		Launched map tasks=316
		Launched reduce tasks=4
		Data-local map tasks=313
		Rack-local map tasks=3
		Total time spent by all maps in occupied slots (ms)=3270423
		Total time spent by all reduces in occupied slots (ms)=870233
		Total time spent by all map tasks (ms)=3270423
		Total time spent by all reduce tasks (ms)=870233
		Total vcore-seconds taken by all map tasks=3270423
		Total vcore-seconds taken by all reduce tasks=870233
		Total megabyte-seconds taken by all map tasks=3348913152
		Total megabyte-seconds taken by all reduce tasks=891118592
	Map-Reduce Framework
		Map input records=104857600
		Map output records=104857600
		Map output bytes=10695475200
		Map output materialized bytes=4587231386
		Input split bytes=48348
		Combine input records=0
		Combine output records=0
		Reduce input groups=104857600
		Reduce shuffle bytes=4587231386
		Reduce input records=104857600
		Reduce output records=104857600
		Spilled Records=209715200
		Shuffled Maps =1264
		Failed Shuffles=0
		Merged Map outputs=1264
		GC time elapsed (ms)=33063
		CPU time spent (ms)=1530840
		Physical memory (bytes) snapshot=148812881920
		Virtual memory (bytes) snapshot=502327087104
		Total committed heap usage (bytes)=181024063488
	Shuffle Errors
		BAD_ID=0
		CONNECTION=0
		IO_ERROR=0
		WRONG_LENGTH=0
		WRONG_MAP=0
		WRONG_REDUCE=0
	File Input Format Counters 
		Bytes Read=10485760000
	File Output Format Counters 
		Bytes Written=10485760000
17/05/09 09:52:23 INFO terasort.TeraSort: done

real	8m11.795s
user	0m9.664s
sys	0m1.141s
</pre>