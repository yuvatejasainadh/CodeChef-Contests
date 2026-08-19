# CodeChef — IOI Gold

## Problem Statement

Chef scored `N` points in the IOI competition. The gold medal cutoff is `G` points.

Chef receives a gold medal if his score is **at least** the gold cutoff.

Given `N` and `G`, print:

* `Yes` if `N >= G`
* `No` otherwise.

## Input Format

The first and only line contains two integers `N` and `G` — Chef's score and the gold medal cutoff.

## Output Format

Print `Yes` if Chef gets a gold medal; otherwise, print `No`.

## Constraints

* `0 <= N, G <= 600`

## Intuition

To determine whether Chef gets gold, we only need to compare his score with the cutoff.

If `N` is greater than or equal to `G`, Chef qualifies for gold. Otherwise, he does not.

## Approach

1. Read `N` and `G`.
2. Check whether `N >= G`.
3. If true, print `Yes`.
4. Otherwise, print `No`.

## Solution

```python
n, g = map(int, input().split())

if n >= g:
    print("Yes")
else:
    print("No")
```

## Complexity

* **Time Complexity:** `O(1)`
* **Space Complexity:** `O(1)`
