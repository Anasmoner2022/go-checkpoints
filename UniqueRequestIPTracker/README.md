# Unique Request IP Tracker

## Function Signature

```go
func UniqueRequestIPTracker(stream string) int
```

---

## Objective

You are given a string `stream`.

Your task is to find the length of the **longest substring** that contains **no repeated characters**.

A substring is a continuous sequence of characters inside a string.

Return the length of the longest valid substring.

---

## Example 1

### Input

```go
stream = "abcabcbb"
```

### Output

```go
3
```

### Explanation

Possible substrings without repeating characters include:

```text
"abc"
"bca"
"cab"
```

All have length `3`, which is the maximum.

---

## Example 2

### Input

```go
stream = "bbbbb"
```

### Output

```go
1
```

### Explanation

The only valid substrings are:

```text
"b"
```

So the answer is `1`.

---

## Example 3

### Input

```go
stream = "pwwkew"
```

### Output

```go
3
```

### Explanation

The longest valid substring is:

```text
"wke"
```

Length = `3`

Note that `"pwke"` is not a substring because the characters are not continuous in the original string.

---

## Example 4

### Input

```go
stream = ""
```

### Output

```go
0
```

### Explanation

An empty string contains no characters.

---

## Requirements

| Requirement      | Value          |
| ---------------- | -------------- |
| Time Complexity  | `O(n)`         |
| Space Complexity | `O(min(n, m))` |

Where:

* `n` is the length of the string
* `m` is the number of possible characters

---

## Hint

This problem uses a **Sliding Window + Hash Map**.

You will need:

* A `left` pointer
* A `right` pointer
* A map that stores the most recent index of each character

---

## Core Idea

Expand the window using the `right` pointer.

If the current character has not appeared inside the current window:

```text
abcde
```

keep expanding.

---

### What happens when a duplicate appears?

Example:

```text
abca
   ^
```

The character `'a'` already exists in the current window.

Instead of removing characters one by one, move the `left` pointer directly after the previous `'a'`.

```text
abca
 ^
```

becomes

```text
bca
```

This is the key optimization that keeps the solution linear.

---

## Visual Example

For:

```text
abcabcbb
```

Window growth:

```text
[a]        -> 1
[ab]       -> 2
[abc]      -> 3
[abca]     -> duplicate 'a'
 [bca]     -> continue
```

Keep updating the maximum window size seen so far.

---

## Common Mistakes

* Generating all possible substrings (`O(n²)`)
* Resetting the window when a duplicate is found
* Moving the left pointer backwards
* Forgetting to update the maximum length
* Using a set and removing characters one by one instead of jumping directly

---

## Goal

Learn the pattern:

```text
Sliding Window
+
Map of Last Seen Positions
```

This is one of the most important interview patterns and appears in many variations involving strings, arrays, and unique elements.

Once you understand this problem, you'll be ready for more advanced sliding window challenges involving frequencies, counts, and dynamic constraints.
