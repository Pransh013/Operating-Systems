## Multitasking

**Definition**: The ability of an operating system to run multiple tasks (processes) simultaneously.

#### Types:
- **Preemptive Multitasking**: The OS decides when to switch between tasks (e.g., Windows, Linux).
- **Cooperative Multitasking**: Each task decides when to give up control (e.g., older Mac OS versions).

#### Use Case:
- Running multiple applications simultaneously (e.g., listening to music while browsing the web).

---

## Multi-Processor

- It involves the use of more than one CPU, enabling load sharing across processors.

- It is more complex compared to single-processor scheduling, especially when managing load balancing and processor affinity.

- Processors can be either Homogeneous (identical) or Heterogeneous (different functionality).

### Approaches to Multiple-Processor Scheduling:
1. **Asymmetric Multiprocessing**:
   - A single processor (master) handles all scheduling and I/O operations.
   - Other processors execute only user code.
   - Reduces data sharing complexity and simplifies scheduling.
   
2. **Symmetric Multiprocessing (SMP)**:
   - Each processor is self-scheduling.
   - Processes may share a common ready queue or have their own private queue.
   - Each processor independently selects processes to execute.

### Processor Affinity:
- Processor Affinity binds a process/thread to a specific CPU or core.
- Improves performance by reducing context switching overhead.
- **Types of Processor Affinity:**
  - Soft Affinity: OS attempts to keep processes on the same processor but doesn’t guarantee it.
  - Hard Affinity: Processes can specify a subset of processors to run on (supported by system calls like `sched_setaffinity()`).

### Load Balancing:
- Ensures workload is evenly distributed across all processors in an SMP system.
- **Types of Load Balancing:**
  1. **Push Migration**: A task actively redistributes processes when an imbalance is detected.
  2. **Pull Migration**: Idle processors pull processes from busy processors.
