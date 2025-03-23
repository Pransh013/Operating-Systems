# Types of CPU Scheduling Algorithms

## First Come First Serve (FCFS)

### Overview:
- **FCFS (First Come First Serve)** is the simplest CPU scheduling algorithm, based on the **FIFO (First In First Out)** principle.
- Processes are executed in the order of their **Arrival Time (AT)**.
- It can be **Preemptive** or **Non-preemptive**, though it is generally implemented in a non-preemptive manner.

### Working of FCFS:
- Processes are executed in the order they arrive.
- There is no priority-based scheduling—hence, simpler but less efficient.

### Example:
Let’s assume the following processes with their **Arrival Time (AT)** and **Burst Time (BT)**:

| Process | AT | BT | CT Calculation | TAT Calculation | WT Calculation |
|---------|----|----|----------------|-----------------|----------------|
| P1      | 0  | 5  | 0 + 5 = 5      | 5 - 0 = 5       | 5 - 5 = 0      |
| P2      | 1  | 3  | 5 + 3 = 8      | 8 - 1 = 7       | 7 - 3 = 4      |
| P3      | 2  | 8  | 8 + 8 = 16     | 16 - 2 = 14     | 14 - 8 = 6     |

![Problems on FCFS](https://d3pdqc0wehtytt.cloudfront.net/media/reading-images/4781d7a4-1484-4e95-b775-eea0167647c1.png "Problems on FCFS")

---

### Convoy Effect:
- **Definition**: When a long process holds the CPU, smaller processes are forced to wait for their turn, increasing their **Waiting Time (WT)**, **Turnaround Time (TAT)**, and **Completion Time (CT)**.
- **Cause**: Occurs because the FCFS scheduling is non-preemptive.
- **Example**: If a long process (e.g., a job taking 10 units of time) is followed by short processes (e.g., jobs taking 1-2 units), the short processes are delayed unnecessarily.

---

### Advantages & Disadvantages of FCFS

#### Advantages:
1. **Simple to implement**: Easy to understand and implement due to its straightforward approach.
2. **Fairness**: Every process gets a turn based on its arrival time, ensuring no process is skipped.
3. **No starvation**: Every process will eventually be executed since it follows the order of arrival.

#### Disadvantages:
1. **Convoy Effect**: Shorter processes have to wait behind longer ones, increasing their waiting time.
2. **Not optimal for time-sharing systems**: No flexibility to interrupt long processes for higher-priority tasks or more critical processes.
3. **Starvation (indefinite delay)**: If a long job takes an excessive amount of time, other processes may face indefinite delays.
