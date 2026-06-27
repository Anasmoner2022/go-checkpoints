### **Level 5: Bandwidth Allocation**

### Signature
```go
func BandwidthAllocation(loads []int, clusters int) int

```

### The Challenge

You are a site reliability engineer managing network traffic. An array called `loads` represents a sequential stream of incoming traffic requests (measured in megabytes) hitting your gateway.

You must partition this sequential stream into exactly `clusters` number of contiguous sub-segments, routing each segment to a different backend data center.

To prevent any single data center from melting down under pressure, your goal is to distribute the data as evenly as possible. Specifically, you must **minimize the maximum traffic load** assigned to any single data center. Write a function that calculates and returns this minimized maximum load.

### Constraints

| Property | Requirement |
| --- | --- |
| **Time Complexity** | $O(n \log(\text{sum} - \text{max}))$ — Where $n$ is the length of the loads slice, $\text{sum}$ is the total load, and $\text{max}$ is the single largest load. Backtracking or recursion ($O(n^k)$) will instantly fail the performance audit. |
| **Space Complexity** | $O(1)$ auxiliary space. |
| **Forbidden** | You must not use the `math` or `sort` packages. |

### Examples

#### Example 1

* **Input:** `loads = [7, 2, 5, 10, 8]`, `clusters = 2`
* **Output:** `18`
* **Reason:** There are four ways to split this array into 2 contiguous clusters:
1. `[7]` and `[2, 5, 10, 8]` (Max load: 25)
2. `[7, 2]` and `[5, 10, 8]` (Max load: 23)
3. `[7, 2, 5]` and `[10, 8]` (Max load: 18)
4. `[7, 2, 5, 10]` and `[8]` (Max load: 24)
The setup that produces the smallest maximum load is option 3, with a load of `18`.



#### Example 2

* **Input:** `loads = [1, 2, 3, 4, 5]`, `clusters = 2`
* **Output:** `9`
* **Reason:** Split into `[1, 2, 3]` (sum 6) and `[4, 5]` (sum 9). The maximum is 9.

### Notes

* **The Search Space:** The absolute smallest possible answer is the largest single element in the array (because a cluster must hold at least one element). The absolute largest possible answer is the sum of all elements (if `clusters == 1`).
* Apply Binary Search to this range of *possible loads*. For every `mid` value you test, run a greedy loop over the array to see if you can successfully partition the `loads` into the required number of `clusters` without exceeding `mid`.
