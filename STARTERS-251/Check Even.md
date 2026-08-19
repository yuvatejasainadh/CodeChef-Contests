# CodeChef — 

## Problem Statement

You are given two integers `L` and `R`.

You have all integers from `L` to `R`, inclusive:

```text
L, L+1, L+2, ..., R
```

Determine whether there is **at least one even integer** in this range.

An integer is even if it is divisible by `2`.

Print:

* `Yes` if the range contains an even number.
* `No` otherwise.

## Input Format

The only line contains two space-separated integers `L` and `R`.

## Output Format

Print `Yes` if there exists an even integer between `L` and `R`; otherwise, print `No`.

## Constraints

* `1 <= L <= R <= 10`

## Intuition

If `L` and `R` are different, the range contains at least two consecutive integers. Among any two consecutive integers, one must be even.

Therefore, the only case where the answer can be `No` is when:

```text
L == R
```

In that case, we simply check whether the single number is odd.

## Approach

1. Read `L` and `R`.
2. If `L == R` and `L` is odd, there is no even number, so print `No`.
3. Otherwise, print `Yes`.

## Solution

```python
a, b = map(int, input().split())

if a == b and a % 2 == 1:
    print("No")
else:
    print("Yes")
```

## Complexity

* **Time Complexity:** `O(1)`
* **Space Complexity:** `O(1)`

## Example

For:

```text
L = 3, R = 5
```

The numbers are:

```text
3, 4, 5
```

Since `4` is even, the answer is:

```text
Yes
```

For:

```text
L = 5, R = 5
```

The only number is `5`, which is odd, so:

```text
No
```
