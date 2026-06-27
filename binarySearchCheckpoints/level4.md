### **Level 4: System Uptime Delta**

### Signature
```go
func SystemUptimeDelta(bootTime string, crashTime string) int

```

### The Challenge

You are writing a kernel diagnostic tool that calculates the total uptime of a server cluster. The system logs the exact date the server booted (`bootTime`) and the exact date the server experienced a critical failure (`crashTime`).

Both dates are provided as strings strictly formatted as `YYYY:MM:DD` (e.g., `2024:02:28`).

Write a function that calculates and returns the **exact number of days** that elapsed between the `bootTime` and the `crashTime`.

### Constraints

| Property | Requirement |
| --- | --- |
| **Time Complexity** | $O(1)$ — Parsing the string and calculating the mathematical delta should execute in constant time. |
| **Space Complexity** | $O(1)$ auxiliary space. |
| **Forbidden** | You must not use the `time` package. You must implement the calendar math from scratch. |

### Examples

#### Example 1

* **Input:** `bootTime = "1900:01:01"`, `crashTime = "2038:12:31"`
* **Output:** `50768`
* **Reason:** This represents the maximum uptime calculation spanning multiple leap years and century exceptions.

#### Example 2

* **Input:** `bootTime = "1991:11:12"`, `crashTime = "1996:03:09"`
* **Output:** `1579`

#### Example 3

* **Input:** `bootTime = "2024:02:28"`, `crashTime = "2024:03:01"`
* **Output:** `2`
* **Reason:** 2024 is a leap year, meaning February has 29 days. The days elapsed are Feb 28 -> Feb 29 (1) -> Mar 1 (2).

### Notes

* The Gregorian calendar rules for leap years are as follows:
1. If a year is exactly divisible by 4, it is a leap year.
2. **Except** if it is exactly divisible by 100, then it is **not** a leap year.
3. **Unless** it is exactly divisible by 400, in which case it **is** a leap year.


* `crashTime` is guaranteed to be chronologically greater than or equal to `bootTime`.
