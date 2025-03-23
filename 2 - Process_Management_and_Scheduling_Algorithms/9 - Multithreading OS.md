# **Thread**  
**Definition:**  
A thread is the smallest unit of execution within a process. It represents a single sequence of instructions that can be executed concurrently with other threads within the same process. Multiple threads in a process share the same memory and resources but execute independently, allowing for parallelism and better resource utilization.

---

# **Process Vs Thread**

| **PROCESS**                                          | **THREAD**                                            |
|------------------------------------------------------|------------------------------------------------------|
| 1. Process means any program is in execution.        | 1. Thread means a segment of a process.               |
| 2. The process takes more time to terminate.         | 2. The thread takes less time to terminate.           |
| 3. It takes more time for creation.                  | 3. It takes less time for creation.                   |
| 4. It also takes more time for context switching.    | 4. It takes less time for context switching.          |
| 5. The process is less efficient in terms of communication. | 5. Thread is more efficient in terms of communication. |
| 6. Multiprogramming holds the concepts of multi-process. | 6. A single process can consist of multiple threads.   |
| 7. The process is isolated.                          | 7. Threads share memory.                              |
| 8. The process is called the heavyweight process.    | 8. A thread is lightweight as it shares code, data, and resources. |
| 9. Process switching uses an interface in an operating system. | 9. Thread switching does not require a system call; it uses APIs. |
| 10. If one process is blocked, it does not affect the execution of other processes. | 10. If a user-level thread is blocked, all other user-level threads are blocked. |
| 11. The process has its own Process Control Block, Stack, and Address Space. | 11. Threads have a parent’s PCB, their own Thread Control Block, and Stack, but share the address space. |
| 12. Changes to the parent process do not affect child processes. | 12. Changes in one thread may affect other threads since they share resources. |
| 13. A system call is involved in process creation.   | 13. No system call is involved; threads are created using APIs. |

---

## **Multithreading in OS**
**Definition:**  
Multithreading is a technique that allows multiple threads to execute concurrently within a single process. Threads are lightweight sub-processes that share the same memory space and resources, enabling efficient task execution and improving application responsiveness.

---

### **Benefits of Multithreading**

1. **Improved Responsiveness:**  
   Threads allow applications to remain responsive even if some threads are blocked or waiting for I/O operations.

2. **Efficient Resource Sharing:**  
   Threads share the memory and resources of the process, reducing the overhead of creating separate processes.

3. **Faster Context Switching:**  
   Switching between threads within a process is faster than switching between separate processes.

4. **Concurrent Task Execution:**  
   Multithreading allows parallel execution of tasks, improving performance for tasks like I/O operations and computations.

### **Applications of Multithreading**

- **GUI Applications:**  
  Keeps the user interface responsive while performing background tasks.  
  ✅ Example: Handling a button click while updating the interface.

- **Network Applications:**  
  Improves performance by handling multiple client connections concurrently.  
  ✅ Example: A web server handling multiple client requests.

- **Multimedia Applications:**  
  Allows playing media (audio/video) while performing other tasks, such as updating user controls or handling inputs.  
  ✅ Example: Playing video while simultaneously handling keyboard inputs.

#### **Example in Java**

```java
class MultithreadingDemo extends Thread {
    public void run() {
        try {
            System.out.println("Thread " + Thread.currentThread().getId() + " is running");
        } catch (Exception e) {
            System.out.println("Exception is caught");
        }
    }

    public static void main(String[] args) {
        int n = 5; // Number of threads
        for (int i = 0; i < n; i++) {
            MultithreadingDemo thread = new MultithreadingDemo();
            thread.start();
        }
    }
}
```

---

## **Comparison Table**

| **Aspect**        | **Multithreading**                          | **Multitasking**                                | **Multiprocessing**                         |
|-------------------|------------------------------------------|------------------------------------------------|------------------------------------------|
| **Definition**    | Multiple threads within a single process | Multiple processes running simultaneously     | Multiple processes across multiple CPUs/cores |
| **Resource Sharing** | Threads share the process’s memory space | Processes are isolated from each other        | Processes run independently on different CPUs |
| **Parallelism**    | Concurrent execution of threads           | Switching between tasks (may seem parallel)    | True parallel execution on multiple CPUs      |
| **Example**        | Web browser loading multiple tabs         | Running music player and browser simultaneously | Running heavy computations on multiple cores |
