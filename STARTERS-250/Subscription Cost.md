# CodeChef — 

## Problem Statement

Chef wants to subscribe to his favourite channel for `N` months.

The payment policy is:

* For the **first 3 months**, the cost is `X` rupees per month.
* For every month after the first 3 months, the cost is `Y` rupees per month.

Find the total amount Chef needs to pay.

## Input Format

* The first line contains an integer `T`, the number of test cases.
* Each test case contains three integers:

  * `N` — number of months
  * `X` — cost per month for the first 3 months
  * `Y` — cost per month after the first 3 months

## Output Format

For each test case, print the total subscription cost.

## Constraints

* `1 <= T <= 100`
* `1 <= N <= 50`
* `100 <= X < Y <= 500`

## Intuition

There are two cases depending on the subscription duration.

### If `N <= 3`

All months fall within the first 3 months, so every month costs `X`.

```text id="9q4y4k"
Total = N × X
```

### If `N > 3`

The first 3 months cost `X` each, while the remaining `N - 3` months cost `Y` each.

```text id="5lqv8b"
Total = 3 × X + (N - 3) × Y
```

## Approach

1. Read `N`, `X`, and `Y`.
2. If `N` is at most `3`, calculate `N * X`.
3. Otherwise, calculate:

   ```text
   3 * X + (N - 3) * Y
   ```
4. Print the result.

## Solution

```python id="3r2p7k"
t = int(input())

while t > 0:
    n, x, y = map(int, input().split())

    if n > 3:
        print((n - 3) * y + 3 * x)
    else:
        print(n * x)

    t -= 1
```

## Complexity

* **Time Complexity:** `O(1)` per test case
* **Space Complexity:** `O(1)`

## Example

For:

```text id="6z5b8j"
N = 5
X = 100
Y = 200
```

The first 3 months cost:

```text id="pr0u4k"
3 × 100 = 300
```

The remaining 2 months cost:

```text id="j82x2v"
2 × 200 = 400
```

Therefore:

```text id="6s9g5v"
Total = 300 + 400 = 700
```
