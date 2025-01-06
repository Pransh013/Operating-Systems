## **Process Scheduler**

A **Process Scheduler** is a component of the operating system responsible for managing the execution of processes by allocating CPU time and other resources to them. It determines which process will run, for how long, and in what order, ensuring optimal usage of the CPU and other system resources.

In modern multitasking operating systems, multiple processes compete for limited resources (especially the CPU). The scheduler ensures these processes are handled efficiently and fairly, maintaining system responsiveness and avoiding deadlocks or starvation.

## **Types of Process Scheduler**

| **Criteria**           | **Long-term Scheduler**                                                            | **Short-term Scheduler**                                                                   | **Medium-term Scheduler**                                                 |
| ---------------------- | ---------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------- |
| **Role**               | Selects which processes from the job pool are admitted into memory.                | Selects which process from the ready queue should be executed next.                        | Swaps processes in and out of memory to manage memory shortages.          |
| **Frequency**          | Runs infrequently, decisions made over long intervals.                             | Runs very frequently (milliseconds or less).                                               | Runs less frequently, depending on memory availability.                   |
| **Speed of Execution** | Slow, as it handles heavy processes over longer durations.                         | Very fast, operates on a micro or millisecond scale.                                       | Intermediate speed, depends on system memory load.                        |
| **Purpose**            | Ensures a balanced mix of I/O-bound and CPU-bound processes in the system.         | Allocates CPU to processes in the ready queue based on priority and scheduling algorithms. | Frees up memory by temporarily removing inactive processes (swapping).    |
| **Decision Factors**   | System utilization, memory availability, type of program (I/O-bound or CPU-bound). | Process priority, remaining burst time, time spent waiting in the ready queue.             | Memory pressure and requirements of running processes.                    |
| **Example Scenarios**  | Decides to admit a batch processing job into memory for later execution.           | Assigns the CPU to a real-time task that requires immediate processing.                    | Swaps out a background task to allocate more memory to an active process. |

---

## **Different Types of Job Queue**

| **Criteria**        | **Job Queue**                                                                                    | **Ready Queue**                                                                               | **Waiting Queue**                                                                                   |
| ------------------- | ------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- |
| **Purpose**         | Stores all newly created processes before they are admitted into memory.                         | Stores processes that are ready for execution and waiting for CPU time.                       | Stores processes that are waiting for I/O operations or other resources before resuming execution.  |
| **Managed By**      | Managed by the Long-term scheduler (Job scheduler), which selects processes to load into memory. | Managed by the Short-term scheduler (CPU scheduler), which picks processes for CPU execution. | Managed by the OS, when a process transitions from Running to Waiting due to I/O or resource needs. |
| **Memory Location** | Processes are stored in secondary memory (disk) before moving to primary memory.                 | Processes are stored in primary memory (RAM) and are ready to be dispatched to the CPU.       | Processes are stored in primary memory while waiting for I/O or resource completion.                |
| **Example**         | A newly created process enters the job queue and waits for memory allocation.                    | A process in the ready queue is picked by the CPU scheduler to start execution.               | A process waiting for a file read operation to complete before resuming execution.                  |

![Job Queue Diagram](https://d3pdqc0wehtytt.cloudfront.net/media/reading-images/285ef7ab-880c-4f15-80e9-f3628b5cd967.png "Job Queue Diagram")

---

## **Various Times Related to Process**

| **Criteria**        | **Definition**                                                           | **Example Calculation**                                      |
| ------------------- | ------------------------------------------------------------------------ | ------------------------------------------------------------ |
| **Arrival Time**    | Time at which a process enters the ready queue.                          | Arrives at 5ms in the ready queue.                           |
| **Burst Time**      | Total CPU time required to execute the process (excluding waiting time). | Requires 10ms of CPU time.                                   |
| **Completion Time** | Time at which the process completes its execution.                       | Completes execution at 20ms.                                 |
| **Turnaround Time** | Total time from process arrival to completion.                           | Turnaround = Completion - Arrival = 20ms - 5ms = 15ms.       |
| **Waiting Time**    | Total time the process waits in the ready queue for CPU assignment.      | Waiting = Turnaround - Burst = 15ms - 10ms = 5ms.            |
| **Response Time**   | Difference between arrival time and when the process first gets CPU.     | Response = First CPU Allocation - Arrival = 7ms - 5ms = 2ms. |

## ![Process Times Example](https://d3pdqc0wehtytt.cloudfront.net/media/reading-images/a404412f-c4f0-41b0-8576-c035ff5e3875.png "Process Times Example")
