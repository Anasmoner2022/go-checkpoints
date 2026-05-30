# Network Traffic Peak

## Function Signature

```go
func NetworkTrafficPeak(traffic []int, k int) float64
```

---

## Objective

You are given:

* A slice of integers `traffic`
* An integer `k`

Your task is to find the **maximum average value** among all contiguous subarrays of length exactly `k`.

Return the answer as a `float64`.

---

## Example 1

### Input

```go
traffic = [10, 20, 30, 40, 10, 20]
k = 3
```

### Output

```go
30.00000
```

### Explanation

All windows of size `3`:

```text
[10, 20, 30] -> sum = 60  -> average = 20.0
[20, 30, 40] -> sum = 90  -> average = 30.0
[30, 40, 10] -> sum = 80  -> average = 26.66667
[40, 10, 20] -> sum = 70  -> average = 23.33333
```

The maximum average is:

```text
30.0
```

---

## Example 2

### Input

```go
traffic = [5, 5, 5, 5]
k = 2
```

### Output

```go
5.00000
```

### Explanation

All windows have the same average:

```text
[5, 5] -> 5.0
[5, 5] -> 5.0
[5, 5] -> 5.0
```

So the answer is `5.0`.

---

## Requirements

| Requirement      | Value  |
| ---------------- | ------ |
| Time Complexity  | `O(n)` |
| Space Complexity | `O(1)` |

---

## Hint

This is a **Fixed-Size Sliding Window** problem.

The window size never changes.

It is always exactly:

```text
k
```

---

## Core Idea

First, calculate the sum of the first `k` elements.

Example:

```text
traffic = [10, 20, 30, 40, 10, 20]
k = 3

Window:
[10, 20, 30]
```

Current sum:

```text
60
```

This becomes your initial window.

---

## Moving the Window

When the window moves one position to the right:

```text
[10, 20, 30] 40 10 20
 ^
```

becomes

```text
10 [20, 30, 40] 10 20
              ^
```

Instead of recalculating the entire sum:

```text
20 + 30 + 40
```

update it using:

```text
newSum = oldSum
         - elementLeavingWindow
         + elementEnteringWindow
```

Example:

```text
60 - 10 + 40 = 90
```

This allows each window update to happen in constant time.

---

## Visual Example

```text
traffic = [10, 20, 30, 40, 10, 20]
k = 3

[10,20,30] -> sum = 60
[20,30,40] -> sum = 90
[30,40,10] -> sum = 80
[40,10,20] -> sum = 70
```

Track the maximum sum while sliding through the array.

At the end:

```text
maximum average = maximum sum / k
```

---

## Common Mistakes

* Recalculating every window sum from scratch (`O(n × k)`)
* Forgetting to update the maximum sum
* Using a variable-size window instead of a fixed-size window
* Returning the maximum sum instead of the maximum average
* Performing integer division

---

## Goal

Learn the pattern:

```text
Fixed-Size Sliding Window
```

The key observation is:

```text
When a window moves:
Remove one value
Add one value
```

This simple idea reduces the solution from `O(n × k)` to `O(n)` and appears frequently in array and interview problems involving averages, sums, and fixed-length ranges.
