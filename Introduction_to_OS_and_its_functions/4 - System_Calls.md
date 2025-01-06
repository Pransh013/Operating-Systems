# System Call

A **System Call** is a mechanism that allows a user-level process to request services from the Operating System (OS). These services often involve accessing hardware resources (e.g., I/O devices) or performing other privileged operations (e.g., memory management) that user programs cannot execute directly.

---

## Why Use System Calls?

User programs often need to interact with hardware or OS-level functionalities, which are restricted to maintain security and stability. System calls provide a controlled interface for accessing these resources while ensuring security and preventing unauthorized operations.

---

## Steps to Execute a System Call

### 1. Parameter Passing
System calls often require parameters (e.g., filenames, memory addresses). Parameters can be passed to the OS through one of the following methods:
- **Register Method:** Parameters are stored in CPU registers.
- **Block in Memory:** Parameters are stored in a memory block, and its address is passed to the OS via a register.
- **Stack Method:** Parameters are pushed onto the stack, and the OS retrieves them by popping the stack.

### 2. System Call Number
- Each system call is associated with a unique number to identify the requested service.
- The system call number is stored in a CPU register before invoking the system call.

### 3. System Call Execution
- A software interrupt or **trap instruction** is executed, switching the control from user mode to kernel mode.
- The **Program Status Word (PSW)** is updated to reflect the transition to kernel mode.

### 4. Interrupt Handling
- The hardware saves the CPU’s current state (e.g., registers, program counter) to ensure the program can resume after the system call.
- The OS identifies the system call handler based on the system call number and transfers control to it.

### 5. Execution of System Call Handler
- The handler performs the requested service (e.g., reading a file, allocating memory).
- Once the service is completed, the OS restores the CPU state and prepares to return control to the user program.

### 6. Return to User Mode
- After the system call completes, control is returned to the user program, and it resumes execution in user mode.

---

## Difference Between System Call and Function Call

| **Aspect**          | **System Call**                                           | **Function Call**                                      |
|----------------------|-----------------------------------------------------------|-------------------------------------------------------|
| **Mode of Operation**| Involves switching from user mode to kernel mode.         | Operates entirely in user mode.                      |
| **Purpose**          | Invokes OS services for privileged operations.            | Executes a user-defined or library function.          |
| **Examples**         | `read()`, `write()`, `fork()`                             | `sqrt()`, `strlen()`, `printf()`                      |

---

## Types of System Calls

| **Category**        | **Description**                                                | **Examples**                     |
|---------------------|----------------------------------------------------------------|-----------------------------------|
| **Process Control** | Manage processes: creation, termination, etc.                 | `fork()`, `exec()`, `exit()`      |
| **File Management** | Manage files: opening, reading, writing, closing, etc.        | `open()`, `read()`, `write()`     |
| **Device Management**| Control devices: requesting or releasing device resources.    | `ioctl()`, `read()`, `write()`    |
| **Information Maintenance** | Retrieve or modify system/process information.         | `getpid()`, `alarm()`, `sleep()`  |
| **Communication**   | Manage inter-process communication (IPC).                     | `pipe()`, `shmget()`, `send()`    |

---

## System Call Implementation

System calls are typically written in high-level languages like C/C++. For the programmer, invoking a system call feels similar to calling a regular function, but it transitions to the **kernel**, whereas a normal function stays within **user space**.

---

## Security in System Calls

System calls ensure security by restricting direct access to critical OS components and hardware. Unauthorized programs cannot harm the system or other user processes, as the OS validates all system calls and ensures access control.

---

## System Call Example in C (UNIX/Linux)

```c
#include <stdio.h>
#include <unistd.h>

int main() {
    // Example system call: using 'write' to print to the terminal
    char *message = "Hello, System Call!\n";
    write(1, message, 18); // 1 = file descriptor for stdout
    return 0;
}
```

In this example, the `write()` system call is used to print a message to the terminal (stdout).

---

## Common System Call Flow

1. **User program** invokes a system call.
2. **System call parameters** are passed (via registers, stack, or memory).
3. A **trap instruction** switches from user mode to kernel mode.
4. The **OS processes the request** and executes the system call handler.
5. The **system call returns the result** to the user program.
6. **Control returns** to the user program in user mode.

---

## Examples of Windows and Unix System Calls

|     **Operation**      |            **Windows**              |             **Unix**               |
|------------------------|-------------------------------------|------------------------------------|
|                        |                                     |                                    |
|                        | `CreateProcess()`                   | `fork()`                           |
|  **Process Control**   | `ExitProcess()`                     | `exit()`                           |
|                        | `WaitForSingleObject()`             | `wait()`                           |
|                        |                                     |                                    |
|                        | `CreateFile()`                      | `open()`                           |
| **File Manipulation**  | `ReadFile()`                        | `read()`                           |
|                        | `WriteFile()`                       | `write()`                          |
|                        | `CloseHandle()`                     | `close()`                          |
|                        |                                     |                                    |
|                        | `SetConsoleMode()`                  | `ioctl()`                          |
| **Device Management**  | `ReadConsole()`                     | `read()`                           |
|                        | `WriteConsole()`                    | `write()`                          |
|                        |                                     |                                    |
|                        | `GetTickCount()`                    | `time()`                           |
|**Information Maintenance**| `GetCurrentProcessId()`          | `getpid()`                         |
|                        | `GetCurrentThreadId()`              | `pthread_self()`                   |
|                        |                                     |                                    |
|                        | `CreatePipe()`                      | `pipe()`                           |
|   **Communication**    | `CreateFileMapping()`               | `shmget()`                         |
|                        | `MapViewOfFile()`                   | `mmap()`                           |
|                        |                                     |                                    |
|                        | `SetFileSecurity()`                 | `chmod()`                          |
|     **Protection**     | `InitializeSecurityDescriptor()`    | `umask()`                          |
|                        | `SetSecurityDescriptorgroup()`      | `chown()`                          |


