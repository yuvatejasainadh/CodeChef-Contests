# CodeChef — 

## Problem Statement

You have `K` coins and `N` items arranged in a fixed order.

The `i`-th item costs `A[i]` coins. You must buy items in order:

```text
1, 2, 3, ..., N
```

If you skip an item, you cannot buy any item after it.

You also have a **one-time coupon** that can make one item completely free.

Find the maximum number of consecutive items you can buy starting from the first item.

## Input Format

* The first line contains an integer `T`, the number of test cases.
* For each test case:

  * The first line contains two integers `N` and `K`.
  * The second line contains `N` integers representing the costs of the items.

## Output Format

For each test case, print the maximum number of items Chef can buy.

## Constraints

* `1 <= T <= 10^4`
* `2 <= N <= 2 * 10^5`
* `1 <= A[i] <= 10^4`
* `1 <= K <= 10^9`
* The sum of `N` over all test cases does not exceed `2 * 10^5`

## Intuition

Since we must buy items from the beginning, for every prefix of the array we need to determine whether it can be purchased.

The coupon should always be used on the **most expensive item** in the prefix because that gives the maximum possible saving.

For a prefix:

```text
Total Cost = sum of all items
Minimum Cost with Coupon = Total Cost - maximum item
```

If this effective cost is at most `K`, we can buy the entire prefix.

Once a prefix becomes unaffordable, adding more positive-cost items cannot make it affordable again, so we can stop.

## Approach

1. Read `N`, `K`, and the array.
2. Maintain:

   * `curr_sum` — total cost of the current prefix.
   * `max_val` — maximum cost in the current prefix.
   * `max_items` — maximum number of items we can buy.
3. For every item:

   * Add its cost to `curr_sum`.
   * Update `max_val`.
   * Calculate the cost after applying the coupon:

     ```text
     effective_cost = curr_sum - max_val
     ```
4. If `effective_cost <= K`, update the answer.
5. Otherwise, stop because no longer prefix can be affordable.
6. Print the maximum number of items.

## Solution

```python
t = int(input())

for _ in range(t):
    n, k = map(int, input().split())
    arr = list(map(int, input().split()))

    max_items = 0
    curr_sum = 0
    max_val = 0

    for i in range(n):
        cost = arr[i]

        curr_sum += cost

        if cost > max_val:
            max_val = cost

        effective_cost = curr_sum - max_val

        if effective_cost <= k:
            max_items = i + 1
        else:
            break

    print(max_items)
```

## Complexity

* **Time Complexity:** `O(N)` per test case
* **Space Complexity:** `O(N)` for storing the array

## Example

Consider:

```text
N = 7
K = 11
A = [1, 2, 3, 4, 5, 6, 1]
```

For the first `5` items:

```text
Total = 1 + 2 + 3 + 4 + 5 = 15
Maximum = 5
Cost after coupon = 15 - 5 = 10
```

Since `10 <= 11`, all first `5` items can be purchased.

For the first `6` items:

```text
Total = 21
Maximum = 6
Cost after coupon = 21 - 6 = 15
```

Since `15 > 11`, we cannot buy `6` items.

Therefore, the answer is:

```text
5
```
