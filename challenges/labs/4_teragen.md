# teragen
```
[zhou@ip-172-31-37-248 jars]$ cd /opt/cloudera/parcels/CDH/jars
[zhou@ip-172-31-37-248 jars]$ time hadoop jar  hadoop-examples.jar teragen \
>    -Dmapreduce.job.maps=6 \
>    -Ddfs.blocksize=64m \
>    -Dmapreduce.map.memory.mb=1024 \
>    65536000 /user/zhou/tgen
17/05/12 02:38:47 INFO client.RMProxy: Connecting to ResourceManager at ip-172-31-37-248.us-west-2.compute.internal/172.31.37.248:8032
17/05/12 02:38:48 INFO terasort.TeraSort: Generating 65536000 using 6
17/05/12 02:38:48 INFO mapreduce.JobSubmitter: number of splits:6
17/05/12 02:38:48 INFO mapreduce.JobSubmitter: Submitting tokens for job: job_1494554979145_0002
17/05/12 02:38:48 INFO impl.YarnClientImpl: Submitted application application_1494554979145_0002
17/05/12 02:38:48 INFO mapreduce.Job: The url to track the job: http://ip-172-31-37-248.us-west-2.compute.internal:8088/proxy/application_1494554979145_0002/
17/05/12 02:38:48 INFO mapreduce.Job: Running job: job_1494554979145_0002
17/05/12 02:38:56 INFO mapreduce.Job: Job job_1494554979145_0002 running in uber mode : false
17/05/12 02:38:56 INFO mapreduce.Job:  map 0% reduce 0%
17/05/12 02:39:09 INFO mapreduce.Job:  map 6% reduce 0%
17/05/12 02:39:10 INFO mapreduce.Job:  map 18% reduce 0%
17/05/12 02:39:12 INFO mapreduce.Job:  map 20% reduce 0%
17/05/12 02:39:13 INFO mapreduce.Job:  map 24% reduce 0%
17/05/12 02:39:15 INFO mapreduce.Job:  map 26% reduce 0%
17/05/12 02:39:16 INFO mapreduce.Job:  map 29% reduce 0%
17/05/12 02:39:18 INFO mapreduce.Job:  map 31% reduce 0%
17/05/12 02:39:19 INFO mapreduce.Job:  map 34% reduce 0%
17/05/12 02:39:21 INFO mapreduce.Job:  map 36% reduce 0%
17/05/12 02:39:22 INFO mapreduce.Job:  map 40% reduce 0%
17/05/12 02:39:24 INFO mapreduce.Job:  map 41% reduce 0%
17/05/12 02:39:25 INFO mapreduce.Job:  map 44% reduce 0%
17/05/12 02:39:27 INFO mapreduce.Job:  map 46% reduce 0%
17/05/12 02:39:28 INFO mapreduce.Job:  map 49% reduce 0%
17/05/12 02:39:30 INFO mapreduce.Job:  map 50% reduce 0%
17/05/12 02:39:31 INFO mapreduce.Job:  map 53% reduce 0%
17/05/12 02:39:33 INFO mapreduce.Job:  map 54% reduce 0%
17/05/12 02:39:34 INFO mapreduce.Job:  map 58% reduce 0%
17/05/12 02:39:36 INFO mapreduce.Job:  map 59% reduce 0%
17/05/12 02:39:37 INFO mapreduce.Job:  map 62% reduce 0%
17/05/12 02:39:39 INFO mapreduce.Job:  map 63% reduce 0%
17/05/12 02:39:40 INFO mapreduce.Job:  map 65% reduce 0%
17/05/12 02:39:42 INFO mapreduce.Job:  map 66% reduce 0%
17/05/12 02:39:43 INFO mapreduce.Job:  map 68% reduce 0%
17/05/12 02:39:44 INFO mapreduce.Job:  map 69% reduce 0%
17/05/12 02:39:45 INFO mapreduce.Job:  map 70% reduce 0%
17/05/12 02:39:46 INFO mapreduce.Job:  map 72% reduce 0%
17/05/12 02:39:47 INFO mapreduce.Job:  map 73% reduce 0%
17/05/12 02:39:48 INFO mapreduce.Job:  map 74% reduce 0%
17/05/12 02:39:49 INFO mapreduce.Job:  map 76% reduce 0%
17/05/12 02:39:50 INFO mapreduce.Job:  map 77% reduce 0%
17/05/12 02:39:51 INFO mapreduce.Job:  map 78% reduce 0%
17/05/12 02:39:52 INFO mapreduce.Job:  map 80% reduce 0%
17/05/12 02:39:53 INFO mapreduce.Job:  map 81% reduce 0%
17/05/12 02:39:54 INFO mapreduce.Job:  map 83% reduce 0%
17/05/12 02:39:55 INFO mapreduce.Job:  map 84% reduce 0%
17/05/12 02:39:56 INFO mapreduce.Job:  map 85% reduce 0%
17/05/12 02:39:57 INFO mapreduce.Job:  map 86% reduce 0%
17/05/12 02:39:58 INFO mapreduce.Job:  map 87% reduce 0%
17/05/12 02:39:59 INFO mapreduce.Job:  map 88% reduce 0%
17/05/12 02:40:00 INFO mapreduce.Job:  map 89% reduce 0%
17/05/12 02:40:01 INFO mapreduce.Job:  map 90% reduce 0%
17/05/12 02:40:02 INFO mapreduce.Job:  map 91% reduce 0%
17/05/12 02:40:03 INFO mapreduce.Job:  map 92% reduce 0%
17/05/12 02:40:04 INFO mapreduce.Job:  map 95% reduce 0%
17/05/12 02:40:05 INFO mapreduce.Job:  map 96% reduce 0%
17/05/12 02:40:07 INFO mapreduce.Job:  map 99% reduce 0%
17/05/12 02:40:09 INFO mapreduce.Job:  map 100% reduce 0%
17/05/12 02:40:09 INFO mapreduce.Job: Job job_1494554979145_0002 completed successfully
17/05/12 02:40:09 INFO mapreduce.Job: Counters: 31
	File System Counters
		FILE: Number of bytes read=0
		FILE: Number of bytes written=741168
		FILE: Number of read operations=0
		FILE: Number of large read operations=0
		FILE: Number of write operations=0
		HDFS: Number of bytes read=511
		HDFS: Number of bytes written=6553600000
		HDFS: Number of read operations=24
		HDFS: Number of large read operations=0
		HDFS: Number of write operations=12
	Job Counters 
		Launched map tasks=6
		Other local map tasks=6
		Total time spent by all maps in occupied slots (ms)=407508
		Total time spent by all reduces in occupied slots (ms)=0
		Total time spent by all map tasks (ms)=407508
		Total vcore-seconds taken by all map tasks=407508
		Total megabyte-seconds taken by all map tasks=417288192
	Map-Reduce Framework
		Map input records=65536000
		Map output records=65536000
		Input split bytes=511
		Spilled Records=0
		Failed Shuffles=0
		Merged Map outputs=0
		GC time elapsed (ms)=1241
		CPU time spent (ms)=121000
		Physical memory (bytes) snapshot=2032041984
		Virtual memory (bytes) snapshot=9398034432
		Total committed heap usage (bytes)=2043674624
	org.apache.hadoop.examples.terasort.TeraGen$Counters
		CHECKSUM=140750829423462787
	File Input Format Counters 
		Bytes Read=0
	File Output Format Counters 
		Bytes Written=6553600000

real	1m25.142s
user	0m6.020s
sys	0m0.697s
```