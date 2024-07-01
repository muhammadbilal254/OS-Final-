# OS Final Exam

## Disk Scheduling
Disk scheduling is a technique operating systems use to manage the
order in which disk I/O (input/output) requests are processed.
Disk scheduling is also known as I/O Scheduling.
The main goals of disk scheduling are to optimize
the performance of disk operations, reduce the time
it takes to access data and improve overall system efficiency.


### Important Terms in Disk Scheduling

- Seek Time: The time taken locating the disk arm (reading/writing) to a specified track where the read write request will be satisfied.    

- Rotational Latency: The time it takes for the desired sector of the disk to rotate under the read-write head.

- Transfer Time: The time it takes to actually transfer the data once the read-write head is positioned correctly.

- Disk Access Time: The sum of the seek time, rotational latency, and transfer time.
  This is the total time required to read or write data.

- Throughput: The number of requests processed per unit time.

- Response Time: The time it takes from when a request is made until it is completed.

- Disk Bandwidth: The total amount of data that can be transferred per unit time.

### FCFS Scheduling Algorithm
It is the simplest Disk Scheduling algorithm. It services the IO requests in the order in which they arrive.
There is no starvation in this algorithm, every request is serviced.

*Disadvantages:*
- The scheme does not optimize the seek time.
- The request may come from different processes therefore there is the possibility of inappropriate movement of the head.

### Example
Consider the following disk request sequence for a disk with 100 tracks
 45, 21, 67, 90, 4, 50, 89, 52, 61, 87, 25

Head pointer starting at 50 and moving in left direction.
Find the number of head movements in cylinders using FCFS scheduling.

Solution:

Number of cylinders moved by the head
```
= (50-45)+(45-21)+(67-21)+(90-67)+(90-4)+(50-4)
    +(89-50)+(61-52)+(87-61)+(87-25)

= 5 + 24 + 46 + 23 + 86 + 46 + 49 + 9 + 26 + 62

= 376
```

![image](https://github.com/muhammadbilal254/OS-Final-/assets/80221112/12bcd70b-3e2e-4cef-8408-9afc1998b4c6)


### SSTF Scheduling Algorithm
Shortest seek time first (SSTF) algorithm selects the disk I/O request which requires
the least disk arm movement from its current position regardless of the direction.
It reduces the total seek time as compared to FCFS.

It allows the head to move to the closest track in the service queue.

*Disadvantages*
- It may cause starvation for some requests.
- Switching direction on the frequent basis slows the working of algorithm.
- It is not the most optimal algorithm.

### Example
Consider the following disk request sequence for a disk with 100 tracks

45, 21, 67, 90, 4, 89, 52, 61, 87, 25

Head pointer starting at 50. Find the number of head movements in cylinders using SSTF scheduling.

Solution:

Number of cylinders = 5 + 7 + 9 + 6 + 20 + 2 + 1 + 65 + 4 + 17 = 136


![image](https://github.com/muhammadbilal254/OS-Final-/assets/80221112/542a0056-04e8-4bf7-9e79-ff586c082834)





