# CodeChef — 

## Problem Statement

An array is called **good** if the parity of its elements alternates:

```text
Odd, Even, Odd, Even, ...
```

or

```text
Even, Odd, Even, Odd, ...
```

You are given an array `A` of `N` integers.

You can choose any subset of elements and rearrange the chosen elements in any order. Find the **maximum possible size** of a subset that can be rearranged into a good array.

## Input Format

* The first line contains an integer `T`, the number of test cases.
* For each test case:

  * The first line contains an integer `N`.
  * The second line contains `N` integers representing the array.

## Output Format

For each test case, print the maximum size of a subset that can be rearranged into a good array.

## Constraints

* `1 <= T <= 100`
* `1 <= N <= 100`
* `1 <= A[i] <= 100`

## Intuition

Only the **parity** of each element matters.

Let:

* `ec` = number of even elements
* `oc` = number of odd elements

For an alternating array:

* If the number of selected odd and even elements is equal, we can use all of them.
* If one parity has more elements, the difference can be at most `1`.

So:

* If `ec == oc`, we can select all `ec + oc` elements.
* Otherwise, the maximum size is:

```text
2 × min(ec, oc) + 1
```

This uses equal numbers of odd and even elements, plus one extra element from the parity that has more elements.

## Approach

1. Count the number of even and odd elements.
2. If both counts are equal, the entire array can be rearranged into an alternating array.
3. Otherwise, use:

   ```text
   2 × min(even_count, odd_count) + 1
   ```
4. Print the result.

## Solution

```python
t = int(input())

for _ in range(t):
    n = int(input())
    arr = list(map(int, input().split()))

    ec, oc = 0, 0

    for x in arr:
        if x % 2 == 0:
            ec += 1
        else:
            oc += 1

    if oc == ec:
        print(ec + oc)
    else:
        print(2 * min(ec, oc) + 1)
```

## Complexity

* **Time Complexity:** `O(N)` per test case
* **Space Complexity:** `O(N)` for storing the array

## Example

For:

```text
A = [1, 1, 2, 4]
```

There are:

```text
Odd  = 2
Even = 2
```

Since the counts are equal, all `4` elements can be rearranged as:

```text
[1, 2, 1, 4]
```

The maximum subset size is therefore:

```text
4
```
