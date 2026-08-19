# CodeChef — 

## Problem Statement

A bus has `N` rows, and each row contains `M` seats.

The seats are numbered consecutively from the front to the back. Given your seat number `X`, determine the row containing your seat.

You can enter the bus from either:

* The **front**, or
* The **back**

Find the minimum number of rows you need to walk through, **including the destination row**.

## Input Format

* The first line contains an integer `T`, the number of test cases.
* Each test case contains three integers:

  * `N` — number of rows
  * `M` — seats per row
  * `X` — your seat number

## Output Format

For each test case, print the minimum number of rows you need to walk through.

## Constraints

* `1 <= T <= 1000`
* `1 <= N, M <= 100`
* `1 <= X <= N * M`

## Intuition

Each row contains `M` seats.

Therefore, the row containing seat `X` is:

```text
row = (X - 1) // M + 1
```

Once we know the row, we can calculate the distance from both entrances.

### From the front

If the seat is in row `row`, we need to walk through:

```text
row
```

rows.

### From the back

There are `N - row + 1` rows from the back to the destination row.

So the answer is:

```text
min(row, N - row + 1)
```

## Approach

1. Read `N`, `M`, and `X`.
2. Find the destination row:

   ```python
   row = (X - 1) // M + 1
   ```
3. Calculate the number of rows from the front:

   ```text
   row
   ```
4. Calculate the number of rows from the back:

   ```text
   N - row + 1
   ```
5. Print the smaller value.

## Solution

```python
t = int(input())

while t > 0:
    n, m, x = map(int, input().split())

    row = (x - 1) // m + 1

    print(min(row, n - row + 1))

    t -= 1
```

## Complexity

* **Time Complexity:** `O(1)` per test case
* **Space Complexity:** `O(1)`

## Example

For:

```text
N = 4
M = 2
X = 5
```

The rows are:

```text
Row 1 → seats 1, 2
Row 2 → seats 3, 4
Row 3 → seats 5, 6
Row 4 → seats 7, 8
```

Seat `5` is in row `3`.

From the front:

```text
3 rows
```

From the back:

```text
4 - 3 + 1 = 2 rows
```

Therefore:

```text
min(3, 2) = 2
```

So the answer is `2`.
