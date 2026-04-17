# Find All Duplicates

## Signature

```go
func findDuplicates(nums []int) []int
```

---

## The Challenge

Given an integer slice `nums` of length `n` where every element satisfies `1 <= nums[i] <= n`, return all elements that appear **exactly twice**.

Each value either appears once or twice — no value appears more than twice. Your solution must not allocate any auxiliary data structure; the input slice itself is the only workspace available.

---

## Constraints

| Property         | Requirement                                                      |
|------------------|------------------------------------------------------------------|
| Time Complexity  | $O(n)$                                                           |
| Space Complexity | $O(1)$ extra space — the output slice does not count toward this limit |
| Forbidden        | Do not use the `sort` package; do not allocate a hash map, frequency array, or any auxiliary slice |

---

## Examples

**Example 1**
```
Input:  nums = [4, 3, 2, 7, 8, 2, 3, 1]
Output: [2, 3]
```

**Example 2**
```
Input:  nums = [1, 1, 2]
Output: [1]
```

**Example 3**
```
Input:  nums = [1]
Output: []
```

---

## Notes

- If `nums` is **empty** or contains a **single element**, no duplicates can exist — return an empty slice.
- The returned slice may list duplicates in **any order**; no specific ordering is required.
- The constraint `1 <= nums[i] <= n` is the critical enabler: every value is a valid **index** into the slice when decremented by one. Use this to your advantage.
- The classic $O(1)$-space technique treats the **sign of each element** as a visited flag: when processing value `v`, negate `nums[abs(v)-1]`. If that position is already negative, `abs(v)` has been seen before — it is a duplicate.
- You may temporarily mutate `nums` during processing; the sign-flip approach leaves all absolute values intact, so the data is not permanently destroyed.
- `abs()` is not in Go's standard library for integers — implement it inline or as a small helper.
