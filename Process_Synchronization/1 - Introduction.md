# **Process Synchronization**

**Definition:**  
Process Synchronization is a technique used to coordinate processes that share data, ensuring that their actions do not result in data inconsistency or race conditions. It is essential in systems where multiple processes operate on shared resources.

---

## **Types of Processes in Operating Systems**

#### **Independent Process**

- A process that does not affect or is not affected by other processes during its execution.
- **Example:**
  - Processes that do not share variables, databases, or files (e.g., a text editor and a media player running independently).

#### **Cooperating Process**

- A process that affects or is affected by other processes.
- **Example:**
  - Processes that share data such as variables, files, or databases (e.g., a web browser and a file download process sharing files).

---

## **Inter-Process Communication (IPC)**

**Definition:**  
IPC is a mechanism that allows processes to communicate and synchronize their actions. This communication is essential for cooperation between processes. IPC can be achieved through two primary methods:  
✅ **Shared Memory**  
✅ **Message Passing**

---

## **Shared Memory Method**

- In **Shared Memory**, two or more processes share a common memory space to communicate.

### **Example: Producer-Consumer Problem**

**Producer:**

- Generates items and stores them in a buffer (shared memory).

**Consumer:**

- Retrieves items from the buffer for processing.

### **There are two variations of this problem:**

- **Unbounded Buffer:**

  - The producer can continue to produce items without any limit.

- **Bounded Buffer:**
  - The producer must wait if the buffer is full, and the consumer must wait if the buffer is empty.

### **Bounded Buffer Flow:**

1. The producer generates items until the buffer is full.
2. The producer waits for the consumer to consume items.
3. The consumer consumes items if they are available; otherwise, it waits for the producer to generate more items.

---

## **Message Passing Method**

- In **Message Passing**, processes communicate by sending and receiving messages without shared memory.

### **Communication Steps:**

1. **Establish a communication link** between the processes (if not already established).
2. **Exchange messages** using two basic primitives:
   - `send(message, destination)`: Sends a message to another process.
   - `receive(message, host)`: Receives a message from another process.

### **Use Case:**

- This method is ideal for **distributed systems**, where processes run on separate machines without access to shared memory.
