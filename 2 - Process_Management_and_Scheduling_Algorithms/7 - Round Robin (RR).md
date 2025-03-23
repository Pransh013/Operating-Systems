# Round Robin (RR) Scheduling

## Overview:
- **Round Robin (RR)** is a preemptive CPU scheduling algorithm widely used in time-sharing and multitasking systems.
- Each process is assigned a fixed **time slice or quantum** during which it can execute.
- If a process’s quantum expires, the CPU switches to the next process in the ready queue. The preempted process is added to the end of the queue for its next turn.
- This algorithm ensures fair time-sharing and prevents any single process from monopolizing the CPU.

---

## Working of Round Robin (RR):
1. All processes are arranged in the **ready queue** in the order of their **Arrival Time (AT)**.
2. Each process is given a fixed **time quantum** to execute.
3. If a process completes execution within the quantum, it finishes and exits.
4. If a process doesn't finish within the quantum, it is preempted and placed at the **end of the queue**.
5. The algorithm continues until all processes are completed.

---

## Example:
### Given Data:
| Process | AT | BT |
|---------|----|----|
| P1      | 0  | 6  |
| P2      | 1  | 3  |
| P3      | 2  | 1  |
| P4      | 3  | 5  |

- **Time Quantum = 2 units**

---

### Execution Order Based on Round Robin (Quantum = 2):
1. **P1** starts at time 0 and runs for 2 units (remaining BT = 4).
2. **P2** starts at time 2 and runs for 2 units (remaining BT = 1).
3. **P3** starts at time 4 and runs for 1 unit (completes execution).
4. **P4** starts at time 5 and runs for 2 units (remaining BT = 3).
5. **P1** resumes at time 7 and runs for 2 units (remaining BT = 2).
6. **P2** resumes at time 9 and completes execution.
7. **P4** resumes at time 10 and runs for 2 units (remaining BT = 1).
8. **P1** resumes at time 12 and completes execution.
9. **P4** resumes at time 14 and completes execution.

---

### Calculations:
| Process | AT | BT | CT Calculation       | CT  | TAT Calculation    | TAT | WT Calculation    | WT  |
|---------|----|----|----------------------|-----|--------------------|-----|-------------------|-----|
| P1      | 0  | 6  | 0 + 6 = 14           | 14  | 14 - 0 = 14        | 14  | 14 - 6 = 8        | 8   |
| P2      | 1  | 3  | 9                    | 9   | 9 - 1 = 8          | 8   | 8 - 3 = 5         | 5   |
| P3      | 2  | 1  | 5                    | 5   | 5 - 2 = 3          | 3   | 3 - 1 = 2         | 2   |
| P4      | 3  | 5  | 15                   | 15  | 15 - 3 = 12        | 12  | 12 - 5 = 7        | 7   |

---

### Explanation:
- **P1** runs for 2 units and is preempted, leaving 4 units remaining.
- **P2** runs for 2 units and is also preempted, leaving 1 unit remaining.
- **P3**, with a burst time of 1 unit, completes execution during its first quantum.
- **P4** runs for 2 units, leaving 3 units remaining.
- The cycle continues with processes being preempted and added to the end of the queue until all are completed.

![Problems on RR](https://d3pdqc0wehtytt.cloudfront.net/media/reading-images/8ba1569b-29a1-4129-a1c5-3173bde58eef.png "Problems on RR")

---

## Advantages and Disadvantages of Round Robin (RR):

| **Advantages**                                             | **Disadvantages**                                                                  |
|------------------------------------------------------------|------------------------------------------------------------------------------------|
| 1. **Fairness**: Ensures all processes get a fixed time slice (quantum), providing equal treatment to all. | 1. **High context switching overhead**: Frequent context switches increase CPU overhead. |
| 2. **No starvation**: Every process eventually gets the CPU, avoiding indefinite delays. | 2. **Higher average turnaround time**: Can lead to higher turnaround times, especially for shorter jobs. |
| 3. **Ideal for time-sharing systems**: Well-suited for systems requiring responsiveness, as processes are rotated regularly. | 3. **Quantum selection**: Selecting an optimal time quantum is challenging. Too short leads to excessive context switching; too long reduces responsiveness. |

---

## Quantum Selection in Round Robin:
- **Too short a quantum**:
  - Causes frequent context switches.
  - Increases CPU overhead and reduces efficiency.
- **Too long a quantum**:
  - Behaves like **First-Come, First-Served (FCFS)**.
  - Longer jobs can dominate the CPU, negating the benefits of Round Robin.

---
