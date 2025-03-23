# Paging

## Definition:
Paging is a memory management scheme where a process is divided into fixed-size pages, and memory is divided into fixed-size frames. Pages of a process can be stored in different locations in memory, allowing non-contiguous allocation. Paging eliminates external fragmentation but may lead to internal fragmentation.

## Steps in Paging:
1. Divide the process into fixed-size pages.
2. Map each page to available memory frames.
3. Load only the required pages into memory, leaving the rest in secondary storage.
4. If a needed page is not in memory, a page fault occurs, and the operating system loads it into a free frame.

---

# Virtual Memory

## Definition:
Virtual Memory creates the illusion of a large, continuous memory by using a portion of secondary memory (like a hard disk) as an extension of the main memory (RAM). Processes are divided into pages, and only the needed pages are loaded into main memory, increasing the degree of multiprogramming.

## How Virtual Memory Works:
- When a program is too large to fit into the physical memory, only a portion of the program is loaded, allowing the rest to reside in secondary storage (disk).
- **Page Faults** occur when the system tries to access a page not currently in memory. The OS then loads the missing page, possibly replacing an existing page in memory using a page replacement algorithm.

---

# Demand Paging

## Definition:
Demand Paging is a virtual memory management technique where pages are loaded into memory only when they are needed. If a page is not available in memory, a page fault occurs, and the required page is brought in from secondary storage.

## Advantages:
- **Efficient use of memory**: Only the required pages are loaded, reducing memory usage.
- **Supports running large applications**: Allows large applications to run on systems with limited RAM.

## Disadvantages:
- **Can slow down system performance**: Frequent page faults may degrade performance.
- **Swapping between secondary storage and main memory introduces latency**: Data has to be fetched from slower storage, which increases delays.
