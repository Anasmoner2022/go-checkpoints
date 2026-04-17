# Longest Consecutive Sequence

## Signature

```go
func longestConsecutive(nums []int) int
```

---

## The Challenge

Given an unsorted integer slice `nums`, return the length of the **longest sequence of consecutive integers** present in the slice.

Consecutive means values that form an unbroken chain (e.g., `4, 5, 6, 7`), but the elements do not need to be adjacent or ordered in the input. Your solution must achieve $O(n)$ time — a sort-based approach that achieves $O(n \log n)$ is not acceptable.

---

## Constraints

| Property         | Requirement                                                   |
|------------------|---------------------------------------------------------------|
| Time Complexity  | $O(n)$                                                        |
| Space Complexity | $O(n)$                                                        |
| Forbidden        | Do not use the `sort` package; do not use any $O(n \log n)$ strategy |

---

## Examples

**Example 1**
```
Input:  nums = [100, 4, 200, 1, 3, 2]
Output: 4
Reason: The longest consecutive sequence is [1, 2, 3, 4]
```

**Example 2**
```
Input:  nums = [0, 3, 7, 2, 5, 8, 4, 6, 0, 1]
Output: 9
Reason: The longest consecutive sequence is [0, 1, 2, 3, 4, 5, 6, 7, 8]
```

**Example 3**
```
Input:  nums = [9, 1, 4, 7, 3, -1, 0, 5, 8, -1, 6]
Output: 7
Reason: Unique values are {-1,0,1} and {3,4,5,6,7,8,9} — the longer chain is [3,4,5,6,7,8,9]
```

---

## Notes

- If `nums` is **empty**, return `0` — no sequence exists.
- **Duplicate values** are valid input and must be handled gracefully; duplicates do not extend a sequence.
- The key insight is to avoid reprocessing. Load all values into a **hash set** for $O(1)$ lookups, then for each number `n`, only begin counting a sequence if `n-1` is **not** present in the set — this marks `n` as the true start of a sequence.
- By only starting counts at sequence beginnings, each element is visited at most twice across the entire algorithm — once during the outer scan and once during a forward walk — keeping the total work $O(n)$.
- Negative integers are valid input, as shown in Example 3.
