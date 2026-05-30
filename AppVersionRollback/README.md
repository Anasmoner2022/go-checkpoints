# App Version Rollback

## Function Signature

```go
func AppVersionRollback(builds []bool) int
```

---

## Objective

You are given a slice of boolean values called `builds`.

* `true` means the build passed.
* `false` means the build failed.

The slice follows a special rule:

```text
true true true true false false false
```

Once a build fails, all builds after it will also fail.

Your task is to find the index of the **first failed build**.

If there are no failed builds, return `-1`.

---

## Example 1

### Input

```go
builds = [true, true, true, false, false]
```

### Output

```go
3
```

### Explanation

The first `false` appears at index `3`.

---

## Example 2

### Input

```go
builds = [false, false, false]
```

### Output

```go
0
```

### Explanation

The first build already failed.

---

## Example 3

### Input

```go
builds = [true, true, true]
```

### Output

```go
-1
```

### Explanation

There are no failed builds.

---

## Example 4

### Input

```go
builds = []
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

This is a classic **Binary Search** problem.

You are not searching for a specific value.

Instead, you are searching for the **boundary** between:

```text
true true true | false false false
```

Your goal is to find the first `false`.

---

## Binary Search Logic

For a midpoint `mid`:

### If `builds[mid] == true`

You are still in the passing section.

```text
true true true [true] false false
```

The first failed build must be somewhere to the **right**.

Move your search range right.

---

### If `builds[mid] == false`

You are already in the failing section.

```text
true true [false] false false
```

The first failed build could be:

* At `mid`
* Somewhere to the left

Move your search range left.

---

## Visual Example

```text
Index:  0 1 2 3 4
Value:  T T T F F
              ^
      First failed build
```

Binary search gradually narrows the range until it finds this transition point.

---

## Common Mistakes

* Scanning the slice from left to right (`O(n)`)
* Returning the first `false` found without using binary search
* Forgetting to handle an empty slice
* Forgetting the case where all values are `true`

---

## Goal

Think of this problem as:

> "Find the first position where a condition changes from true to false."

This pattern appears frequently in binary search problems and is often called **finding a boundary** or **finding the first bad version**.
