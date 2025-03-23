# Disk Scheduling

Disk scheduling is a method used by operating systems to **manage I/O requests** to a disk drive. Multiple I/O requests may arrive from different processes, but the **disk controller can only handle one request at a time**. Disk scheduling optimizes how these requests are processed to improve performance.

---

## 🔥 **Importance of Disk Scheduling**

- **Multiple I/O Requests:** Multiple processes may request I/O operations simultaneously, but only **one request** can be serviced at a time.
- **Reduce Disk Arm Movement:** Requests may be scattered across the disk, resulting in **excessive movement** of the disk arm.
- **Improve Efficiency:** Hard disks are one of the **slowest components** of a system, so efficient access methods are essential.

---

## 🔑 **Important Terminologies**

- **Seek Time:** Time taken to **move the disk arm** to the desired track.
- **Rotational Latency:** Time taken for the disk to **rotate the required sector** under the read/write head.
- **Transfer Time:** Time taken to **transfer the data** from/to the disk. It depends on the disk's rotation speed and the amount of data.
- **Disk Access Time:**  
\[
\text{Disk Access Time} = \text{Seek Time} + \text{Rotational Latency} + \text{Transfer Time}
\]
- **Disk Response Time:** The time spent by a request **waiting to perform its I/O** operation.

---

## ⚙️ **Disk Scheduling Algorithms**

### 1️⃣ **FCFS (First-Come, First-Served)**

- The simplest disk scheduling algorithm where **requests are handled in the order they arrive**.
- **Example:**  
  - **Disk queue:** `50, 170, 43, 140, 16, 190`  
  - **Initial head position:** `50`  
  - **Total head movement:**  
\[
(170 - 50) + (170 - 43) + (140 - 43) + (140 - 16) + (190 - 16) = 642
\]

### ✅ **Advantages and Disadvantages of FCFS**

| **Advantages**                  | **Disadvantages**                  |
|---------------------------------|-----------------------------------|
| Every request gets a fair chance | Does not optimize seek time       |
| No indefinite postponement      | May result in long wait times for some requests |

---

### 2️⃣ **SSTF (Shortest Seek Time First)**

- The disk arm moves to the **nearest request first**, minimizing seek time.
- **Example:**  
  - **Disk queue:** `50, 190, 16`  
  - **Initial head position:** `50`  
  - **Total head movement:**  
\[
(50 - 16) + (190 - 16) = 208
\]

### ✅ **Advantages and Disadvantages of SSTF**

| **Advantages**                  | **Disadvantages**                  |
|---------------------------------|-----------------------------------|
| Reduces average response time   | May cause starvation for longer requests |
| Increases throughput            | Requires overhead to calculate seek time |

---

### 3️⃣ **SCAN (Elevator Algorithm)**

- The disk arm moves in **one direction**, servicing requests along the way until it reaches the end of the disk, then **reverses direction**.
- **Example:**  
  - **Disk queue:** `50, 199, 16`  
  - **Initial head position:** `50`  
  - **Total head movement:**  
\[
(199 - 50) + (199 - 16) = 322
\]

### ✅ **Advantages and Disadvantages of SCAN**

| **Advantages**                  | **Disadvantages**                  |
|---------------------------------|-----------------------------------|
| High throughput                 | Long wait times for requests near recently visited locations |
| Lower variance in response times |                                   |

---

### 4️⃣ **CSCAN (Circular SCAN)**

- Similar to SCAN, but instead of reversing direction, the **disk arm jumps to the start** of the disk and continues in the same direction.
- **Example:**  
  - **Disk queue:** `50, 199, 0, 43`  
  - **Initial head position:** `50`  
  - **Total head movement:**  
\[
(199 - 50) + (199 - 0) + (43 - 0) = 391
\]

### ✅ **Advantages and Disadvantages of CSCAN**

| **Advantages**                  | **Disadvantages**                  |
|---------------------------------|-----------------------------------|
| Provides a more uniform wait time | Can be inefficient if the disk has few requests at the other end |
| Prevents requests from waiting too long |                                   |

---

### 5️⃣ **LOOK**

- Similar to SCAN, but the disk arm **only goes as far as the last request** in its direction before reversing, avoiding unnecessary movement.
- **Example:**  
  - **Disk queue:** `50, 190, 16`  
  - **Initial head position:** `50`  
  - **Total head movement:**  
\[
(190 - 50) + (190 - 16) = 314
\]

### ✅ **Advantages and Disadvantages of LOOK**

| **Advantages**                  | **Disadvantages**                  |
|---------------------------------|-----------------------------------|
| Reduces unnecessary traversal   | Similar disadvantages to SCAN     |
| Provides better performance than SCAN |                                |

---

### 6️⃣ **CLOOK**

- Similar to CSCAN, but the disk arm goes only **as far as the last request**, and then jumps back to the beginning without going to the extreme end of the disk.
- **Example:**  
  - **Disk queue:** `50, 190, 43, 16`  
  - **Initial head position:** `50`  
  - **Total head movement:**  
\[
(190 - 50) + (190 - 16) + (43 - 16) = 341
\]

### ✅ **Advantages and Disadvantages of CLOOK**

| **Advantages**                  | **Disadvantages**                  |
|---------------------------------|-----------------------------------|
| Reduces unnecessary movement like LOOK | More complex than CSCAN          |
| Provides uniform wait times like CSCAN |                                |

---

## 🛠️ **Summary of Disk Scheduling Algorithms**

| **Algorithm** | **Total Head Movement** | **Advantages**                     | **Disadvantages**               |
|---------------|--------------------------|------------------------------------|--------------------------------|
| **FCFS**      | 642                      | Fair scheduling, no starvation     | High average seek time         |
| **SSTF**      | 208                      | Lower response time, better throughput | Starvation, high variance in response times |
| **SCAN**      | 322                      | High throughput, low variance     | Long wait times for recently passed requests |
| **CSCAN**     | 391                      | Uniform wait times, prevents starvation | Can be inefficient with few requests |
| **LOOK**      | 314                      | Reduces unnecessary movement, more efficient | Similar drawbacks as SCAN       |
| **CLOOK**     | 341                      | Efficient movement, prevents unnecessary traversal | More complex than CSCAN        |
