# CodeChef — 

## Problem Statement

You are given two cells on an `8 × 8` chessboard.

A bishop can move any number of cells along a diagonal in a single move.

There are two types of diagonals:

* Cells where `x + y` is constant.
* Cells where `x - y` is constant.

Given the starting cell `(X1, Y1)` and destination cell `(X2, Y2)`, find the minimum number of bishop moves required to reach the destination.

If the destination cannot be reached, print `-1`.

## Input Format

* The first line contains an integer `T`, the number of test cases.
* Each test case contains four integers:

  * `X1`, `Y1` — starting cell
  * `X2`, `Y2` — destination cell

## Output Format

For each test case, print:

* `0` if both cells are the same.
* `1` if both cells lie on the same diagonal.
* `2` if they can be connected through another diagonal.
* `-1` if the destination is unreachable.

## Constraints

* `1 <= T <= 100`
* `1 <= X1, Y1, X2, Y2 <= 8`
* `(X1, Y1) != (X2, Y2)`

## Intuition

A bishop can only move between cells of the **same color**.

The color of a chessboard cell depends on the parity of `x + y`.

Therefore, if:

```text
(X1 + Y1) % 2 != (X2 + Y2) % 2
```

the cells have different colors, so the bishop can never reach the destination.

If they have the same color, there are three possibilities.

### Same cell

If both coordinates are equal, no move is needed.

### Same diagonal

Two cells are on the same diagonal if either:

```text
X1 + Y1 == X2 + Y2
```

or:

```text
X1 - Y1 == X2 - Y2
```

In this case, the bishop can reach the destination in one move.

### Otherwise

If the cells have the same color but are not on the same diagonal, a bishop can always reach the destination in **2 moves** on a standard chessboard.

## Approach

1. Compare the parity of `X1 + Y1` and `X2 + Y2`.
2. If the parity differs, print `-1`.
3. If the starting and destination cells are the same, print `0`.
4. If either diagonal condition matches, print `1`.
5. Otherwise, print `2`.

## Solution

```python
t = int(input())

while t > 0:
    x1, y1, x2, y2 = map(int, input().split())

    if (x1 + y1) % 2 != (x2 + y2) % 2:
        print(-1)

    elif x1 == x2 and y1 == y2:
        print(0)

    elif (x1 + y1 == x2 + y2) or (x1 - y1 == x2 - y2):
        print(1)

    else:
        print(2)

    t -= 1
```

## Complexity

* **Time Complexity:** `O(1)` per test case
* **Space Complexity:** `O(1)`

## Example

For:

```text
(1, 2) → (7, 8)
```

We have:

```text
1 + 2 = 3
7 + 8 = 15
```

Both cells have the same parity, and:

```text
1 + 2 = 7 + 8
```

So they lie on the same diagonal.

Therefore, the answer is:

```text
1
```

For:

```text
(1, 2) → (2, 2)
```

The parities are different:

```text
1 + 2 = 3  → odd
2 + 2 = 4  → even
```

A bishop cannot change the color of its square, so the answer is:

```text
-1
```
