### **Level 1: Memory Pointer Snap**

### Signature
```go
func MemoryPointerSnap(addresses []int, queries []int) []int

```

### The Challenge

You are writing a memory allocation manager for a virtual machine. You are given an array called `addresses` which contains the starting byte sizes of available memory blocks. This array is strictly sorted in **ascending order**.

You are also given an array of `queries`, representing incoming requests from applications needing a specific amount of memory.

For each query, you must find the **minimum index** of an available memory block that is **greater than or equal to** the requested size (i.e., the closest block to the right). If no memory block is large enough to handle the query, record `-1` for that specific request.

Write a function that processes all queries and returns a slice of integers containing the corresponding indices.

### Constraints

| Property | Requirement |
| --- | --- |
| **Time Complexity** | O(q log n) — Where q is the number of queries and n is the number of addresses. Scanning the array linearly for every query O(q * n) will fail the automated performance benchmark. |
| **Space Complexity** | O(q) — To store the output slice of results. |
| **Forbidden** | Do not use the `sort.Search` package to bypass writing the algorithm manually. |

### Examples

#### Example 1

* **Input:** `addresses = [2, 4, 8, 16, 32]`, `queries = [3, 16, 40, 1]`
* **Output:** `[1, 3, -1, 0]`
* **Reason:**
* Query `3`: The smallest block 3 is `4` (at index 1).
* Query `16`: Exact match for `16` (at index 3).
* Query `40`: No block is 40, so return `-1`.
* Query `1`: The smallest block 1 is `2` (at index 0).



### Notes

* Watch your binary search boundaries carefully. You are looking for a **lower bound** (the first element that satisfies the condition), not just an exact match.
