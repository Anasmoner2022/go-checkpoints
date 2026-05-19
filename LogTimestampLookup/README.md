## Log Timestamp Lookup

### Signature
```go
func LogTimestampLookup(logs []int64, target int64) int

```

### The Challenge

You are building a high-performance telemetry tool for a DevOps monitoring stack. Your system receives a massive slice of Unix timestamps representing server log entries.

Because logs are recorded chronologically as they happen, the input slice `logs` is **guaranteed to be sorted in ascending order**.

Your task is to write a function that finds the index of the **first log entry** that occurred **exactly at or immediately after** a specific `target` timestamp. If all logs in the system occurred before the target timestamp, return `-1`.

### Constraints

| Property | Requirement |
| --- | --- |
| **Time Complexity** | O(\log n) — Linear scans (O(n)) will instantly fail the performance audit. |
| **Space Complexity** | O(1) auxiliary space — You must not allocate slices, maps, or strings. |
| **Forbidden** | Do not use the built-in `sort` or `slices` packages. |

### Examples

#### Example 1

* **Input:** `logs = [1715000000, 1715000010, 1715000020, 1715000030]`, `target = 1715000015`
* **Output:** `2`
* **Reason:** The log at index 2 (`1715000020`) is the first entry that is greater than or equal to `1715000015`.

#### Example 2

* **Input:** `logs = [1715000000, 1715000010, 1715000020, 1715000030]`, `target = 1715000010`
* **Output:** `1`
* **Reason:** There is an exact match at index 1.

#### Example 3

* **Input:** `logs = [1715000000, 1715000010]`, `target = 1715005000`
* **Output:** `-1`
* **Reason:** All logs occurred before the target timestamp.

### Notes

* An empty `logs` slice contains no records — return `-1`.
* Watch out for integer overflow when calculating midpoints in binary search. Use a memory-safe arithmetic strategy.
