# Missing Number

## Signature

```go
func missingNumber(nums []int) int
```

---

## The Challenge

Given a slice `nums` containing `n` distinct integers in the range `[0, n]`, return the **one number** that is missing from the sequence.

The slice holds exactly `n` elements drawn from `n+1` possible values, so exactly one value is always absent. Your solution must identify it without sorting or allocating auxiliary data structures.

---

## Constraints

| Property         | Requirement                        |
|------------------|------------------------------------|
| Time Complexity  | $O(n)$                             |
| Space Complexity | $O(1)$ extra space                 |
| Forbidden        | Do not use the `sort` package; do not use a hash map or auxiliary slice |

---

## Examples

**Example 1**
```
Input:  nums = [3, 0, 1]
Output: 2
```

**Example 2**
```
Input:  nums = [0, 1]
Output: 2
```

**Example 3**
```
Input:  nums = [9, 6, 4, 2, 3, 5, 7, 0, 1]
Output: 8
```

---

## Notes

- If `nums` is **empty** (`n = 0`), the only value in the range `[0, 0]` is `0` — return `0`.
- All values in `nums` are **distinct** and guaranteed to be in `[0, n]`; no input validation is required beyond the empty case.
- There is a well-known **mathematical property** of consecutive integers that lets you determine the expected total in $O(1)$ — compare it against the actual sum of the slice.
- An **XOR-based** approach is equally valid and avoids any risk of integer overflow on large inputs; both strategies satisfy the constraints.
