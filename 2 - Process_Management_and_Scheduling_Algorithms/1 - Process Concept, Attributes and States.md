## **What is a Process?**

A **process** is a program in execution, including the current values of the **program counter**, **registers**, and **variables**.

### **Process vs. Program**
- A **program** is a group of instructions written in a text file.
- A **process** is the activity or the **active state** of a program when it is being executed.

### **Lifecycle of a Program to a Process**
- When we execute a program, it becomes a process that performs all the tasks defined in the program.  
- A process, when loaded into memory, can be divided into the following four sections:  
  1. **Stack**: Contains temporary data such as function parameters, return addresses, and local variables.
  2. **Heap**: Dynamically allocated memory area used during runtime for managing dynamic data.
  3. **Data**: Holds global variables used by the program.
  4. **Text**: Contains the current executable instructions of the program.

---

### **Process Components**
- **Process Stack**: Stores local variables, function parameters, return addresses, and temporary data.  
- **Data Section**: Contains global variables and static data.  
- **Heap**: Used for dynamic memory allocation at runtime.  
- **Text Section**: Contains the compiled program instructions ready for execution.

![Process Memory Layout](https://d3pdqc0wehtytt.cloudfront.net/media/reading-images/11126bcb-30da-4b8d-9656-a212030f9dca.png "Process Memory Layout")
---

## **Process States in Operating Systems**

A process transitions through various states during its lifecycle. The states may vary slightly across operating systems, but generally, a process can be in one of the following **five states**:

1. **New**:  
   - The process is just created and is being initialized but has not yet begun execution.

2. **Ready**:  
   - The process is waiting to be allocated CPU time.  
   - It can enter the ready state from the new state or after being interrupted during execution.

3. **Running**:  
   - The process is actively executing its instructions on the CPU.  
   - Only one process can be in the running state on a single CPU at any time.

4. **Waiting**:  
   - The process is waiting for a resource, such as:  
     - User input  
     - File availability  
   - It remains in this state until the required resource is available.

5. **Terminated**:  
   - The process has completed its execution or was terminated by the operating system.  
   - It remains in this state until it is removed from memory.

![Process State Diagram](https://d3pdqc0wehtytt.cloudfront.net/media/reading-images/bd6a9801-72a1-4d65-8fbe-40ef8ace5468.png "Process State Diagram")

---

## **Attributes of a Process (Stored in the Process Control Block - PCB)**

The **Process Control Block (PCB)** is a data structure used by the operating system to store important information about each process. These attributes collectively form the context of the process.

### **Key Attributes:**

1. **Process ID**:  
   - A unique identifier assigned to each process when it is created.  
   - Used to uniquely identify and track the process in the system.

2. **Program Counter**:  
   - Stores the address of the next instruction to be executed for the process.  
   - If the process is interrupted, the program counter holds the address where execution will resume.

3. **Process State**:  
   - Indicates the current state of the process (New, Ready, Running, Waiting, or Terminated).  
   - The OS keeps track of the state as the process moves through different phases.

4. **Priority**:  
   - Each process is assigned a priority.  
   - The process with the highest priority gets the CPU first, based on the OS’s scheduling policy.

5. **General Purpose Registers**:  
   - Holds data and instructions specific to the process during execution.  
   - These registers include temporary data like variables, function results, etc.

6. **List of Open Files**:  
   - During execution, a process may open files.  
   - The OS maintains a list of these open files in the PCB to ensure they remain accessible while the process is running.

7. **List of Open Devices**:  
   - Similar to files, the OS tracks all devices (e.g., printers, USBs) used by the process during its execution.  
   - This ensures proper access and control over the devices.

![Process Control Block](https://d3pdqc0wehtytt.cloudfront.net/media/reading-images/45aeadff-1aa3-4d81-81f5-bb8b711b2426.png "Process Control Block")

---
