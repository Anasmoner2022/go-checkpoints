# Memory Buffer Defragmenter

## Function Signature

```go
func MemoryBufferDefragmenter(buffer []int, targetAddress int) int
```

---

## Objective

You are given:

* A rotated sorted array `buffer`
* A target value `targetAddress`

Your task is to find the index of `targetAddress`.

Return:

* The index if the target exists
* `-1` if the target is not found

---

## What Is a Rotated Sorted Array?

A sorted array:

```text
[0, 1, 2, 4, 5, 6, 7]
```

can be rotated to become:

```text
[4, 5, 6, 7, 0, 1, 2]
```

The order is broken at one pivot point, but the array still contains two sorted sections.

---

## Example 1

### Input

```go
buffer = [4, 5, 6, 7, 0, 1, 2]
targetAddress = 0
```

### Output

```go
4
```

### Explanation

```text
[4, 5, 6, 7, 0, 1, 2]
              ^
```

The value `0` is located at index `4`.

---

## Example 2

### Input

```go
buffer = [4, 5, 6, 7, 0, 1, 2]
targetAddress = 3
```

### Output

```go
-1
```

### Explanation

The value `3` does not exist in the array.

---

## Example 3

### Input

```go
buffer = [1]
targetAddress = 1
```

### Output

```go
0
```

---

## Example 4

### Input

```go
buffer = [1]
targetAddress = 0
```

### Output

```go
-1
```

---

## Requirements

| Requirement      | Value      |
| ---------------- | ---------- |
| Time Complexity  | `O(log n)` |
| Space Complexity | `O(1)`     |

---

## Hint

This is a **Modified Binary Search** problem.

A normal binary search assumes the entire array is sorted.

Here, the array is rotated.

The trick is to notice that:

> At least one half of the current search range is always sorted.

---

## Core Idea

Calculate:

```go
mid := left + (right-left)/2
```

If:

```go
buffer[mid] == targetAddress
```

return `mid`.

Otherwise, determine which side is sorted.

---

## Case 1: Left Half Is Sorted

Example:

```text
[4, 5, 6, 7, 0, 1, 2]
       ^
      mid
```

The left side:

```text
[4, 5, 6, 7]
```

is sorted.

You can detect this using:

```go
buffer[left] <= buffer[mid]
```

Now check:

```text
Is target inside this sorted range?
```

If yes:

```text
Search Left
```

Otherwise:

```text
Search Right
```

---

## Case 2: Right Half Is Sorted

Example:

```text
[6, 7, 0, 1, 2, 4, 5]
       ^
      mid
```

The right side:

```text
[0, 1, 2, 4, 5]
```

is sorted.

Now check whether the target belongs to that range.

If yes:

```text
Search Right
```

Otherwise:

```text
Search Left
```

---

## Visual Example

Searching for:

```text
target = 0

[4, 5, 6, 7, 0, 1, 2]
       ^
      mid = 6
```

Left half is sorted:

```text
[4, 5, 6, 7]
```

Target is not inside:

```text
4 <= 0 < 7
```

Move right:

```text
[0, 1, 2]
 ^
```

Found the answer.

---

## Common Mistakes

* Using a linear scan (`O(n)`)
* Treating the array as fully sorted
* Forgetting to determine which half is sorted
* Using incorrect range checks
* Not handling single-element arrays

---

## Key Observation

Even though the entire array is not sorted:

```text
[4, 5, 6, 7, 0, 1, 2]
```

one side of every search range will always be sorted.

That property allows binary search to continue eliminating half of the remaining elements each step.

---

## Goal

Learn the pattern:

```text
Binary Search
+
Identify Sorted Half
+
Discard Half the Search Space
```

This is one of the most important binary search variations and appears frequently in technical interviews and competitive programming.
