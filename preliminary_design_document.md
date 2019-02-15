## 1.1 - Description of modification/addition to Linux
For our semester project, our group intends to implement a new scheduling algorithm for the I/O scheduler. We want to implement the ‘shortest seek time first’ algorithm, with the distance being related to the current location of the disk head.

An explanation of the shortest-seek-time-first algorithm may be as follows:

Suppose our input/output head were located on track 50, and we had track requests at locations 95, 180, 34, 119, 11, 123, 62, 64.

Our algorithm would travel address the thread heads as such:

50 -> 62 ->64 -> 34 -> 11 -> 95 -> 119 -> 123 -> 180

## 1.2 - Rationale as to why this is a good idea, or what the good points of it are
Presently, the Linux disk scheduler operates using the Budget Fair Queueing algorithm. Each process is assigned a fraction of the disk throughput. The primary benefit to this implementation is maximized resource allocation. A potential cost to this implementation is throughput since I/O processes might require different times to complete. Budget Fair Queueing attempts to increase this throughput by distributing the processes independent of device parameters and random requests, solely focusing on the I/O processes as desired. Our group believes, however, another way to maximize throughput is by implementing another I/O scheduling algorithm: shortest seek time first.

Shortest seek time first services I/O requests in order of increasing distance from the current location of the disk head. The seek time of every request would be calculated in advance in a queue, and these requests would be scheduled according to their calculated seek time. Our group believes this will increase the throughput of I/O servicing by decreasing the average response time needed for a thread.

**Sources:** 
* https://algo.ing.unimo.it/people/paolo/disk_sched/description.php
* https://www.geeksforgeeks.org/disk-scheduling-algorithms/

## 1.3 - Preliminary list of [possible] Linux modules that will be modified/affected
```linux/block/bfq-iosched.c```

## 1.4 - Preliminary list of any new modules that you will produce [or 'Not Applicable' if there are none]

Not applicable 