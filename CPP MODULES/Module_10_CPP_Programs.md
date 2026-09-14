# C++ Programs – Module 10

This module contains 3 programs from the CP-II Index: Climbing Stairs, House Robber, and Knapsack 1. The questions are based on the uploaded index (Module 10, page 4). fileciteturn5file0L191-L220

---

# Program 1: Climbing Stairs

## Question

You are climbing a staircase. It takes `n` steps to reach the top. Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

## Aim

To write a C++ program to find the number of distinct ways to climb a staircase when we can climb either 1 step or 2 steps at a time.

## Algorithm

1. Read the number of steps `n`.
2. If `n` is 1, the number of ways is 1.
3. Start with 1 way for 1 step and 2 ways for 2 steps.
4. Find each next value by adding the previous two values.
5. Print the number of ways for `n` steps.

## Program

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;

    cout << "Enter number of steps: ";
    cin >> n;

    if (n == 1) {
        cout << "Number of ways = 1" << endl;
        return 0;
    }

    int a = 1;
    int b = 2;
    int ways = 0;

    for (int i = 3; i <= n; i++) {
        ways = a + b;
        a = b;
        b = ways;
    }

    cout << "Number of ways = " << b << endl;

    return 0;
}
```

## Input

```text
Enter number of steps: 5
```

## Output

```text
Number of ways = 8
```

## Simple Explanation

For 5 steps, we can reach the top in 8 different ways.

The number of ways follows this pattern:

```text
1 step  = 1 way
2 steps = 2 ways
3 steps = 3 ways
4 steps = 5 ways
5 steps = 8 ways
```

So, the answer is `8`.

---

# Program 2: House Robber

## Question

Given an integer array `nums` representing the amount of money of each house, return the maximum amount of money you can rob tonight without alerting the police.

**Note:** Police will get alert if two adjacent houses were broken into on the same night.

## Aim

To write a C++ program to find the maximum amount of money that can be robbed without robbing two adjacent houses.

## Algorithm

1. Read the number of houses and the money in each house.
2. Keep the maximum money possible up to the previous house.
3. For each house, choose between robbing it or skipping it.
4. Update the maximum value after checking each house.
5. Print the maximum amount of money that can be robbed.

## Program

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;

    cout << "Enter number of houses: ";
    cin >> n;

    int nums[n];

    cout << "Enter money in each house: ";
    for (int i = 0; i < n; i++) {
        cin >> nums[i];
    }

    if (n == 1) {
        cout << "Maximum money = " << nums[0] << endl;
        return 0;
    }

    int previous2 = 0;
    int previous1 = 0;

    for (int i = 0; i < n; i++) {
        int rob = previous2 + nums[i];
        int skip = previous1;

        int current;

        if (rob > skip) {
            current = rob;
        } else {
            current = skip;
        }

        previous2 = previous1;
        previous1 = current;
    }

    cout << "Maximum money = " << previous1 << endl;

    return 0;
}
```

## Input

```text
Enter number of houses: 5
Enter money in each house: 2 7 9 3 1
```

## Output

```text
Maximum money = 12
```

## Simple Explanation

The houses contain:

```text
2  7  9  3  1
```

We cannot rob two adjacent houses.

One best choice is:

```text
2 + 9 + 1 = 12
```

Therefore, the maximum amount of money is `12`.

---

# Program 3: Knapsack 1

## Question

There are `N` items, numbered `1, 2, …, N`. For each `i` (`1 ≤ i ≤ N`), Item `i` has a weight of `wi` and a value of `vi`. Taro has decided to choose some of the `N` items and carry them home in a knapsack. The capacity of the knapsack is `W`, which means that the sum of the weights of items taken must be at most `W`. Find the maximum possible sum of the values of items that Taro takes home.

## Aim

To write a C++ program to find the maximum total value of items that can be placed in a knapsack without exceeding its capacity.

## Algorithm

1. Read the number of items and the knapsack capacity.
2. Read the weight and value of each item.
3. For each item, check whether it can be included in the knapsack.
4. Store the maximum value possible for each capacity.
5. Print the maximum value obtained.

## Program

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, W;

    cout << "Enter number of items: ";
    cin >> n;

    cout << "Enter knapsack capacity: ";
    cin >> W;

    int weight[n];
    int value[n];

    cout << "Enter weights of items: ";
    for (int i = 0; i < n; i++) {
        cin >> weight[i];
    }

    cout << "Enter values of items: ";
    for (int i = 0; i < n; i++) {
        cin >> value[i];
    }

    // dp[j] stores maximum value for capacity j
    int dp[W + 1] = {0};

    for (int i = 0; i < n; i++) {

        // Go backwards so that each item is used only once
        for (int j = W; j >= weight[i]; j--) {

            int include = dp[j - weight[i]] + value[i];

            if (include > dp[j]) {
                dp[j] = include;
            }
        }
    }

    cout << "Maximum value = " << dp[W] << endl;

    return 0;
}
```

## Input

```text
Enter number of items: 3
Enter knapsack capacity: 5
Enter weights of items: 2 3 4
Enter values of items: 3 4 5
```

## Output

```text
Maximum value = 7
```

## Simple Explanation

There are 3 items:

| Item | Weight | Value |
|---|---:|---:|
| 1 | 2 | 3 |
| 2 | 3 | 4 |
| 3 | 4 | 5 |

The capacity is `5`.

We can select:

- Item 1 → weight 2, value 3
- Item 2 → weight 3, value 4

Total weight:

`2 + 3 = 5`

Total value:

`3 + 4 = 7`

So, the maximum value is `7`.

---

# Quick Revision

| Program | Main Concept | Easy Idea |
|---|---|---|
| Climbing Stairs | Dynamic Programming | Add the previous two answers |
| House Robber | Dynamic Programming | Choose rob or skip each house |
| Knapsack 1 | 0/1 Dynamic Programming | Choose items without exceeding capacity |

## Important C++ Concepts Used

### 1. Array

```cpp
int nums[5];
```

Stores multiple values.

### 2. For Loop

```cpp
for (int i = 0; i < n; i++) {
    // code
}
```

Repeats a block of code.

### 3. If-Else

```cpp
if (a > b) {
    // code
} else {
    // code
}
```

Used to choose between two conditions.

### 4. Dynamic Programming

Dynamic programming stores previously calculated answers so that they can be used to solve the next part of the problem.

### 5. 0/1 Knapsack

In this problem, each item can be selected **only once** or not selected.

---

# Beginner Note

These programs are written using simple logic so they are easier to understand and explain in a practical examination. The algorithms are kept to **exactly 5 short points** for each program.
