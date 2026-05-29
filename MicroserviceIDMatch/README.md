# Microservice ID Match

## Function Signature

```go
func MicroserviceIDMatch(matrix [][]int, target int) bool
```

---

## Problem Overview

In a distributed microservice environment, service instance IDs are stored inside a structured routing matrix to enable efficient lookups across the infrastructure.

The matrix follows these ordering guarantees:

1. Every row is sorted in **ascending order** from left to right.
2. The first value of each row is always **greater** than the last value of the previous row.

Your task is to implement an efficient search function that determines whether a given `target` service ID exists inside the matrix.

Return:

* `true` if the target exists
* `false` otherwise

---

## Performance Requirements

| Requirement          | Constraint             |
| -------------------- | ---------------------- |
| **Time Complexity**  | `O(log(m × n))`        |
| **Space Complexity** | `O(1)` auxiliary space |

Where:

* `m` = number of rows
* `n` = number of columns

### Important

A full scan using nested loops (`O(m × n)`) does **not** satisfy the required performance constraints.

You must solve the problem using an optimized binary search approach without allocating additional memory or flattening the matrix.

---

## Examples

### Example 1

#### Input

```go
matrix = [
    [1,  3,  5,  7],
    [10, 11, 16, 20],
    [23, 30, 34, 60],
]

target = 3
```

#### Output

```go
true
```

---

### Example 2

#### Input

```go
matrix = [
    [1,  3,  5,  7],
    [10, 11, 16, 20],
    [23, 30, 34, 60],
]

target = 13
```

#### Output

```go
false
```

---

## Edge Cases

Your function should return `false` when:

* The matrix is empty
* The matrix contains empty rows

---

## Hint

Because of the matrix ordering rules, the entire matrix can be treated as a single sorted array.

Instead of searching row by row, perform binary search on a **virtual 1D array** of size:

```text
m × n
```

You can convert a virtual index `mid` into matrix coordinates using:

```go
row = mid / totalColumns
col = mid % totalColumns
```

This allows direct access to matrix values without modifying or copying the original data structure.
