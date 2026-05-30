# Log Timestamp Lookup

## Function Signature

```go
func LogTimestampLookup(logs []int64, target int64) int
```

---

## Objective

You are given:

* A sorted slice of integers called `logs`
* A target value called `target`

Your task is to find the index of the **first element that is greater than or equal to `target`**.

Return:

* The index of the first value `>= target`
* `-1` if no such value exists

---

## Example 1

### Input

```go
logs = [1715000000, 1715000010, 1715000020, 1715000030]
target = 1715000015
```

### Output

```go
2
```

### Explanation

```text
1715000000 1715000010 1715000020 1715000030
                        ^
```

`1715000020` is the first value that is greater than or equal to `1715000015`.

---

## Example 2

### Input

```go
logs = [1715000000, 1715000010, 1715000020, 1715000030]
target = 1715000010
```

### Output

```go
1
```

### Explanation

There is an exact match at index `1`.

---

## Example 3

### Input

```go
logs = [1715000000, 1715000010]
target = 1715005000
```

### Output

```go
-1
```

### Explanation

All values are smaller than the target.

---

## Example 4

### Input

```go
logs = []
target = 100
```

### Output

```go
-1
```

### Explanation

The slice is empty.

---

## Requirements

| Requirement      | Value      |
| ---------------- | ---------- |
| Time Complexity  | `O(log n)` |
| Space Complexity | `O(1)`     |

---

## Hint

This is a **Binary Search** problem.

Unlike classic binary search, you are not looking for an exact value.

You are looking for the **first position where the value becomes greater than or equal to the target**.

This pattern is commonly called:

```text
Lower Bound
```

---

## Core Idea

At each step, check the middle element.

### If `logs[mid] < target`

```text
[1 3 5 7 9]
       ^
target = 8
```

Everything up to `mid` is too small.

Search the right half.

---

### If `logs[mid] >= target`

```text
[1 3 5 7 9]
     ^
target = 5
```

This position could be the answer.

However, there might be an earlier valid position.

Continue searching the left half.

---

## Visual Example

For:

```text
logs = [1, 3, 5, 7, 9]
target = 6
```

The answer is:

```text
1 3 5 7 9
      ^
```

Index `3`, because `7` is the first value that is greater than or equal to `6`.

---

## Common Mistakes

* Using a linear scan (`O(n)`)
* Returning only exact matches
* Stopping immediately after finding a valid value
* Forgetting the case where no valid answer exists
* Using `mid := (left + right) / 2` without considering overflow

---

## Goal

Learn the pattern:

```text
Binary Search
+
Find First Valid Position
```

This "lower bound" technique appears frequently in search problems and is one of the most useful variations of binary search.

Mastering it will make problems like insertion position, first occurrence, and boundary searching much easier.
