<pre>
[littlecong@ip-172-31-37-12 jars]$ time hadoop jar  hadoop-examples.jar teragen -Dmapreduce.job.maps=4 -Ddfs.blocksize=32m 104857600 /user/littlecong/10G
.......
real	6m45.644s
user	0m6.777s
sys	0m0.937s
</pre>
<pre>
[littlecong@ip-172-31-37-12 jars]$ time hadoop jar  hadoop-examples.jar terasort  /user/littlecong/10G /user/littlecong/10G_sorted
</pre>