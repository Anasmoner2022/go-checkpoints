# Top K Frequent Elements

## Signature

```go
func topKFrequent(nums []int, k int) []int
```

---

## The Challenge

Given an integer slice `nums` and an integer `k`, return the `k` most frequently occurring elements.

The answer may be returned in **any order** and is guaranteed to be unique — there is always exactly one valid set of `k` elements. Your solution must outperform a naive sort-by-frequency approach.

---

## Constraints

| Property         | Requirement                                                        |
|------------------|--------------------------------------------------------------------|
| Time Complexity  | $O(n)$ — better than $O(n \log n)$                                 |
| Space Complexity | $O(n)$                                                             |
| Forbidden        | Do not use the `sort` package; do not use a heap or priority queue |

---

## Examples

**Example 1**
```
Input:  nums = [1, 1, 1, 2, 2, 3], k = 2
Output: [1, 2]
```

**Example 2**
```
Input:  nums = [1], k = 1
Output: [1]
```

**Example 3**
```
Input:  nums = [4, 4, 4, 6, 6, 2, 2, 7], k = 3
Output: [4, 6, 2]
```

---

## Notes

- `k` is always valid: `1 <= k <= number of unique elements` — no out-of-bounds or empty-result case is possible.
- A single-element slice always returns that element; no special handling is needed beyond the general algorithm.
- The path to $O(n)$ is **bucket sort by frequency**: create a slice of buckets indexed by frequency (index `i` holds all elements that appear exactly `i` times). Since no element can appear more than `n` times, the bucket slice has a fixed size of `n+1`.
- Walk the bucket slice from **highest index to lowest**, collecting elements until you have gathered `k` values — this yields the top `k` without any comparison-based sort.
- Build a **frequency map** first in one linear pass, then populate the buckets in a second — two $O(n)$ passes remain $O(n)$
