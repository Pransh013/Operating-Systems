# Page Replacement Algorithms

When a page fault occurs and memory is full, the OS needs to decide which page to remove to make space for the required page. Page replacement algorithms help determine which page to evict to reduce the total number of page faults and improve system performance.

---

## 1. FIFO (First-In-First-Out) Page Replacement

### Description:
In FIFO, the oldest page (the one loaded first) is removed from memory when a new page needs to be loaded. It's simple but not always optimal, as pages loaded early might still be heavily used.

### Steps:
- When a new page arrives, it is added to the end of the queue.
- If the memory is full, the first page in the queue (oldest page) is removed.
- The new page is placed at the end of the queue.

### Example:
- **Reference String**: 1, 2, 3, 4, 1, 2, 5, 1, 2, 3, 4, 5
- **Number of Frames**: 3

| Step | Reference | Frames (after page load) | Page Fault? |
|------|-----------|--------------------------|-------------|
| 1    | 1         | 1 - -                    | Yes         |
| 2    | 2         | 1 2 -                    | Yes         |
| 3    | 3         | 1 2 3                    | Yes         |
| 4    | 4         | 4 2 3 (Replace 1)        | Yes         |
| 5    | 1         | 1 2 3 (Replace 4)        | Yes         |
| 6    | 2         | 1 2 3                    | No          |
| 7    | 5         | 5 2 3 (Replace 1)        | Yes         |
| 8    | 1         | 1 2 3 (Replace 5)        | Yes         |

**Total Page Faults**: 9

---

## 2. LRU (Least Recently Used) Page Replacement

### Description:
In LRU, the page that has not been used for the longest time is replaced. This approach assumes that pages used recently are likely to be used again soon.

### Steps:
- Track the usage history of pages.
- When a page needs to be replaced, select the page that has not been accessed for the longest time.
- Update the usage information after every page access.

### Example:
- **Reference String**: 1, 2, 3, 4, 1, 2, 5, 1, 2, 3, 4, 5
- **Number of Frames**: 3

| Step | Reference | Frames (after page load) | Page Fault? |
|------|-----------|--------------------------|-------------|
| 1    | 1         | 1 - -                    | Yes         |
| 2    | 2         | 1 2 -                    | Yes         |
| 3    | 3         | 1 2 3                    | Yes         |
| 4    | 4         | 4 2 3 (Replace 1)        | Yes         |
| 5    | 1         | 1 2 3 (Replace 4)        | Yes         |
| 6    | 2         | 1 2 3                    | No          |
| 7    | 5         | 5 2 3 (Replace 1)        | Yes         |
| 8    | 1         | 1 2 3 (Replace 5)        | Yes         |

**Total Page Faults**: 9

---

## 3. Optimal Page Replacement

### Description:
The Optimal algorithm replaces the page that will not be used for the longest time in the future. This is the most efficient algorithm, but it is not feasible in practice because it requires future knowledge of memory access patterns.

### Steps:
- When a page needs to be replaced, look ahead at the reference string to find the page that will be used farthest in the future.
- Replace the page that will not be needed for the longest time.

### Example:
- **Reference String**: 1, 2, 3, 4, 1, 2, 5, 1, 2, 3, 4, 5
- **Number of Frames**: 3

| Step | Reference | Frames (after page load) | Page Fault? |
|------|-----------|--------------------------|-------------|
| 1    | 1         | 1 - -                    | Yes         |
| 2    | 2         | 1 2 -                    | Yes         |
| 3    | 3         | 1 2 3                    | Yes         |
| 4    | 4         | 4 2 3 (Replace 1)        | Yes         |
| 5    | 1         | 1 2 3 (Replace 4)        | Yes         |
| 6    | 2         | 1 2 3                    | No          |
| 7    | 5         | 5 2 3 (Replace 1)        | Yes         |
| 8    | 1         | 5 1 3 (Replace 2)        | Yes         |

**Total Page Faults**: 8

---

## Comparison of Page Replacement Algorithms

| Algorithm | Strategy                               | Advantage                               | Disadvantage                        |
|-----------|----------------------------------------|-----------------------------------------|-------------------------------------|
| FIFO      | Replace the oldest page               | Simple to implement                    | Can lead to high page faults (Belady’s anomaly) |
| LRU       | Replace the least recently used page  | Efficient for real-world scenarios     | Requires tracking usage history, can be costly |
| Optimal   | Replace the page needed farthest in the future | Minimizes page faults                  | Not practical, requires future knowledge |
