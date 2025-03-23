# Shortest Remaining Time First (SRTF)

## Overview:
- **Shortest Remaining Time First (SRTF)** is a preemptive version of the **Shortest Job First (SJF)** scheduling algorithm.
- In this algorithm, the CPU switches to a new process if it arrives with a shorter **Burst Time (BT)** than the remaining time of the currently executing process.
- It ensures that the process with the least remaining time is always executed next, making it more dynamic than non-preemptive SJF.

---

## Working of SRTF:
1. The CPU is assigned to the process with the shortest remaining burst time.
2. If a new process arrives with a shorter burst time than the remaining time of the currently running process, the running process is preempted, and the new process starts executing.
3. The preempted process goes back into the ready queue and resumes execution later when it has the shortest remaining burst time.

---

## Example (Preemptive SJF or SRTF):
### Given Data:
| Process | AT | BT |
|---------|----|----|
| P1      | 0  | 8  |
| P2      | 1  | 4  |
| P3      | 2  | 9  |
| P4      | 3  | 5  |

### Execution Order Based on SRTF:
1. At time 0, **P1** starts execution (BT = 8).
2. At time 1, **P2** arrives with a shorter burst time (BT = 4), so **P1** is preempted, and **P2** starts executing.
3. At time 2, **P3** arrives, but **P2** continues since its remaining burst time (3 units) is shorter than **P3** (BT = 9).
4. At time 3, **P4** arrives with a burst time of 5 units, but **P2** still has the shortest remaining time (2 units), so **P2** finishes execution at time 5.
5. After **P2** finishes, **P4** (with the next shortest burst time) starts execution.
6. At time 8, **P4** finishes, and **P1** resumes with its remaining time of 7 units.
7. **P1** executes until time 15, then **P3** executes until completion at time 24.

---

### Calculations:
| Process | AT | BT | CT  | TAT        | WT        |
|---------|----|----|-----|------------|-----------|
| P1      | 0  | 8  | 15  | 15 - 0 = 15 | 15 - 8 = 7 |
| P2      | 1  | 4  | 5   | 5 - 1 = 4   | 4 - 4 = 0  |
| P3      | 2  | 9  | 24  | 24 - 2 = 22 | 22 - 9 = 13|
| P4      | 3  | 5  | 8   | 8 - 3 = 5   | 5 - 5 = 0  |

---

### Explanation:
- **P1** starts first but is preempted by **P2** at time 1 because **P2** has a shorter burst time.
- **P2** completes execution at time 5.
- **P4** starts execution after **P2** finishes because it has a shorter burst time than the remaining time of **P1** and **P3**.
- Once **P4** completes, **P1** resumes and finishes at time 15.
- **P3** runs last because it had the longest burst time, finishing at time 24.

---

### Result:
| Process | AT | BT | CT | TAT | WT |
|---------|----|----|----|-----|----|
| P1      | 0  | 8  | 15 | 15  | 7  |
| P2      | 1  | 4  | 5  | 4   | 0  |
| P3      | 2  | 9  | 24 | 22  | 13 |
| P4      | 3  | 5  | 8  | 5   | 0  |

---

![Problems on SRTF](https://d3pdqc0wehtytt.cloudfront.net/media/reading-images/2e663342-fdbe-4dbb-b8fc-6c591b321d94.png "Problems on SRTF")

---

## Advantages and Disadvantages of SRTF:

| **Advantages**                                            | **Disadvantages**                                                                  |
|-----------------------------------------------------------|------------------------------------------------------------------------------------|
| 1. **Minimizes average waiting time**: CPU runs the process with the shortest remaining time, reducing waiting time. | 1. **Starvation**: Longer processes may face indefinite delays if shorter processes keep arriving. |
| 2. **Improved turnaround time**: Prioritizing shorter jobs helps minimize overall turnaround time. | 2. **Overhead**: Frequent context switching due to preemption leads to increased overhead. |
| 3. **Preemptive**: More responsive to new processes with shorter burst times, improving system responsiveness. | 3. **Difficult to estimate burst time**: Estimating or predicting remaining burst time is challenging in real systems. |

---
