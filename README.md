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


## SCAN and C-SCAN algorithm

### Scan Algorithm
It is also called as Elevator Algorithm. In this algorithm, the disk arm moves into a particular direction till the end, satisfying all the requests coming in its path,and then it turns backand
moves in the reverse direction satisfying requests coming in its path.

It works in the way an elevator works, elevator moves in a direction completely till the last floor of that direction and then turns back.

### Example
Consider the following disk request sequence for a disk with 100 tracks

98, 137, 122, 183, 14, 133, 65, 78

Head pointer starting at 54 and moving in left direction. Find the number of head movements in cylinders using SCAN scheduling.

Number of Cylinders = 40 + 14 + 65 + 13 + 20 + 24 + 11 + 4 + 46 = 237

![image](https://github.com/muhammadbilal254/OS-Final-/assets/80221112/b1a38116-3e84-4629-a1bd-cf9424e447bd)

---

### C-SCAN algorithm
In C-SCAN algorithm, the arm of the disk moves in a particular direction servicing requests until it reaches the last cylinder, 
then it jumps to the last cylinder of the opposite direction without servicing any request then it turns back 
and start moving in that direction servicing the remaining requests.

### Example
Consider the following disk request sequence for a disk with 100 tracks

98, 137, 122, 183, 14, 133, 65, 78

Head pointer starting at 54 and moving in left direction. Find the number of head movements in cylinders using C-SCAN scheduling

No. of cylinders crossed = 40 + 14 + 199 + 16 + 46 + 4 + 11 + 24 + 20 + 13 = 387

![image](https://github.com/muhammadbilal254/OS-Final-/assets/80221112/61046ed5-afde-407e-a358-4ff15f1bb517)

### Look Scheduling
It is like SCAN scheduling Algorithm to some extant except the difference that, in this scheduling algorithm,
the arm of the disk stops moving inwards (or outwards) when no more request in that direction exists. 
This algorithm tries to overcome the overhead of SCAN algorithm which forces disk arm to move in
one direction till the end regardless of knowing if any request exists in the direction or not.

### Example
Consider the following disk request sequence for a disk with 100 tracks

98, 137, 122, 183, 14, 133, 65, 78

Head pointer starting at 54 and moving in left direction. Find the number of head movements in cylinders using LOOK scheduling.

Number of cylinders crossed = 40 + 51 + 13 + +20 + 24 + 11 + 4 + 46 = 209

![image](https://github.com/muhammadbilal254/OS-Final-/assets/80221112/b79b44ac-3595-44ca-9589-1e09b8503d7e)

### C-Look Scheduling
C-Look Algorithm is similar to C-SCAN algorithm to some extent. In this algorithm,
the arm of the disk moves outwards servicing requests until it reaches the highest request cylinder, then it jumps to the lowest request
cylinder without servicing any request then it again start moving outwards servicing the remaining requests.

It is different from C SCAN algorithm in the sense that, C SCAN force the disk arm to move till the last cylinder regardless of
knowing whether any request is to be serviced on that cylinder or not.

### Example
Consider the following disk request sequence for a disk with 100 tracks

98, 137, 122, 183, 14, 133, 65, 78

Head pointer starting at 54 and moving in left direction. Find the number of head movements in cylinders using C LOOK scheduling.

Number of cylinders crossed = 11 + 13 + 20 + 24 + 11 + 4 + 46 + 169 = 298

![image](https://github.com/muhammadbilal254/OS-Final-/assets/80221112/e4e6fd45-2049-45fc-80ee-6abb5a7a4944)

----
----

### Process Scheduling Algorithm

A process scheduling algorithm determines how the CPU is allocated to processes. It ensures that processes are executed in an efficient and fair manner.

### Types of Schedulers

1. Long-Term Scheduler (Job Scheduler): Decides which processes should be brought into the ready queue from the job pool. It controls the degree of multiprogramming.

2. Short-Term Scheduler (CPU Scheduler): Selects which process from the ready queue should be executed next by the CPU. This happens frequently.

3. Medium-Term Scheduler: Temporarily removes processes from the main memory and places them in the secondary memory (swapping). It aims to improve the process mix.

### Types of Processes

1. I/O-Bound Processes: Spend more time doing input/output operations than computations. They have short CPU bursts.

2. CPU-Bound Processes: Spend more time doing computations than input/output operations. They have long CPU bursts.

### CPU Schedulers

CPU schedulers decide the order in which processes are executed. The primary function is to maximize CPU utilization and improve system performance.

### Types of Scheduling Algorithms

1. First-Come, First-Served (FCFS): Processes are executed in the order they arrive. It's simple but can lead to the "convoy effect."

2. Shortest Job Next (SJN): Processes with the shortest burst time are executed first. It minimizes waiting time but requires precise knowledge of process length.

3. Priority Scheduling: Each process is assigned a priority, and the CPU is allocated to the process with the highest priority. Lower priority processes might suffer from starvation.

4. Round Robin (RR): Each process gets a small unit of CPU time (time quantum). Processes are executed in a cyclic order. It's fair and good for time-sharing systems.

5. Multilevel Queue Scheduling: Processes are divided into different queues based on their priority or type, and each queue has its own scheduling algorithm.

6. Multilevel Feedback Queue Scheduling: Processes can move between queues based on their behavior and requirements, combining multiple algorithms.

### Scheduling Criteria

1. CPU Utilization: Keep the CPU as busy as possible.
2. Throughput: The number of processes completed per unit of time.
3. Turnaround Time: The total time taken from process submission to completion.
4. Waiting Time: The total time a process spends waiting in the ready queue.
5. Response Time: The time from process submission until the first response is produced.

These criteria help in evaluating the effectiveness and efficiency of scheduling algorithms.

---
---

# Memory Management System

A memory management system is crucial in an operating system as it manages the computer's memory, ensuring that each process has enough memory to execute efficiently without interfering with other processes.

### Key Concepts of Memory Management

1. *Memory Allocation*: Allocating memory to processes when they need it and deallocating it when they are done.
2. *Memory Protection*: Ensuring that one process cannot interfere with the memory allocated to another process.
3. *Memory Sharing*: Allowing multiple processes to share the same memory space, if needed.
4. *Virtual Memory*: Using a portion of the hard drive to extend the physical memory (RAM), enabling the execution of larger processes than the available physical memory.

### Types of Memory

1. *Primary Memory (RAM)*: Fast and directly accessible by the CPU. It is volatile, meaning it loses its data when the power is turned off.
2. *Secondary Memory*: Includes hard drives and SSDs. It is non-volatile and used for long-term storage.

### Memory Allocation Techniques

1. *Contiguous Memory Allocation*: Allocates a single continuous block of memory to each process.
   - *Fixed-Size Partitioning*: Divides memory into fixed-size blocks. Processes are loaded into the first available block.
   - *Variable-Size Partitioning*: Allocates memory as needed. It can lead to fragmentation.

2. *Non-Contiguous Memory Allocation*: Allocates memory in separate blocks, allowing more flexibility.
   - *Paging*: Divides memory into fixed-size pages and processes into blocks of the same size called frames. The operating system maintains a page table to map frames to pages.
   - *Segmentation*: Divides memory into segments of different sizes based on the logical divisions of a process, like code, data, and stack.

### Virtual Memory

Virtual memory allows the execution of processes that may not be entirely in the physical memory by using disk space to extend RAM.

- *Demand Paging*: Loads pages into memory only when they are needed, reducing the load on physical memory.
- *Page Replacement Algorithms*: Determine which pages to swap out when new pages need to be loaded.
  - *FIFO (First-In-First-Out)*: Replaces the oldest page in memory.
  - *LRU (Least Recently Used)*: Replaces the page that has not been used for the longest time.
  - *Optimal*: Replaces the page that will not be used for the longest time in the future (theoretical).

### Memory Management Techniques

1. *Swapping*: Temporarily moves inactive processes from RAM to disk to free up memory for other processes.
2. *Compaction*: Reorganizes memory to eliminate fragmentation, making larger contiguous blocks available.
3. *Garbage Collection*: Automatically reclaims memory that is no longer in use by the program.

### Memory Protection and Sharing

1. *Protection*: Ensures that processes do not interfere with each other’s memory using techniques like base and limit registers.
2. *Sharing*: Allows processes to share memory spaces when necessary, such as when multiple processes need access to the same data.

### Importance of Memory Management

- *Efficiency*: Ensures optimal use of memory resources, reducing waste and improving system performance.
- *Security*: Prevents unauthorized access to memory, protecting the integrity of processes.
- *Multitasking*: Enables multiple processes to run simultaneously without interference.

In summary, memory management is a fundamental aspect of an operating system, handling the allocation, protection, and optimization of memory resources to ensure smooth and efficient execution of processes.

---
---


