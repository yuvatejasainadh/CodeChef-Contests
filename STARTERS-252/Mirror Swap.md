# CodeChef — 

## Problem Statement

You are given an array `A` of size `2N`.

You can perform the following operation any number of times:

* Swap `A[i]` with its mirror element `A[2N - i - 1]`.

Your goal is to **maximize the sum of the first `N` elements** of the array.

For every mirrored pair, you can choose which of the two values should be placed in the first half. Therefore, the maximum contribution from each pair is the larger value.

## Input Format

* The first line contains an integer `T`, the number of test cases.
* For each test case:

  * The first line contains an integer `N`.
  * The second line contains `2N` integers representing the array.

## Output Format

For each test case, print the maximum possible sum of the first `N` elements.

## Constraints

* `1 <= T <= 100`
* `1 <= N <= 100`
* `1 <= A[i] <= 100`

## Intuition

The array consists of `N` mirrored pairs:

```text
A[0]       ↔ A[2N-1]
A[1]       ↔ A[2N-2]
A[2]       ↔ A[2N-3]
...
A[N-1]     ↔ A[N]
```

Each pair contains exactly one element that will contribute to the first-half sum.

Since we can swap the two elements, we should always place the **larger value** in the first half.

Therefore, for every `i` from `0` to `N-1`, take:

```text
max(A[i], A[2N-i-1])
```

and add it to the answer.

## Approach

1. Read `N` and the array.
2. Iterate through the first `N` elements.
3. For each index `i`, find its mirror index:

   ```python
   2 * n - i - 1
   ```
4. If the mirrored element is larger, swap the two elements.
5. After processing all mirrored pairs, the first `N` elements contain the maximum possible values.
6. Sum the first `N` elements and print the result.

## Solution

```python
t = int(input())

for _ in range(t):
    n = int(input())
    arr = list(map(int, input().split()))

    for i in range(n):
        if arr[i] < arr[(2 * n) - i - 1]:
            arr[i], arr[(2 * n) - i - 1] = arr[(2 * n) - i - 1], arr[i]

    print(sum(arr[:n]))
```

## Complexity

* **Time Complexity:** `O(N)` per test case
* **Space Complexity:** `O(N)` for storing the array

## Example

For:

```text
N = 3
A = [1, 4, 3, 4, 2, 1]
```

The mirrored pairs are:

```text
(1, 1) → max = 1
(4, 2) → max = 4
(3, 4) → max = 4
```

So the maximum first-half sum is:

```text
1 + 4 + 4 = 9
```

> Note: The provided explanation appears to contain a typo saying `99`; the correct answer for the sample is `9`.
