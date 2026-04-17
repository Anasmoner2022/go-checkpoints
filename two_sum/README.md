# Two Sum

## Signature

```go
func twoSum(nums []int, target int) []int
```

---

## The Challenge

Given an integer slice `nums` and an integer `target`, return the **indices** of the two numbers that add up to `target`.

You may assume that exactly one valid answer exists, and you may not use the same element twice. The returned indices can be in any order.

---

## Constraints

| Property         | Requirement                        |
|------------------|------------------------------------|
| Time Complexity  | $O(n)$                             |
| Space Complexity | $O(n)$ extra space                 |
| Forbidden        | Do not use the `sort` package; do not use a nested loop ($O(n^2)$ brute force is not acceptable) |

---

## Examples

**Example 1**
```
Input:  nums = [2, 7, 11, 15], target = 9
Output: [0, 1]
Reason: nums[0] + nums[1] = 2 + 7 = 9
```

**Example 2**
```
Input:  nums = [3, 2, 4], target = 6
Output: [1, 2]
Reason: nums[1] + nums[2] = 2 + 4 = 6
```

**Example 3**
```
Input:  nums = [3, 3], target = 6
Output: [0, 1]
Reason: nums[0] + nums[1] = 3 + 3 = 6
```

---

## Notes

- The problem **guarantees** exactly one valid solution — no need to handle the case where no answer exists.
- You may **not** use the same index twice (e.g., using `nums[0]` twice to hit a target of `4` when `nums = [2, 3]` is invalid).
- For each element, think about what value you need to **complete the pair** — and whether you have seen it before.
- A **hash map** storing `value → index` allows you to answer that question in $O(1)$ per element, driving the overall solution to $O(n)$.
- Duplicate values (as in Example 3) are valid inputs — your map must store indices, not just values, and must not overwrite a previous entry before checking against it.
