# The best params should be

```
map.java.opts.max.heap=1638
reduce.java.opts.max.heap=1638
job.maps=4
map.memory.mb=2048
job.reduces=4
reduce.memory.mb=2048

real    1m49.289s
user    0m6.444s
sys     0m0.868s

real    3m40.256s
user    0m8.304s
sys     0m0.839s
```

or
```
map.java.opts.max.heap=1638
reduce.java.opts.max.heap=1638
job.maps=8
map.memory.mb=2048
job.reduces=8
reduce.memory.mb=2048

real    1m50.207s
user    0m6.141s
sys     0m0.825s

real    3m29.590s
user    0m8.621s
sys     0m0.958s

```
# Here is all the result

```
[hdfs@ip-172-31-37-12 ~]$ ./YARNtest.sh 
Testing loop started on Wed May 10 02:30:29 UTC 2017
map.java.opts.max.heap=409
reduce.java.opts.max.heap=409
job.maps=4
map.memory.mb=512
job.reduces=4
reduce.memory.mb=512

real    2m29.624s
user    0m6.150s
sys     0m0.787s

real    3m18.672s
user    0m8.010s
sys     0m0.850s
Deleted /results/tg-10GB-4-4-512
Deleted /results/ts-10GB-4-4-512
map.java.opts.max.heap=819
reduce.java.opts.max.heap=819
job.maps=4
map.memory.mb=1024
job.reduces=4
reduce.memory.mb=1024

real    2m21.638s
user    0m6.026s
sys     0m0.777s

real    3m14.519s
user    0m8.576s
sys     0m0.892s
Deleted /results/tg-10GB-4-4-1024
Deleted /results/ts-10GB-4-4-1024
map.java.opts.max.heap=1638
reduce.java.opts.max.heap=1638
job.maps=4
map.memory.mb=2048
job.reduces=4
reduce.memory.mb=2048

real    1m49.289s
user    0m6.444s
sys     0m0.868s

real    3m40.256s
user    0m8.304s
sys     0m0.839s
Deleted /results/tg-10GB-4-4-2048
Deleted /results/ts-10GB-4-4-2048
map.java.opts.max.heap=409
reduce.java.opts.max.heap=409
job.maps=4
map.memory.mb=512
job.reduces=8
reduce.memory.mb=512

real    2m57.334s
user    0m6.106s
sys     0m0.819s

real    2m22.252s
user    0m8.424s
sys     0m0.891s
Deleted /results/tg-10GB-4-8-512
Deleted /results/ts-10GB-4-8-512
map.java.opts.max.heap=819
reduce.java.opts.max.heap=819
job.maps=4
map.memory.mb=1024
job.reduces=8
reduce.memory.mb=1024

real    2m27.969s
user    0m5.888s
sys     0m0.807s

real    2m43.088s
user    0m8.158s
sys     0m0.825s
Deleted /results/tg-10GB-4-8-1024
Deleted /results/ts-10GB-4-8-1024
map.java.opts.max.heap=1638
reduce.java.opts.max.heap=1638
job.maps=4
map.memory.mb=2048
job.reduces=8
reduce.memory.mb=2048

real    2m4.745s
user    0m6.253s
sys     0m0.833s

real    4m11.483s
user    0m8.530s
sys     0m0.932s
Deleted /results/tg-10GB-4-8-2048
Deleted /results/ts-10GB-4-8-2048
map.java.opts.max.heap=409
reduce.java.opts.max.heap=409
job.maps=8
map.memory.mb=512
job.reduces=4
reduce.memory.mb=512

real    2m30.099s
user    0m6.369s
sys     0m0.757s

real    3m2.342s
user    0m8.505s
sys     0m0.830s
Deleted /results/tg-10GB-8-4-512
Deleted /results/ts-10GB-8-4-512
map.java.opts.max.heap=819
reduce.java.opts.max.heap=819
job.maps=8
map.memory.mb=1024
job.reduces=4
reduce.memory.mb=1024

real    2m34.632s
user    0m6.174s
sys     0m0.766s

real    3m1.552s
user    0m8.180s
sys     0m0.832s
Deleted /results/tg-10GB-8-4-1024
Deleted /results/ts-10GB-8-4-1024
map.java.opts.max.heap=1638
reduce.java.opts.max.heap=1638
job.maps=8
map.memory.mb=2048
job.reduces=4
reduce.memory.mb=2048

real    2m2.614s
user    0m5.919s
sys     0m0.715s

real    3m56.634s
user    0m8.572s
sys     0m0.892s
Deleted /results/tg-10GB-8-4-2048
Deleted /results/ts-10GB-8-4-2048
map.java.opts.max.heap=409
reduce.java.opts.max.heap=409
job.maps=8
map.memory.mb=512
job.reduces=8
reduce.memory.mb=512

real    2m9.677s
user    0m6.160s
sys     0m0.808s

real    2m49.452s
user    0m7.739s
sys     0m0.821s
Deleted /results/tg-10GB-8-8-512
Deleted /results/ts-10GB-8-8-512
map.java.opts.max.heap=819
reduce.java.opts.max.heap=819
job.maps=8
map.memory.mb=1024
job.reduces=8
reduce.memory.mb=1024

real    2m12.865s
user    0m6.333s
sys     0m0.888s

real    2m54.602s
user    0m8.222s
sys     0m0.772s
Deleted /results/tg-10GB-8-8-1024
Deleted /results/ts-10GB-8-8-1024
map.java.opts.max.heap=1638
reduce.java.opts.max.heap=1638
job.maps=8
map.memory.mb=2048
job.reduces=8
reduce.memory.mb=2048

real    1m50.207s
user    0m6.141s
sys     0m0.825s

real    3m29.590s
user    0m8.621s
sys     0m0.958s
Deleted /results/tg-10GB-8-8-2048
Deleted /results/ts-10GB-8-8-2048
Testing loop ended on Wed May 10 03:37:58 UTC 2017
```