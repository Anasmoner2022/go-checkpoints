### **Level 2: The Drone Intercept**

### Signature
```go
func DroneIntercept(jammers [][]int, target []int) bool

```

### The Challenge

You are operating an automated delivery drone on an infinite 2D coordinate grid. The drone always powers on and starts its flight at the origin coordinates `[0, 0]`. You are given a `target` destination formatted as `[x_target, y_target]`.

The airspace is monitored by mobile signal jammers. The starting coordinates of these jammers are provided in a 2D array called `jammers`, where `jammers[i] = [x_i, y_i]`.

Every tick (turn) of the system clock, both the drone and all jammers can independently move 1 unit in any of the four cardinal directions (North, South, East, West).

A jammer successfully intercepts the drone if it can reach the `target` destination **before or at the exact same time** as the drone. Return `true` if it is mathematically guaranteed that the drone can reach the target safely, and `false` if any jammer can intercept it.

### Constraints

| Property | Requirement |
| --- | --- |
| **Time Complexity** | $O(j)$ — where $j$ is the number of jammers.  |
| **Space Complexity** | $O(1)$ auxiliary space. |
| **Forbidden** | You must not use the `math` package. |

### Examples

#### Example 1

* **Input:** `jammers = [[1, 0], [0, 3]]`, `target = [0, 1]`
* **Output:** `true`
* **Reason:** The drone needs 1 move to reach `(0, 1)`. The closest jammer at `(1, 0)` needs 2 moves. The drone arrives first safely.

#### Example 2

* **Input:** `jammers = [[1, 0]]`, `target = [2, 0]`
* **Output:** `false`
* **Reason:** The drone needs 2 moves to reach `(2, 0)`. The jammer at `(1, 0)` only needs 1 move to get there and wait for the drone. Intercepted.

#### Example 3

* **Input:** `jammers = [[2, 0]]`, `target = [1, 0]`
* **Output:** `false`
* **Reason:** The drone and the jammer both require 1 move to reach `(1, 0)`. Because they arrive at the same time, the intercept is successful.

### Notes

* Because the drone and jammers can only move in cardinal directions (not diagonally), the shortest path between any two points is the **Manhattan Distance**:
$Distance = |x_1 - x_2| + |y_1 - y_2|$
* Since the `math` package is forbidden, you must implement your own logic to calculate the absolute value of coordinate differences to prevent negative distances.

