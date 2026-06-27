### **Level 3: Log Range Extraction**

### Signature
```go
func LogRangeExtraction(timestamps []int, queries [][]int) []int

```

### The Challenge

You are building an analytics dashboard for a high-frequency trading platform. The system records every transaction with a Unix timestamp, stored sequentially in a slice called `timestamps`. Because time only moves forward, this slice is strictly sorted in **ascending order**.

Your dashboard must process a batch of `queries`. Each query is formatted as `[startTime, endTime]`. For every query, you must calculate the exact number of transactions that occurred within that time range (inclusive of both `startTime` and `endTime`).

Write a function that processes all queries and returns a slice of integers representing the transaction count for each requested time window.

### Constraints

| Property | Requirement |
| --- | --- |
| **Time Complexity** | $O(q \log n)$ — Where $q$ is the number of queries and $n$ is the number of timestamps. A linear scan to count elements for each query ($O(q \times n)$) will fail the automated performance metrics. |
| **Space Complexity** | $O(q)$ — To store and return the slice of calculated counts. |
| **Forbidden** | Do not use the `sort` package. |

### Examples

#### Example 1

* **Input:** `timestamps = [10, 20, 30, 40, 50]`
`queries = [[15, 35], [20, 20], [60, 70], [5, 45]]`
* **Output:** `[2, 1, 0, 4]`
* **Reason:**
* `[15, 35]`: The timestamps within this range are `20` and `30`. (Count: 2)
* `[20, 20]`: Only timestamp `20` matches. (Count: 1)
* `[60, 70]`: No timestamps fall in this range. (Count: 0)
* `[5, 45]`: Timestamps `10, 20, 30, 40` match. (Count: 4)



### Notes

* Do not iterate through the array to count items! Instead, use binary search twice per query:
1. Find the index of the first element $\ge startTime$ (Lower Bound).
2. Find the index of the first element $> endTime$ (Upper Bound).


* The total count of elements in the range is simply `UpperBoundIndex - LowerBoundIndex`.
* Be careful with boundary cases where the `endTime` is larger than the maximum timestamp in the array.
