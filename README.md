# Chapter 10

## Question 1

python3 multi.py -n 1 -L a:30:200 -c -t
ARG seed 0
ARG job_num 3
ARG max_run 100
ARG max_wset 200
ARG job_list a:30:200
ARG affinity 
ARG per_cpu_queues False
ARG num_cpus 1
ARG quantum 10
ARG peek_interval 30
ARG warmup_time 10
ARG cache_size 100
ARG random_order False
ARG trace True
ARG trace_time False
ARG trace_cache False
ARG trace_sched False
ARG compute True

Job name:a run_time:30 working_set_size:200

Scheduler central queue: ['a']

   0   a      
   1   a      
   2   a      
   3   a      
   4   a      
   5   a      
   6   a      
   7   a      
   8   a      
   9   a      
----------
  10   a      
  11   a      
  12   a      
  13   a      
  14   a      
  15   a      
  16   a      
  17   a      
  18   a      
  19   a      
----------
  20   a      
  21   a      
  22   a      
  23   a      
  24   a      
  25   a      
  26   a      
  27   a      
  28   a      
  29   a      

Finished time 30

Per-CPU stats
  CPU 0  utilization 100.00 [ warm 0.00 ]


## Question2
python3 multi.py -n 1 -L a:30:200 -M 300 -c -T
ARG seed 0
ARG job_num 3
ARG max_run 100
ARG max_wset 200
ARG job_list a:30:200
ARG affinity 
ARG per_cpu_queues False
ARG num_cpus 1
ARG quantum 10
ARG peek_interval 30
ARG warmup_time 10
ARG cache_size 300
ARG random_order False
ARG trace False
ARG trace_time True
ARG trace_cache False
ARG trace_sched False
ARG compute True

Job name:a run_time:30 working_set_size:200

Scheduler central queue: ['a']

   0   a [ 29]      
   1   a [ 28]      
   2   a [ 27]      
   3   a [ 26]      
   4   a [ 25]      
   5   a [ 24]      
   6   a [ 23]      
   7   a [ 22]      
   8   a [ 21]      
   9   a [ 20]      
----------------
  10   a [ 18]      
  11   a [ 16]      
  12   a [ 14]      
  13   a [ 12]      
  14   a [ 10]      
  15   a [  8]      
  16   a [  6]      
  17   a [  4]      
  18   a [  2]      
  19   a [  0]      

Finished time 20

Per-CPU stats
  CPU 0  utilization 100.00 [ warm 50.00 ]




## Question3

After 10seconds, when the cache is warmed up, process takes half the time from then on.


## Question4
Cache become warm up aftert 10th CPU time. If I reduce the warmup time, the process takes less time. With increasing warmup time, it takes more time to finish.


## Question5
python3 multi.py  -n 2 -L a:100:100,b:100:50,c:100:50 -c -t -C
ARG seed 0
ARG job_num 3
ARG max_run 100
ARG max_wset 200
ARG job_list a:100:100,b:100:50,c:100:50
ARG affinity 
ARG per_cpu_queues False
ARG num_cpus 2
ARG quantum 10
ARG peek_interval 30
ARG warmup_time 10
ARG cache_size 100
ARG random_order False
ARG trace True
ARG trace_time False
ARG trace_cache True
ARG trace_sched False
ARG compute True

Job name:a run_time:100 working_set_size:100
Job name:b run_time:100 working_set_size:50
Job name:c run_time:100 working_set_size:50

Scheduler central queue: ['a', 'b', 'c']

   0   a cache[   ]     b cache[   ]     
   1   a cache[   ]     b cache[   ]     
   2   a cache[   ]     b cache[   ]     
   3   a cache[   ]     b cache[   ]     
   4   a cache[   ]     b cache[   ]     
   5   a cache[   ]     b cache[   ]     
   6   a cache[   ]     b cache[   ]     
   7   a cache[   ]     b cache[   ]     
   8   a cache[   ]     b cache[   ]     
   9   a cache[w  ]     b cache[ w ]     
---------------------------------------
  10   c cache[w  ]     a cache[ w ]     
  11   c cache[w  ]     a cache[ w ]     
  12   c cache[w  ]     a cache[ w ]     
  13   c cache[w  ]     a cache[ w ]     
  14   c cache[w  ]     a cache[ w ]     
  15   c cache[w  ]     a cache[ w ]     
  16   c cache[w  ]     a cache[ w ]     
  17   c cache[w  ]     a cache[ w ]     
  18   c cache[w  ]     a cache[ w ]     
  19   c cache[  w]     a cache[w  ]     
---------------------------------------
  20   b cache[  w]     c cache[w  ]     
  21   b cache[  w]     c cache[w  ]     
  22   b cache[  w]     c cache[w  ]     
  23   b cache[  w]     c cache[w  ]     
  24   b cache[  w]     c cache[w  ]     
  25   b cache[  w]     c cache[w  ]     
  26   b cache[  w]     c cache[w  ]     
  27   b cache[  w]     c cache[w  ]     
  28   b cache[  w]     c cache[w  ]     
  29   b cache[ ww]     c cache[  w]     
---------------------------------------
  30   a cache[ ww]     b cache[  w]     
  31   a cache[ ww]     b cache[  w]     
  32   a cache[ ww]     b cache[  w]     
  33   a cache[ ww]     b cache[  w]     
  34   a cache[ ww]     b cache[  w]     
  35   a cache[ ww]     b cache[  w]     
  36   a cache[ ww]     b cache[  w]     
  37   a cache[ ww]     b cache[  w]     
  38   a cache[ ww]     b cache[  w]     
  39   a cache[w  ]     b cache[ ww]     
---------------------------------------
  40   c cache[w  ]     a cache[ ww]     
  41   c cache[w  ]     a cache[ ww]     
  42   c cache[w  ]     a cache[ ww]     
  43   c cache[w  ]     a cache[ ww]     
  44   c cache[w  ]     a cache[ ww]     
  45   c cache[w  ]     a cache[ ww]     
  46   c cache[w  ]     a cache[ ww]     
  47   c cache[w  ]     a cache[ ww]     
  48   c cache[w  ]     a cache[ ww]     
  49   c cache[  w]     a cache[w  ]     
---------------------------------------
  50   b cache[  w]     c cache[w  ]     
  51   b cache[  w]     c cache[w  ]     
  52   b cache[  w]     c cache[w  ]     
  53   b cache[  w]     c cache[w  ]     
  54   b cache[  w]     c cache[w  ]     
  55   b cache[  w]     c cache[w  ]     
  56   b cache[  w]     c cache[w  ]     
  57   b cache[  w]     c cache[w  ]     
  58   b cache[  w]     c cache[w  ]     
  59   b cache[ ww]     c cache[  w]     
---------------------------------------
  60   a cache[ ww]     b cache[  w]     
  61   a cache[ ww]     b cache[  w]     
  62   a cache[ ww]     b cache[  w]     
  63   a cache[ ww]     b cache[  w]     
  64   a cache[ ww]     b cache[  w]     
  65   a cache[ ww]     b cache[  w]     
  66   a cache[ ww]     b cache[  w]     
  67   a cache[ ww]     b cache[  w]     
  68   a cache[ ww]     b cache[  w]     
  69   a cache[w  ]     b cache[ ww]     
---------------------------------------
  70   c cache[w  ]     a cache[ ww]     
  71   c cache[w  ]     a cache[ ww]     
  72   c cache[w  ]     a cache[ ww]     
  73   c cache[w  ]     a cache[ ww]     
  74   c cache[w  ]     a cache[ ww]     
  75   c cache[w  ]     a cache[ ww]     
  76   c cache[w  ]     a cache[ ww]     
  77   c cache[w  ]     a cache[ ww]     
  78   c cache[w  ]     a cache[ ww]     
  79   c cache[  w]     a cache[w  ]     
---------------------------------------
  80   b cache[  w]     c cache[w  ]     
  81   b cache[  w]     c cache[w  ]     
  82   b cache[  w]     c cache[w  ]     
  83   b cache[  w]     c cache[w  ]     
  84   b cache[  w]     c cache[w  ]     
  85   b cache[  w]     c cache[w  ]     
  86   b cache[  w]     c cache[w  ]     
  87   b cache[  w]     c cache[w  ]     
  88   b cache[  w]     c cache[w  ]     
  89   b cache[ ww]     c cache[  w]     
---------------------------------------
  90   a cache[ ww]     b cache[  w]     
  91   a cache[ ww]     b cache[  w]     
  92   a cache[ ww]     b cache[  w]     
  93   a cache[ ww]     b cache[  w]     
  94   a cache[ ww]     b cache[  w]     
  95   a cache[ ww]     b cache[  w]     
  96   a cache[ ww]     b cache[  w]     
  97   a cache[ ww]     b cache[  w]     
  98   a cache[ ww]     b cache[  w]     
  99   a cache[w  ]     b cache[ ww]     
---------------------------------------
 100   c cache[w  ]     a cache[ ww]     
 101   c cache[w  ]     a cache[ ww]     
 102   c cache[w  ]     a cache[ ww]     
 103   c cache[w  ]     a cache[ ww]     
 104   c cache[w  ]     a cache[ ww]     
 105   c cache[w  ]     a cache[ ww]     
 106   c cache[w  ]     a cache[ ww]     
 107   c cache[w  ]     a cache[ ww]     
 108   c cache[w  ]     a cache[ ww]     
 109   c cache[  w]     a cache[w  ]     
---------------------------------------
 110   b cache[  w]     c cache[w  ]     
 111   b cache[  w]     c cache[w  ]     
 112   b cache[  w]     c cache[w  ]     
 113   b cache[  w]     c cache[w  ]     
 114   b cache[  w]     c cache[w  ]     
 115   b cache[  w]     c cache[w  ]     
 116   b cache[  w]     c cache[w  ]     
 117   b cache[  w]     c cache[w  ]     
 118   b cache[  w]     c cache[w  ]     
 119   b cache[ ww]     c cache[  w]     
---------------------------------------
 120   a cache[ ww]     b cache[  w]     
 121   a cache[ ww]     b cache[  w]     
 122   a cache[ ww]     b cache[  w]     
 123   a cache[ ww]     b cache[  w]     
 124   a cache[ ww]     b cache[  w]     
 125   a cache[ ww]     b cache[  w]     
 126   a cache[ ww]     b cache[  w]     
 127   a cache[ ww]     b cache[  w]     
 128   a cache[ ww]     b cache[  w]     
 129   a cache[w  ]     b cache[ ww]     
---------------------------------------
 130   c cache[w  ]     a cache[ ww]     
 131   c cache[w  ]     a cache[ ww]     
 132   c cache[w  ]     a cache[ ww]     
 133   c cache[w  ]     a cache[ ww]     
 134   c cache[w  ]     a cache[ ww]     
 135   c cache[w  ]     a cache[ ww]     
 136   c cache[w  ]     a cache[ ww]     
 137   c cache[w  ]     a cache[ ww]     
 138   c cache[w  ]     a cache[ ww]     
 139   c cache[  w]     a cache[w  ]     
---------------------------------------
 140   b cache[  w]     c cache[w  ]     
 141   b cache[  w]     c cache[w  ]     
 142   b cache[  w]     c cache[w  ]     
 143   b cache[  w]     c cache[w  ]     
 144   b cache[  w]     c cache[w  ]     
 145   b cache[  w]     c cache[w  ]     
 146   b cache[  w]     c cache[w  ]     
 147   b cache[  w]     c cache[w  ]     
 148   b cache[  w]     c cache[w  ]     
 149   b cache[ ww]     c cache[  w]     

Finished time 150

Per-CPU stats
  CPU 0  utilization 100.00 [ warm 0.00 ]
  CPU 1  utilization 100.00 [ warm 0.00 ]


Because of round robin scheduling, and no cache affinity, cache doesn't get used at all.

## Question6

python3 multi.py -n 2 -L a:100:100,b:100:50,c:100:50 -A a:0,b:1,c:1 -c -t -C
ARG seed 0
ARG job_num 3
ARG max_run 100
ARG max_wset 200
ARG job_list a:100:100,b:100:50,c:100:50
ARG affinity a:0,b:1,c:1
ARG per_cpu_queues False
ARG num_cpus 2
ARG quantum 10
ARG peek_interval 30
ARG warmup_time 10
ARG cache_size 100
ARG random_order False
ARG trace True
ARG trace_time False
ARG trace_cache True
ARG trace_sched False
ARG compute True

Job name:a run_time:100 working_set_size:100
Job name:b run_time:100 working_set_size:50
Job name:c run_time:100 working_set_size:50

Scheduler central queue: ['a', 'b', 'c']

   0   a cache[   ]     b cache[   ]     
   1   a cache[   ]     b cache[   ]     
   2   a cache[   ]     b cache[   ]     
   3   a cache[   ]     b cache[   ]     
   4   a cache[   ]     b cache[   ]     
   5   a cache[   ]     b cache[   ]     
   6   a cache[   ]     b cache[   ]     
   7   a cache[   ]     b cache[   ]     
   8   a cache[   ]     b cache[   ]     
   9   a cache[w  ]     b cache[ w ]     
---------------------------------------
  10   a cache[w  ]     c cache[ w ]     
  11   a cache[w  ]     c cache[ w ]     
  12   a cache[w  ]     c cache[ w ]     
  13   a cache[w  ]     c cache[ w ]     
  14   a cache[w  ]     c cache[ w ]     
  15   a cache[w  ]     c cache[ w ]     
  16   a cache[w  ]     c cache[ w ]     
  17   a cache[w  ]     c cache[ w ]     
  18   a cache[w  ]     c cache[ w ]     
  19   a cache[w  ]     c cache[ ww]     
---------------------------------------
  20   a cache[w  ]     b cache[ ww]     
  21   a cache[w  ]     b cache[ ww]     
  22   a cache[w  ]     b cache[ ww]     
  23   a cache[w  ]     b cache[ ww]     
  24   a cache[w  ]     b cache[ ww]     
  25   a cache[w  ]     b cache[ ww]     
  26   a cache[w  ]     b cache[ ww]     
  27   a cache[w  ]     b cache[ ww]     
  28   a cache[w  ]     b cache[ ww]     
  29   a cache[w  ]     b cache[ ww]     
---------------------------------------
  30   a cache[w  ]     c cache[ ww]     
  31   a cache[w  ]     c cache[ ww]     
  32   a cache[w  ]     c cache[ ww]     
  33   a cache[w  ]     c cache[ ww]     
  34   a cache[w  ]     c cache[ ww]     
  35   a cache[w  ]     c cache[ ww]     
  36   a cache[w  ]     c cache[ ww]     
  37   a cache[w  ]     c cache[ ww]     
  38   a cache[w  ]     c cache[ ww]     
  39   a cache[w  ]     c cache[ ww]     
---------------------------------------
  40   a cache[w  ]     b cache[ ww]     
  41   a cache[w  ]     b cache[ ww]     
  42   a cache[w  ]     b cache[ ww]     
  43   a cache[w  ]     b cache[ ww]     
  44   a cache[w  ]     b cache[ ww]     
  45   a cache[w  ]     b cache[ ww]     
  46   a cache[w  ]     b cache[ ww]     
  47   a cache[w  ]     b cache[ ww]     
  48   a cache[w  ]     b cache[ ww]     
  49   a cache[w  ]     b cache[ ww]     
---------------------------------------
  50   a cache[w  ]     c cache[ ww]     
  51   a cache[w  ]     c cache[ ww]     
  52   a cache[w  ]     c cache[ ww]     
  53   a cache[w  ]     c cache[ ww]     
  54   a cache[w  ]     c cache[ ww]     
  55   - cache[w  ]     c cache[ ww]     
  56   - cache[w  ]     c cache[ ww]     
  57   - cache[w  ]     c cache[ ww]     
  58   - cache[w  ]     c cache[ ww]     
  59   - cache[w  ]     c cache[ ww]     
---------------------------------------
  60   - cache[w  ]     b cache[ ww]     
  61   - cache[w  ]     b cache[ ww]     
  62   - cache[w  ]     b cache[ ww]     
  63   - cache[w  ]     b cache[ ww]     
  64   - cache[w  ]     b cache[ ww]     
  65   - cache[w  ]     b cache[ ww]     
  66   - cache[w  ]     b cache[ ww]     
  67   - cache[w  ]     b cache[ ww]     
  68   - cache[w  ]     b cache[ ww]     
  69   - cache[w  ]     b cache[ ww]     
---------------------------------------
  70   - cache[w  ]     c cache[ ww]     
  71   - cache[w  ]     c cache[ ww]     
  72   - cache[w  ]     c cache[ ww]     
  73   - cache[w  ]     c cache[ ww]     
  74   - cache[w  ]     c cache[ ww]     
  75   - cache[w  ]     c cache[ ww]     
  76   - cache[w  ]     c cache[ ww]     
  77   - cache[w  ]     c cache[ ww]     
  78   - cache[w  ]     c cache[ ww]     
  79   - cache[w  ]     c cache[ ww]     
---------------------------------------
  80   - cache[w  ]     b cache[ ww]     
  81   - cache[w  ]     b cache[ ww]     
  82   - cache[w  ]     b cache[ ww]     
  83   - cache[w  ]     b cache[ ww]     
  84   - cache[w  ]     b cache[ ww]     
  85   - cache[w  ]     b cache[ ww]     
  86   - cache[w  ]     b cache[ ww]     
  87   - cache[w  ]     b cache[ ww]     
  88   - cache[w  ]     b cache[ ww]     
  89   - cache[w  ]     b cache[ ww]     
---------------------------------------
  90   - cache[w  ]     c cache[ ww]     
  91   - cache[w  ]     c cache[ ww]     
  92   - cache[w  ]     c cache[ ww]     
  93   - cache[w  ]     c cache[ ww]     
  94   - cache[w  ]     c cache[ ww]     
  95   - cache[w  ]     c cache[ ww]     
  96   - cache[w  ]     c cache[ ww]     
  97   - cache[w  ]     c cache[ ww]     
  98   - cache[w  ]     c cache[ ww]     
  99   - cache[w  ]     c cache[ ww]     
---------------------------------------
 100   - cache[w  ]     b cache[ ww]     
 101   - cache[w  ]     b cache[ ww]     
 102   - cache[w  ]     b cache[ ww]     
 103   - cache[w  ]     b cache[ ww]     
 104   - cache[w  ]     b cache[ ww]     
 105   - cache[w  ]     c cache[ ww]     
 106   - cache[w  ]     c cache[ ww]     
 107   - cache[w  ]     c cache[ ww]     
 108   - cache[w  ]     c cache[ ww]     
 109   - cache[w  ]     c cache[ ww]     

Finished time 110

Per-CPU stats
  CPU 0  utilization 50.00 [ warm 40.91 ]
  CPU 1  utilization 100.00 [ warm 81.82 ]


it does better because of Cache affinity

## Question7
When the number of CPU is 3 and the cache size is 100, I can see super-linear speedup in effect. With less than 3 CPU, cache is never used because of CPU affinity.

## Question8
Per cpu scheduling makes use of cache more effeciently. In fact, it works better than hand-controlled affinity because with per cpu scheduling, CPU can look for jobs when its idling.

With lower peek interval, it works better.

## Question9


python3 multi.py -n 2 -s 1 -c -T
ARG seed 1
ARG job_num 3
ARG max_run 100
ARG max_wset 200
ARG job_list 
ARG affinity 
ARG per_cpu_queues False
ARG num_cpus 2
ARG quantum 10
ARG peek_interval 30
ARG warmup_time 10
ARG cache_size 100
ARG random_order False
ARG trace False
ARG trace_time True
ARG trace_cache False
ARG trace_sched False
ARG compute True

Job name:0 run_time:10 working_set_size:160
Job name:1 run_time:70 working_set_size:50
Job name:2 run_time:40 working_set_size:80

Scheduler central queue: ['0', '1', '2']

   0   0 [  9]      1 [ 69]      
   1   0 [  8]      1 [ 68]      
   2   0 [  7]      1 [ 67]      
   3   0 [  6]      1 [ 66]      
   4   0 [  5]      1 [ 65]      
   5   0 [  4]      1 [ 64]      
   6   0 [  3]      1 [ 63]      
   7   0 [  2]      1 [ 62]      
   8   0 [  1]      1 [ 61]      
   9   0 [  0]      1 [ 60]      
-----------------------------
  10   2 [ 39]      1 [ 58]      
  11   2 [ 38]      1 [ 56]      
  12   2 [ 37]      1 [ 54]      
  13   2 [ 36]      1 [ 52]      
  14   2 [ 35]      1 [ 50]      
  15   2 [ 34]      1 [ 48]      
  16   2 [ 33]      1 [ 46]      
  17   2 [ 32]      1 [ 44]      
  18   2 [ 31]      1 [ 42]      
  19   2 [ 30]      1 [ 40]      
-----------------------------
  20   2 [ 28]      1 [ 38]      
  21   2 [ 26]      1 [ 36]      
  22   2 [ 24]      1 [ 34]      
  23   2 [ 22]      1 [ 32]      
  24   2 [ 20]      1 [ 30]      
  25   2 [ 18]      1 [ 28]      
  26   2 [ 16]      1 [ 26]      
  27   2 [ 14]      1 [ 24]      
  28   2 [ 12]      1 [ 22]      
  29   2 [ 10]      1 [ 20]      
-----------------------------
  30   2 [  8]      1 [ 18]      
  31   2 [  6]      1 [ 16]      
  32   2 [  4]      1 [ 14]      
  33   2 [  2]      1 [ 12]      
  34   2 [  0]      1 [ 10]      
  35   - [   ]      1 [  8]      
  36   - [   ]      1 [  6]      
  37   - [   ]      1 [  4]      
  38   - [   ]      1 [  2]      
  39   - [   ]      1 [  0]      

Finished time 40

Per-CPU stats
  CPU 0  utilization 87.50 [ warm 37.50 ]
  CPU 1  utilization 100.00 [ warm 75.00 ]



# Chapter 13


## Question 2

free -m
               total        used        free      shared  buff/cache   available
Mem:            1849         138        1421           0         289        1570
Swap:              0           0           0


## Question 3


## Question 4

Kernel kills the process with OOM.


 oom-kill:constraint=CONSTRAINT_NONE,nodemask=(null),cpuset=/,mems_allowed=0,global_oom,task_memcg=/user.slice/user-1000.slice/session-1.scope,task=a.out,pid=32037,uid=1000
[ 2826.189173] Out of memory: Killed process 32037 (a.out) total-vm:1853656kB, anon-rss:1713160kB, file-rss:8kB, shmem-rss:0kB, UID:1000 pgtables:3396kB oom_score_adj:0


## Question 5


## Question 6

pmap 32134
32134:   ./a.out 50 100
0000000000400000      4K r-x-- a.out
000000000041f000      4K r---- a.out
0000000000420000      4K rw--- a.out
000000002f16e000    132K rw---   [ anon ]
0000ffff92d19000  51204K rw---   [ anon ]
0000ffff95f1a000   1608K r-x-- libc.so.6
0000ffff960ac000    104K ----- libc.so.6
0000ffff960c6000     16K r---- libc.so.6
0000ffff960ca000      8K rw--- libc.so.6
0000ffff960cc000     48K rw---   [ anon ]
0000ffff960d8000    164K r-x-- ld-linux-aarch64.so.1
0000ffff9610b000      8K rw---   [ anon ]
0000ffff96113000      8K r----   [ anon ]
0000ffff96115000      4K r-x--   [ anon ]
0000ffff96116000      8K r---- ld-linux-aarch64.so.1
0000ffff96118000      8K rw--- ld-linux-aarch64.so.1
0000ffffda77e000    132K rw---   [ stack ]
 total            53464K

## Question 7
Lots of different entities make up a modern address space.

[ec2-user@ip-172-31-50-182 ~]$ pmap -x 32134
32134:   ./a.out 50 100
Address           Kbytes     RSS   Dirty Mode  Mapping
0000000000400000       4       4       0 r-x-- a.out
000000000041f000       4       4       4 r---- a.out
0000000000420000       4       4       4 rw--- a.out
000000002f16e000     132       4       4 rw---   [ anon ]
0000ffff92d19000   51204   51204   51204 rw---   [ anon ]
0000ffff95f1a000    1608    1068       0 r-x-- libc.so.6
0000ffff960ac000     104       0       0 ----- libc.so.6
0000ffff960c6000      16      16      16 r---- libc.so.6
0000ffff960ca000       8       8       8 rw--- libc.so.6
0000ffff960cc000      48      16      16 rw---   [ anon ]
0000ffff960d8000     164     160       0 r-x-- ld-linux-aarch64.so.1
0000ffff9610b000       8       8       8 rw---   [ anon ]
0000ffff96113000       8       0       0 r----   [ anon ]
0000ffff96115000       4       4       0 r-x--   [ anon ]
0000ffff96116000       8       8       8 r---- ld-linux-aarch64.so.1
0000ffff96118000       8       8       8 rw--- ld-linux-aarch64.so.1
0000ffffda77e000     132      12      12 rw---   [ stack ]

## Question 8

Yes it does.



# Chapter 14
 
## Question 1

[ec2-user@ip-172-31-50-182 ~]$ ./null
Segmentation fault (core dumped)


## Question 2

(gdb) run
Starting program: /home/ec2-user/null 
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib64/libthread_db.so.1".

Program received signal SIGSEGV, Segmentation fault.
0x00000000004006b4 in main (argc=1, argv=0xfffffffff378) at null.c:7
7	    printf("%d\n", *x);


## Question 3
 valgrind --leak-check=yes ./null
==34439== Memcheck, a memory error detector
==34439== Copyright (C) 2002-2022, and GNU GPL'd, by Julian Seward et al.
==34439== Using Valgrind-3.19.0 and LibVEX; rerun with -h for copyright info
==34439== Command: ./null
==34439== 
==34439== Invalid read of size 4
==34439==    at 0x4006B4: main (null.c:7)
==34439==  Address 0x0 is not stack'd, malloc'd or (recently) free'd
==34439== 
==34439== 
==34439== Process terminating with default action of signal 11 (SIGSEGV): dumping core
==34439==  Access not within mapped region at address 0x0
==34439==    at 0x4006B4: main (null.c:7)
==34439==  If you believe this happened as a result of a stack
==34439==  overflow in your program's main thread (unlikely but
==34439==  possible), you can try to increase the size of the
==34439==  main thread stack using the --main-stacksize= flag.
==34439==  The main thread stack size used in this run was 10485760.
==34439== 
==34439== HEAP SUMMARY:
==34439==     in use at exit: 4 bytes in 1 blocks
==34439==   total heap usage: 1 allocs, 0 frees, 4 bytes allocated
==34439== 
==34439== 4 bytes in 1 blocks are definitely lost in loss record 1 of 1
==34439==    at 0x486D440: calloc (vg_replace_malloc.c:1328)
==34439==    by 0x4006A7: main (null.c:5)
==34439== 
==34439== LEAK SUMMARY:
==34439==    definitely lost: 4 bytes in 1 blocks
==34439==    indirectly lost: 0 bytes in 0 blocks
==34439==      possibly lost: 0 bytes in 0 blocks
==34439==    still reachable: 0 bytes in 0 blocks
==34439==         suppressed: 0 bytes in 0 blocks
==34439== 
==34439== For lists of detected and suppressed errors, rerun with: -s
==34439== ERROR SUMMARY: 2 errors from 2 contexts (suppressed: 0 from 0)
Segmentation fault (core dumped)


## Question 4

Reading symbols from forget...
(gdb) run
Starting program: /home/ec2-user/forget 
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib64/libthread_db.so.1".
1
[Inferior 1 (process 34545) exited normally]


--------------



valgrind --leak-check=yes ./forget 
==34548== Memcheck, a memory error detector
==34548== Copyright (C) 2002-2022, and GNU GPL'd, by Julian Seward et al.
==34548== Using Valgrind-3.19.0 and LibVEX; rerun with -h for copyright info
==34548== Command: ./forget
==34548== 
1
==34548== 
==34548== HEAP SUMMARY:
==34548==     in use at exit: 4 bytes in 1 blocks
==34548==   total heap usage: 2 allocs, 1 frees, 1,028 bytes allocated
==34548== 
==34548== 4 bytes in 1 blocks are definitely lost in loss record 1 of 1
==34548==    at 0x48681CC: malloc (vg_replace_malloc.c:381)
==34548==    by 0x400623: main (forget_free.c:5)
==34548== 
==34548== LEAK SUMMARY:
==34548==    definitely lost: 4 bytes in 1 blocks
==34548==    indirectly lost: 0 bytes in 0 blocks
==34548==      possibly lost: 0 bytes in 0 blocks
==34548==    still reachable: 0 bytes in 0 blocks
==34548==         suppressed: 0 bytes in 0 blocks
==34548== 
==34548== For lists of detected and suppressed errors, rerun with: -s
==34548== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 0 from 0)
## Question 5

Reading symbols from 100...
(gdb) run
Starting program: /home/ec2-user/100 
[Thread debugging using libthread_db enabled]
Using host libthread_db library "/lib64/libthread_db.so.1".
[Inferior 1 (process 34699) exited normally]

----------------
valgrind --leak-check=yes ./100
==34701== Memcheck, a memory error detector
==34701== Copyright (C) 2002-2022, and GNU GPL'd, by Julian Seward et al.
==34701== Using Valgrind-3.19.0 and LibVEX; rerun with -h for copyright info
==34701== Command: ./100
==34701== 
==34701== Invalid write of size 4
==34701==    at 0x400630: main (100.c:6)
==34701==  Address 0x4a521d0 is 224 bytes inside an unallocated block of size 4,194,032 in arena "client"
==34701== 
==34701== 
==34701== HEAP SUMMARY:
==34701==     in use at exit: 0 bytes in 0 blocks
==34701==   total heap usage: 1 allocs, 1 frees, 100 bytes allocated
==34701== 
==34701== All heap blocks were freed -- no leaks are possible
==34701== 
==34701== For lists of detected and suppressed errors, rerun with: -s
==34701== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 0 from 0)

## Question 6
yes the program runs and prints garbage value.


valgrind --leak-check=yes ./free
==35375== Memcheck, a memory error detector
==35375== Copyright (C) 2002-2022, and GNU GPL'd, by Julian Seward et al.
==35375== Using Valgrind-3.19.0 and LibVEX; rerun with -h for copyright info
==35375== Command: ./free
==35375== 
==35375== Invalid read of size 4
==35375==    at 0x4006B4: main (free_then_print.c:8)
==35375==  Address 0x4a52040 is 0 bytes inside a block of size 100 free'd
==35375==    at 0x486AC88: free (vg_replace_malloc.c:872)
==35375==    by 0x4006AF: main (free_then_print.c:6)
==35375==  Block was alloc'd at
==35375==    at 0x48681CC: malloc (vg_replace_malloc.c:381)
==35375==    by 0x4006A3: main (free_then_print.c:5)
==35375== 
0
==35375== 
==35375== HEAP SUMMARY:
==35375==     in use at exit: 0 bytes in 0 blocks
==35375==   total heap usage: 2 allocs, 2 frees, 1,124 bytes allocated
==35375== 
==35375== All heap blocks were freed -- no leaks are possible
==35375== 
==35375== For lists of detected and suppressed errors, rerun with: -s
==35375== ERROR SUMMARY: 1 errors from 1 contexts (suppressed: 0 from 0)
## Question 7
 Compilation shows error. Also the program crashes.


## Question 8
valgrind --leak-check=yes ./vector 
==35719== Memcheck, a memory error detector
==35719== Copyright (C) 2002-2022, and GNU GPL'd, by Julian Seward et al.
==35719== Using Valgrind-3.19.0 and LibVEX; rerun with -h for copyright info
==35719== Command: ./vector
==35719== 
first value: 4
second value: 5
third value: 6
size: 3
capacity: 4
==35719== 
==35719== HEAP SUMMARY:
==35719==     in use at exit: 0 bytes in 0 blocks
==35719==   total heap usage: 4 allocs, 4 frees, 1,052 bytes allocated
==35719== 
==35719== All heap blocks were freed -- no leaks are possible
==35719== 
==35719== For lists of detected and suppressed errors, rerun with: -s
==35719== ERROR SUMMARY: 0 errors from 0 contexts (suppressed: 0 from 0)

