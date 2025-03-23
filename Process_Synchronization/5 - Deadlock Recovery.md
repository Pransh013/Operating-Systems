# Deadlock Recovery

When a Deadlock Detection Algorithm identifies that a deadlock has occurred, the system must recover from it. There are two primary approaches for breaking a deadlock: **Process Termination** and **Resource Preemption**.

---

## ✅ **1. Process Termination**

This approach involves terminating one or more processes involved in the deadlock. There are two methods to achieve this:

### a. Abort All Deadlocked Processes

- **Description:** Terminate all processes involved in the deadlock.
- **Advantage:** Guarantees the elimination of the deadlock.
- **Disadvantages:**
  - Computational work done by the deadlocked processes is lost.
  - Results in a high cost, as partial computations need to be discarded and potentially recomputed later.

### b. Abort One Process at a Time

- **Description:** Terminate one deadlocked process at a time until the deadlock is resolved.
- **Advantage:**
  - Fewer processes are killed, so there is a lower loss of computational work.
- **Disadvantages:**
  - High overhead, since the deadlock detection algorithm must be rerun after each process termination to check if the deadlock is resolved.

### 🟢 **Advantages of Process Termination:**

| Advantages                  | Disadvantages                                                                                   |
| --------------------------- | ----------------------------------------------------------------------------------------------- |
| Simple and straightforward. | Loss of data and resources used by terminated processes.                                        |
| Quick resolution.           | May cause further system issues if critical processes are terminated.                           |
| Frees up resources quickly. | Significant resource waste if terminated processes had completed a large portion of their work. |

---

## ✅ **2. Resource Preemption**

This method involves **preempting (reclaiming)** resources from one or more processes and reallocating them to other processes to break the deadlock. It introduces three key challenges:

### a. Selecting a Victim

- **Description:** Choose which process or resources to preempt in a way that **minimizes costs** (e.g., based on priority or the process's current progress).

### b. Rollback

- **Description:** If resources are preempted from a process, the process must **roll back to a safe state** (total rollback involves restarting the process).

### c. Starvation

- **Description:** A process might be chosen as a victim repeatedly, **preventing it from ever completing**.
- To avoid this, the system must ensure a process is selected as a victim only a **limited number of times**.

### 🟢 **Advantages and Disadvantages of Resource Preemption:**

| Advantages                                                  | Disadvantages                                                     |
| ----------------------------------------------------------- | ----------------------------------------------------------------- |
| Allows breaking the deadlock without terminating processes. | Increased overhead in determining which resources to preempt.     |
| More efficient than process termination.                    | Can cause system instability if critical resources are preempted. |
| Avoids system restarts.                                     | May delay process completion if frequently preempted.             |

---
