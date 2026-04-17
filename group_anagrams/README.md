# Group Anagrams

## Signature

```go
func groupAnagrams(strs []string) [][]string
```

---

## The Challenge

Given a slice of strings `strs`, group all strings that are **anagrams of each other** into the same subslice and return all groups.

Two strings are anagrams if they contain the same characters with the same frequencies, regardless of order. The output groups may be returned in **any order**, and the strings within each group may also appear in any order.

---

## Constraints

| Property         | Requirement                                            |
|------------------|--------------------------------------------------------|
| Time Complexity  | $O(n \cdot k)$ — where $n$ is the number of strings and $k$ is the maximum string length |
| Space Complexity | $O(n \cdot k)$ — for the hash map and output storage  |
| Forbidden        | Do not use the `sort` package to sort individual strings as a grouping key |

---

## Examples

**Example 1**
```
Input:  strs = ["eat", "tea", "tan", "ate", "nat", "bat"]
Output: [["eat","tea","ate"], ["tan","nat"], ["bat"]]
```

**Example 2**
```
Input:  strs = [""]
Output: [[""]]
```

**Example 3**
```
Input:  strs = ["a"]
Output: [["a"]]
```

---

## Notes

- If `strs` is **empty**, return an empty slice — `[][]string{}`.
- A string with **no anagram partners** forms its own group of one, as shown in Examples 2 and 3.
- The key challenge is designing a **canonical key** that two strings share if and only if they are anagrams — without sorting.
- A **fixed-size frequency array** of 26 counters (one per lowercase letter) can serve as that key; convert the array to a string representation to use it as a map key in Go.
- All strings are guaranteed to contain only **lowercase English letters** — no input validation is required.
