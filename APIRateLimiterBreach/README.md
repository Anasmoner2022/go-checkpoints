# API Rate Limiter Breach

## Function Signature

```go
func APIRateLimiterBreach(requests []int, threshold int) int
```

---

## Objective

You are given:

* A slice called `requests`
* An integer called `threshold`

Each value in `requests` represents the number of API requests received during one second.

Your task is to find the **smallest number of continuous seconds** whose total requests are greater than or equal to `threshold`.

Return:

* The minimum length of the sub-slice
* `0` if no valid sub-slice exists

---

## Example 1

### Input

```go
requests = [2, 3, 1, 2, 4, 3]
threshold = 7
```

### Output

```go
2
```

### Explanation

Possible valid sub-slices:

```text
[2,3,1,2] => 8
[1,2,4]   => 7
[4,3]     => 7
```

The shortest one is:

```text
[4,3]
```

Its length is `2`.

---

## Example 2

### Input

```go
requests = [1, 4, 4]
threshold = 4
```

### Output

```go
1
```

### Explanation

The value `[4]` alone already reaches the threshold.

---

## Example 3

### Input

```go
requests = [1, 1, 1, 1, 1]
threshold = 10
```

### Output

```go
0
```

### Explanation

The total sum is only `5`, so no valid sub-slice exists.

---

## Requirements

| Requirement      | Value  |
| ---------------- | ------ |
| Time Complexity  | `O(n)` |
| Space Complexity | `O(1)` |

---

## Hint

This problem is solved using the **Sliding Window** technique.

Use:

* A `left` pointer
* A `right` pointer
* A running `sum`

### Idea

1. Move `right` to expand the window.
2. Add values to the current sum.
3. When the sum becomes greater than or equal to `threshold`:

   * Update the minimum length
   * Move `left` to shrink the window
4. Continue until the end of the slice.

---

## Important Note

All numbers are positive integers.

That means:

* Expanding the window increases the sum
* Shrinking the window decreases the sum

This makes the sliding window approach very efficient.

---

## Common Mistakes

* Using nested loops (`O(n²)`)
* Recalculating the sum every time
* Resetting pointers incorrectly
* Forgetting to update the minimum length before shrinking the window

---

## Goal

Build a solution where both pointers move only forward.

If your implementation is correct, the total operations will stay linear: `O(n)`.

Sliding window looks confusing at first… then suddenly it clicks and you start using it everywhere like a new programming superpower.
