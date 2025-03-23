# Shortest Job First (SJF)

## Overview:
- **Shortest Job First (SJF)** is a CPU scheduling algorithm that selects the process with the shortest **Burst Time (BT)** to execute next.
- It can be **Preemptive** (Shortest Remaining Time First, SRTF) or **Non-preemptive**.
- It aims to reduce **Waiting Time (WT)** and **Turnaround Time (TAT)** by giving preference to shorter processes.

---

## Working of SJF:
- The process with the shortest burst time is selected for execution first.
- In **non-preemptive SJF**, once a process starts executing, it cannot be interrupted until it finishes.

---

### Example (Non-preemptive SJF):
Let’s assume the following processes with their **Arrival Time (AT)** and **Burst Time (BT)**:

| Process | AT | BT |
|---------|----|----|
| P1      | 0  | 7  |
| P2      | 2  | 4  |
| P3      | 4  | 1  |
| P4      | 5  | 3  |

#### Execution Order Based on SJF:
1. **P1** arrives at time 0 and starts executing.
2. At time 2, **P2** arrives, but since **P1** is still running (non-preemptive), it finishes first.
3. After **P1** completes at time 7, processes **P2**, **P3**, and **P4** are available. **P3** has the shortest burst time (1 unit), so it is executed next.
4. Once **P3** finishes at time 8, the remaining processes are **P2** and **P4**. **P4** has a shorter burst time (3 units), so it runs next.
5. Finally, **P2** runs last since it has the longest burst time left (4 units).

---

### Calculations:
| Process | AT | BT | CT Calculation | CT  | TAT Calculation | TAT | WT Calculation | WT  |
|---------|----|----|----------------|-----|-----------------|-----|----------------|-----|
| P1      | 0  | 7  | 0 + 7 = 7      |  7  | 7 - 0 = 7       |  7  | 7 - 7 = 0      |  0  |
| P2      | 2  | 4  | 13 + 4 = 17    | 17  | 17 - 2 = 15     | 15  | 15 - 4 = 11    | 11  |
| P3      | 4  | 1  | 7 + 1 = 8      |  8  | 8 - 4 = 4       |  4  | 4 - 1 = 3      |  3  |
| P4      | 5  | 3  | 8 + 3 = 11     | 11  | 11 - 5 = 6      |  6  | 6 - 3 = 3      |  3  |

---

### Explanation:
- **P1** runs first because it arrives at time 0.
- **P3** runs next because it has the shortest burst time (1 unit) among the available processes at time 7.
- **P4** runs after **P3** due to its shorter burst time (3 units) compared to **P2**.
- **P2** runs last because it has the longest burst time (4 units) and arrives later than some shorter processes.

![Problems on SJF](https://d3pdqc0wehtytt.cloudfront.net/media/reading-images/ff7569b0-8110-46ca-ae63-e6b8487b253a.png "Problems on SJF")

---

### Starvation in SJF:
- **Definition**: Starvation occurs when a process with a long burst time is continually postponed due to the arrival of shorter processes.
- **Cause**: In non-preemptive SJF, long processes may suffer indefinite delays if shorter processes keep arriving.
- **Example**: If a process with 10 units of burst time is always followed by processes with 1-2 units of burst time, the longer process may not get CPU time for a long period.

---

### Advantages and Disadvantages of SJF:

| **Advantages**                                            | **Disadvantages**                                                                 |
|-----------------------------------------------------------|-----------------------------------------------------------------------------------|
| 1. **Minimizes waiting time**: Reduces average waiting time as shorter processes are executed first. | 1. **Starvation**: Longer processes may face indefinite delays if shorter processes keep arriving. |
| 2. **Reduces turnaround time**: Shorter processes complete quickly, improving overall system turnaround time. | 2. **Difficult to predict burst time**: Requires accurate estimation of burst times, which is often not feasible. |
| 3. **More efficient than FCFS**: Addresses inefficiencies of FCFS by prioritizing shorter jobs.    | 3. **Not suitable for time-sharing systems**: Preemptive SJF (SRTF) is complex to implement in real-time systems. |

---
