# CodeChef — 

## Problem Statement

There are `N` boxes containing chocolates. The `i`-th box contains `A[i]` chocolates.

The players follow these rules:

* If the **total remaining chocolates are even**, it is Alice's turn.
* If the **total remaining chocolates are odd**, it is Bob's turn.
* On a turn, the player must choose a non-empty box and eat any positive number of chocolates from it.
* Players do not alternate turns automatically. The next player is determined only by the parity of the total remaining chocolates.

Both players play optimally to maximize the total number of chocolates they eat.

Find the number of chocolates Alice will eat.

## Input Format

* The first line contains an integer `T`, the number of test cases.
* For each test case:

  * The first line contains an integer `N`.
  * The second line contains `N` integers representing the chocolates in each box.

## Output Format

For each test case, print the maximum number of chocolates Alice can eat under optimal play.

## Constraints

* `1 <= T <= 100`
* `1 <= N <= 100`
* `1 <= A[i] <= 100`

## Intuition

Only the **parity of the boxes** matters for deciding whose turn it is.

Consider the boxes containing an odd number of chocolates.

Let:

```text
c_odd = number of odd-valued boxes
```

### When `c_odd` is even

The total number of chocolates is even, so Alice gets the opportunity to consume chocolates from the even-sized portions.

For every box:

```text
even_part = A[i] - (A[i] % 2)
```

This represents the largest even amount that can be taken from that box.

Alice can collect all these even portions. The remaining odd chocolates come in pairs, and Alice can optimally obtain one chocolate from each pair.

Therefore:

```text
Alice's score = sum of even parts + c_odd / 2
```

### When `c_odd` is odd

There is an odd number of odd boxes. Under optimal play, Bob can control the game so that Alice can only obtain one chocolate for every pair of odd boxes.

Therefore:

```text
Alice's score = c_odd // 2
```

## Approach

1. Count the number of odd elements in the array.
2. If the number of odd elements is even:

   * Calculate the sum of the even parts of all boxes.
   * Add `c_odd // 2`.
3. If the number of odd elements is odd:

   * Alice's score is `c_odd // 2`.
4. Print Alice's score.

## Solution

```python
t = int(input())

while t > 0:
    n = int(input())
    A = list(map(int, input().split()))

    c_odd = sum(1 for x in A if x % 2 != 0)

    if c_odd % 2 == 0:
        even_parts = sum(x - (x % 2) for x in A)
        alice_score = even_parts + (c_odd // 2)
    else:
        alice_score = c_odd // 2

    print(alice_score)

    t -= 1
```

## Complexity

* **Time Complexity:** `O(N)` per test case
* **Space Complexity:** `O(N)` for storing the array

## Example

For:

```text
A = [3, 3]
```

Both elements are odd, so:

```text
c_odd = 2
```

Since `c_odd` is even:

```text
even_parts = 2 + 2 = 4
c_odd // 2 = 1
```

Therefore:

```text
Alice's score = 4 + 1 = 5
```

So Alice can eat a maximum of `5` chocolates.
