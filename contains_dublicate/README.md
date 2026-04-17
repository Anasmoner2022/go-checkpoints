# Contains Duplicate

## Signature

```go
func containsDuplicate(nums []int) bool
```

---

## The Challenge

Given an integer slice `nums`, return `true` if **any value appears at least twice**, and `false` if every element is distinct.

Your solution must achieve the required complexity bounds without relying on sorting or any external packages.

---

## Constraints

| Property         | Requirement              |
|------------------|--------------------------|
| Time Complexity  | $O(n)$                   |
| Space Complexity | $O(n)$ extra space       |
| Forbidden        | Do not use the `sort` package |

---

## Examples

**Example 1**
```
Input:  nums = [1, 2, 3, 1]
Output: true
```

**Example 2**
```
Input:  nums = [1, 2, 3, 4]
Output: false
```

**Example 3**
```
Input:  nums = [1, 1, 1, 3, 3, 4, 3, 2, 4, 2]
Output: true
```

---

## Notes

- If `nums` is **empty** or contains a **single element**, return `false` — no duplicate can exist.
- The function must handle large slices efficiently; a nested-loop approach is not acceptable.
- Focus on a data structure that allows $O(1)$ average-case lookups.
