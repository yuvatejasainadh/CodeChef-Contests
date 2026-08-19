# CodeChef — 

## Problem Statement

You are given an integer `N`.

In one operation, you can:

1. Add `1` to `N`, or
2. Replace `N` with the smallest multiple of `5` that is **strictly greater** than `N`.

The goal is to make `N` divisible by `3`.

Find the minimum number of operations required.

## Input Format

* The first line contains an integer `T`, the number of test cases.
* Each test case contains one integer `N`.

## Output Format

For each test case, print the minimum number of operations required to make `N` divisible by `3`.

## Constraints

* `1 <= T <= 100`
* `1 <= N <= 100`

## Intuition

There are only a few possibilities because we only need to make `N` divisible by `3`.

### Case 1: Already divisible by 3

If:

```text
N % 3 == 0
```

no operation is required.

Answer:

```text
0
```

### Case 2: Add 1

If:

```text
(N + 1) % 3 == 0
```

we can make `N` divisible by `3` using one operation.

Answer:

```text
1
```

### Case 3: Use the multiple-of-5 operation

The next multiple of `5` after `N` can only be a small distance away. We check whether the possible next multiples of `5` are divisible by `3`.

For the next multiple of `5` to be:

* `N + 2`, it must satisfy both `(N + 2) % 3 == 0` and `(N + 2) % 5 == 0`.
* `N + 5`, it must satisfy both `(N + 5) % 3 == 0` and `(N + 5) % 5 == 0`.

If either is possible, the answer is `1`.

### Otherwise

If none of the one-operation possibilities work, two additions of `1` are always enough because `N` is either `1` or `2` modulo `3`.

Therefore, the answer is `2`.

## Approach

1. If `N` is already divisible by `3`, print `0`.
2. Check whether adding `1` makes it divisible by `3`.
3. Check whether replacing it with the next relevant multiple of `5` makes it divisible by `3`.
4. If any one-operation solution exists, print `1`.
5. Otherwise, print `2`.

## Solution

```python
t = int(input())

while t > 0:
    n = int(input())

    if n % 3 == 0:
        print(0)

    elif (n + 1) % 3 == 0:
        print(1)

    elif (n + 2) % 3 == 0 and (n + 2) % 5 == 0:
        print(1)

    elif (n + 5) % 3 == 0 and (n + 5) % 5 == 0:
        print(1)

    else:
        print(2)

    t -= 1
```

## Complexity

* **Time Complexity:** `O(1)` per test case
* **Space Complexity:** `O(1)`

## Example

For `N = 10`:

```text
10 % 3 != 0
```

The next multiple of `5` strictly greater than `10` is `15`.

Since:

```text
15 % 3 == 0
```

one operation is enough.

Therefore, the answer is:

```text
1
```
