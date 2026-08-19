# CodeChef — 

## Problem Statement

Chef needs to give a presentation that lasts exactly **10 minutes**, which is `600` seconds.

Each slide takes exactly **30 seconds** to present.

Chef has already prepared `N` slides. Find how many additional slides he needs to prepare so that the presentation lasts exactly 10 minutes.

## Input Format

The only line contains an integer `N` — the number of slides Chef has already prepared.

## Output Format

Print the number of additional slides Chef needs to prepare.

## Constraints

* `0 <= N <= 20`

## Intuition

The presentation needs to last `600` seconds.

Each slide takes `30` seconds, so the total number of slides required is:

```text
600 / 30 = 20
```

Chef already has `N` slides.

Therefore, the number of additional slides required is:

```text
20 - N
```

## Approach

1. Read `N`.
2. Calculate `20 - N`.
3. Print the result.

## Solution

```python
n = int(input())

print(20 - n)
```

## Complexity

* **Time Complexity:** `O(1)`
* **Space Complexity:** `O(1)`

## Example

If Chef already has `10` slides:

```text
Required slides = 20
Existing slides = 10

Additional slides = 20 - 10 = 10
```

Therefore, the answer is:

```text
10
```
