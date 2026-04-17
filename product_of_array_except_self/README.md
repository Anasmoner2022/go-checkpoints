# Product of Array Except Self

## Signature

```go
func productExceptSelf(nums []int) []int
```

---

## The Challenge

Given an integer slice `nums`, return a slice `output` where `output[i]` is the **product of every element in `nums` except `nums[i]`**.

The result must be computed without using division and in a single algorithmic pass over the data. You must not rely on a total-product-then-divide strategy — it breaks on zero and is explicitly off-limits.

---

## Constraints

| Property         | Requirement                                                              |
|------------------|--------------------------------------------------------------------------|
| Time Complexity  | $O(n)$                                                                   |
| Space Complexity | $O(1)$ extra space — the output slice does not count toward this limit   |
| Forbidden        | Do not use division; do not use the `math` or `sort` package             |

---

## Examples

**Example 1**
```
Input:  nums = [1, 2, 3, 4]
Output: [24, 12, 8, 6]
Reason: output[0] = 2×3×4, output[1] = 1×3×4, output[2] = 1×2×4, output[3] = 1×2×3
```

**Example 2**
```
Input:  nums = [-1, 1, 0, -3, 3]
Output: [0, 0, 9, 0, 0]
```

**Example 3**
```
Input:  nums = [2, 3, 4, 5]
Output: [60, 40, 30, 24]
```

---

## Notes

- The input slice will always contain **at least two elements** — no empty or single-element edge case applies.
- The slice **may contain zeros** — division-based approaches silently fail here; the prefix/suffix strategy handles zeros correctly with no special casing.
- The core insight is that `output[i]` equals the **product of all elements to the left** of `i` multiplied by the **product of all elements to the right** of `i`.
- Compute the **prefix products** left-to-right directly into the output slice (first pass), then multiply in the **suffix products** right-to-left using a single running variable (second pass) — no auxiliary array needed.
- Two $O(n)$ passes with $O(1)$ extra space satisfy both constraints simultaneously.
