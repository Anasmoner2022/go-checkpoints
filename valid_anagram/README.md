# Valid Anagram

## Signature

```go
func isAnagram(s string, t string) bool
```

---

## The Challenge

Given two strings `s` and `t`, return `true` if `t` is an **anagram** of `s`, and `false` otherwise.

An anagram is a word formed by rearranging the letters of another, using **every original letter exactly once**. Both strings are assumed to contain only lowercase English letters.

---

## Constraints

| Property         | Requirement                    |
|------------------|--------------------------------|
| Time Complexity  | $O(n)$                         |
| Space Complexity | $O(1)$ extra space             |
| Forbidden        | Do not use the `sort` package  |

> **Note on space:** Since the input is restricted to 26 lowercase English letters, a fixed-size frequency array counts as $O(1)$ space regardless of input length.

---

## Examples

**Example 1**
```
Input:  s = "anagram", t = "nagaram"
Output: true
```

**Example 2**
```
Input:  s = "rat", t = "car"
Output: false
```

**Example 3**
```
Input:  s = "listen", t = "silent"
Output: true
```

---

## Notes

- If `s` and `t` differ in **length**, return `false` immediately — no further processing is needed.
- If either string is **empty**, return `true` only if both are empty.
- Your solution should perform a **single pass** (or two linear passes at most) — avoid any $O(n^2)$ character comparison approach.
- Think about how a **fixed-size array** indexed by character value can track letter frequencies efficiently.
