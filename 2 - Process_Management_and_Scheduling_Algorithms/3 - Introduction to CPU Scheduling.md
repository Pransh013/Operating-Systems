## **CPU Scheduling**

In uniprogramming systems (e.g., MS-DOS), when a process waits for an I/O operation, the CPU remains idle.

- **Uniprogramming:** Only one program can be executed at a time.
- **Overhead:** Refers to extra system resources (time, memory, CPU cycles) required beyond user program execution, often causing system inefficiency.

- This creates wasted CPU time and leads to **starvation** (when a process doesn't get the resources it needs).

In **multiprogramming systems**, the CPU doesn't remain idle during a process's I/O wait time:

- The operating system switches to another process to maximize CPU utilization.
- **CPU Scheduling:** The process of selecting which process will be given access to the CPU for execution.
- The short-term scheduler (CPU scheduler) handles this scheduling and assigns the CPU to processes in the ready queue.

---

### **Context Switching**

- When a running process requests I/O, the short-term scheduler saves the current process state (in the **Process Control Block - PCB**) and switches the process from **Running** to **Waiting** state.
- The scheduler then picks another process from the **Ready Queue** and assigns the CPU to it.
- This switching between processes is called **Context Switching**.

![Context Switching Diagram](https://d3pdqc0wehtytt.cloudfront.net/media/reading-images/01244947-0b8b-4a26-bd97-762089949e19.png "Context Switching Diagram")

---

### **Criteria for CPU Scheduling**

| **Criteria**         | **Description**                                                                                       | **Goal**                                           |
|-----------------------|-------------------------------------------------------------------------------------------------------|---------------------------------------------------|
| **CPU Utilization**   | Refers to the percentage of time that the CPU is being actively used.                                 | Maximize CPU usage by keeping the CPU busy.       |
| **Throughput**        | Measures the number of processes completed per unit time.                                            | Maximize throughput by completing more processes. |
| **Turnaround Time**   | Total time from when a process enters the ready queue to when it finishes execution.                  | Minimize turnaround time for efficiency.          |
| **Waiting Time**      | Time spent by a process in the ready queue waiting for CPU time.                                      | Minimize waiting time in the ready queue.         |
| **Response Time**     | Time from when a process enters the ready queue to when it starts execution.                          | Minimize response time for faster process starts. |

---

### **Purpose of a Scheduling Algorithm**

The main objectives of a scheduling algorithm in an operating system are:

1. **Maximum CPU Utilization:** Ensure that the CPU remains busy most of the time, reducing idle periods.
2. **Fair Allocation of CPU:** Ensure that all processes get a fair share of CPU time.
3. **Maximum Throughput:** Increase the number of processes completed in a given time.
4. **Minimum Turnaround Time:** Reduce the total time from process submission to completion.
5. **Minimum Waiting Time:** Minimize the time processes spend in the ready queue.
6. **Minimum Response Time:** Ensure that processes start execution as quickly as possible after entering the ready queue.

---

### **Difference Between Preemptive and Non-Preemptive Approach**

| **Criteria**          | **Preemptive Approach**                                           | **Non-Preemptive Approach**                                   |
|------------------------|------------------------------------------------------------------|-------------------------------------------------------------|
| **Resource Allocation** | Resources are allocated for a predetermined time.              | Resources cannot be withdrawn until the process finishes.   |
| **Process Switching**  | The process can be preempted (interrupted) before it completes. | The process runs to completion without interruption.        |
| **Process States**     | Transition from Running to Ready or Waiting to Ready state.     | No switching until the process finishes and moves to Waiting. |
| **Use Case**           | Used in **Round Robin**, **Priority Scheduling (Preemptive)**.  | Used in **First Come First Serve (FCFS)**, **SJF (Non-Preemptive)**. |

---
