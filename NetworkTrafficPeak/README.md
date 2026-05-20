## Network Traffic Peak

### Signature
```go
func NetworkTrafficPeak(traffic []int, k int) float64

```

### The Challenge

You are working on an internal monitoring system for a core network router. The router logs the total volume of network traffic (in megabytes) processed every second as an element in an integer slice called `traffic`.

To identify spike patterns, you need to calculate the **maximum average data throughput** sustained over any continuous window of exactly `k` seconds.

Write a function that calculates this maximum average value and returns it as a floating-point number (`float64`).

### Constraints

| Property | Requirement |
| --- | --- |
| **Time Complexity** | O(n) — You must traverse the array in a single pass. Recalculating the sum for every window from scratch (O(n*k)) will fail the performance test. |
| **Space Complexity** | O(1) auxiliary space — Modifying the data structure or allocating arrays/slices is strictly forbidden. |
| **Input Bounds** | `k` will always be greater than 0, and less than or equal to the total length of the `traffic` slice. |

### Examples

#### Example 1

* **Input:** `traffic = [10, 20, 30, 40, 10, 20]`, `k = 3`
* **Output:** `30.00000`
* **Reason:**
The contiguous windows of size 3 are:
* `[10, 20, 30]` -> Average = 20.0
* `[20, 30, 40]` -> Average = 30.0
* `[30, 40, 10]` -> Average = 26.66667
* `[40, 10, 20]` -> Average = 23.33333
The maximum sustained average is `30.0`.



#### Example 2

* **Input:** `traffic = [5, 5, 5, 5]`, `k = 2`
* **Output:** `5.00000`
* **Reason:** All windows of size 2 have a total sum of 10 and an average of 5.0.

### Notes

* Because the output requires floating-point precision, make sure to explicitly cast your calculated integer sums to `float64` before dividing by `k` to prevent decimal truncation.
* **Sliding Window Principle:** Do not sum up all `k` elements every time the window moves down the array. Instead, subtract the element leaving the window on the left, and add the new element entering the window on the right.
