# **Semaphores in Operating Systems**

**Definition:**  
A **semaphore** is a synchronization primitive used to manage **concurrent access** to shared resources.  
It uses a counter to track the availability of resources and ensures **mutual exclusion**, preventing race conditions.

## ✅ **Types of Semaphores:**

### 1. **Binary Semaphore (Mutex):**

- Takes values **0** or **1**.
- Used to ensure **mutual exclusion**, allowing only one process to access the **critical section** at a time.

### 2. **Counting Semaphore:**

- Can take values **greater than 1**.
- Used to manage **multiple instances** of a resource (e.g., multiple printers or connections).

---

# **Deadlock in Operating Systems**

**Definition:**  
A **deadlock** occurs when two or more processes become stuck in a state where:

- Each process holds a resource and waits for another **resource held by another process**.
- None of the processes can continue, causing a system halt.

![Deadlock Diagram](https://d3pdqc0wehtytt.cloudfront.net/media/reading-images/8cdbfe4d-e77e-433e-85e8-337ca55be5a0.png "Deadlock Diagram")

## ✅ **Example of Deadlock:**

### **Example 1: Two processes, `P1` and `P2`, each hold one tape drive and wait for the other’s tape drive to be released.**

### **Example 2: Two processes, P0 and P1, using semaphores:**

1. **P0** executes `wait(A)` → locks semaphore A.
2. **P1** executes `wait(B)` → locks semaphore B.
3. Now:
   - **P0** tries to `wait(B)` → blocked.
   - **P1** tries to `wait(A)` → blocked.
4. Both processes are **stuck waiting** for each other, causing **deadlock**.

## ✅ **Conditions for Deadlock:**

1. **Mutual Exclusion:**

   - At least one resource is held in an **exclusive mode**.

2. **Hold and Wait:**

   - A process holding one resource is waiting to acquire another.

3. **No Preemption:**

   - Resources cannot be forcibly taken from processes.

4. **Circular Wait:**
   - A circular chain exists where each process waits for a resource held by the next process in the chain.
