# Dual Mode of Operating Systems

The dual mode operation in the OS ensures proper execution and security, allowing the system to differentiate between user processes and kernel operations.

## User Mode
- In **user mode**, the system runs user applications (e.g., file creation). However, user mode processes cannot directly access the computer's hardware.
- To perform hardware-related tasks (such as handling interrupts), the system switches to **kernel mode**. 
- The **mode bit** is set to `1` in user mode, indicating that the system is running user-level instructions.

## Kernel Mode
- In **kernel mode**, the OS performs essential low-level tasks, including hardware management and privileged instructions that require direct hardware access.
- The kernel handles processes that need hardware support, and in this mode, the mode bit is set to `0`.
- Privileged instructions, such as I/O management and handling interrupts, can only be executed in kernel mode to maintain system security.

## Switching Between User Mode and Kernel Mode
During its lifetime, a process switches between **user mode** and **kernel mode**.
- While in user mode, the process has limited access to system resources. In contrast, in kernel mode, it has unrestricted access to system resources like memory and hardware.
- In kernel mode, processes can access devices and memory. However, a crash in kernel mode can bring down the entire system.
- A crash in user mode only affects the specific faulty process, preserving the stability of the rest of the system.

## System Call Interface (SCI)
The kernel provides the **System Call Interface (SCI)**, which serves as an entry point for user processes to transition into kernel mode. **System calls** are the only way for a process to switch from user mode to kernel mode.

### Why is Switching Required?

1. **Security**: If all processes ran in a single mode, vulnerabilities in one process could compromise the entire system. Switching between user mode and kernel mode ensures processes cannot exploit system weaknesses.
   
2. **Trap Handling**: Traps (such as invalid memory access or division by zero) cause system faults or exceptions. If a process in kernel mode encounters a trap, it can crash the entire OS. However, if it occurs in user mode, only the user process crashes.
   
Switching between modes ensures a more stable and secure system by isolating user processes from critical system operations.

## Difference between User Mode and Kernel Mode

| Basis of Difference | User Mode | Kernel Mode |
| -------------------- | --------- | ----------- |
| **Modes**            | User Mode is regarded as the restricted mode or the slave mode. | Kernel Mode is considered the master mode, system mode, or the privileged mode. |
| **Definition**       | In restricted User Mode, the application programs execute and start. | The computer enters Kernel Mode, which is a privileged mode while accessing hardware resources. |
| **Interruptions**    | In case any interrupt occurs in User Mode, only one process fails. | In case an interrupt occurs in Kernel Mode, the complete operating system might fail. |
| **Restrictions**     | There are restrictions in User Mode to access kernel programs. They cannot be accessed directly. | Both kernel programs, as well as user programs, can access in Kernel Mode. |

## Comparison of Kernel Structures: Monolithic, Microkernel, and Hybrid Kernel

| Kernel Type         | Description | Advantages | Examples |
| ------------------- | ----------- | ----------- | -------- |
| **Monolithic Kernel** | All major functions (file management, memory, device management, etc.) are managed directly within the kernel. | High performance due to direct communication between components. | LINUX |
| **Microkernel**      | Only essential services (file sharing, scheduling) run in the kernel. Other services run in user space, reducing kernel size. | Simplicity, modularity, security. Easier updates and better process isolation. | Minix, Symbian OS |
| **Hybrid Kernel**    | Combines elements of monolithic and microkernel. Some essential functions run in the kernel, while others run in user space. | Combines performance of monolithic kernel and security of microkernel. Better isolation and maintainability. | macOS |
