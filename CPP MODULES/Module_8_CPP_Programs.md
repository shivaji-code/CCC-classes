# C++ Programs – Module 8

This module contains 3 programs from the CP-II Index: Daily Temperatures, Largest Rectangle in Histogram, and Gas Station. fileciteturn5file0L138-L159

---

# Program 1: Daily Temperatures

## Question

Given an array of integer's `temperatures` represents the daily temperatures, return an array `answer` such that `answer[i]` is the number of days you have to wait after the `ith` day to get a warmer temperature. If there is no future day for which this is possible, keep `answer[i] == 0` instead.

## Aim

To write a C++ program to find how many days we have to wait to get a warmer temperature for each day.

## Algorithm

1. Read the number of days and the temperatures.
2. Start from the first day and check the following days.
3. Find the first day having a warmer temperature.
4. Store the number of days waited in the answer array.
5. Print the answer array.

## Program

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;

    cout << "Enter number of days: ";
    cin >> n;

    int temperatures[n];
    int answer[n] = {0};

    cout << "Enter temperatures: ";
    for (int i = 0; i < n; i++) {
        cin >> temperatures[i];
    }

    for (int i = 0; i < n; i++) {

        for (int j = i + 1; j < n; j++) {

            if (temperatures[j] > temperatures[i]) {
                answer[i] = j - i;
                break;
            }
        }
    }

    cout << "Answer: ";

    for (int i = 0; i < n; i++) {
        cout << answer[i] << " ";
    }

    return 0;
}
```

## Input

```text
Enter number of days: 8
Enter temperatures: 73 74 75 71 69 72 76 73
```

## Output

```text
Answer: 1 1 4 2 1 1 0 0
```

## Simple Explanation

For each day, we look at the days after it and find the first warmer temperature.

For example:

- `73` → warmer temperature `74` comes after 1 day.
- `75` → warmer temperature `76` comes after 4 days.
- `76` → no warmer temperature comes later, so the answer is `0`.

Therefore, the result is:

`1 1 4 2 1 1 0 0`

---

# Program 2: Largest Rectangle in Histogram

## Question

Given an array of integers `heights` representing the histogram's bar height where the width of each bar is 1, return the area of the largest rectangle in the histogram.

## Aim

To write a C++ program to find the largest rectangular area that can be formed in a histogram.

## Algorithm

1. Read the number of bars and their heights.
2. Select each bar one by one as the starting bar.
3. Extend the rectangle to the right while finding the smallest height.
4. Calculate the area using `height × width` and keep the maximum area.
5. Print the largest area.

## Program

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;

    cout << "Enter number of bars: ";
    cin >> n;

    int heights[n];

    cout << "Enter heights: ";
    for (int i = 0; i < n; i++) {
        cin >> heights[i];
    }

    int maxArea = 0;

    for (int i = 0; i < n; i++) {

        int minimumHeight = heights[i];

        for (int j = i; j < n; j++) {

            if (heights[j] < minimumHeight) {
                minimumHeight = heights[j];
            }

            int width = j - i + 1;
            int area = minimumHeight * width;

            if (area > maxArea) {
                maxArea = area;
            }
        }
    }

    cout << "Largest rectangle area = " << maxArea << endl;

    return 0;
}
```

## Input

```text
Enter number of bars: 6
Enter heights: 2 1 5 6 2 3
```

## Output

```text
Largest rectangle area = 10
```

## Simple Explanation

The histogram is:

```text
2 1 5 6 2 3
```

The bars with heights `5` and `6` can form a rectangle with:

- Height = `5`
- Width = `2`

Therefore:

`Area = 5 × 2 = 10`

So, the largest rectangle area is `10`.

---

# Program 3: Gas Station

## Question

Given two integer arrays `gas` and `cost`, return the starting gas station's index if you can travel around the circuit once in the clockwise direction, otherwise return `-1`. If there exists a solution, it is guaranteed to be unique.

## Aim

To write a C++ program to find the starting gas station from which we can travel around the complete circuit.

## Algorithm

1. Read the number of gas stations and the `gas` and `cost` arrays.
2. Calculate the total gas and total cost.
3. If total gas is less than total cost, print `-1`.
4. Try each station as a starting point and check whether the complete circuit is possible.
5. Print the valid starting station index.

## Program

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;

    cout << "Enter number of gas stations: ";
    cin >> n;

    int gas[n];
    int cost[n];

    cout << "Enter gas values: ";
    for (int i = 0; i < n; i++) {
        cin >> gas[i];
    }

    cout << "Enter cost values: ";
    for (int i = 0; i < n; i++) {
        cin >> cost[i];
    }

    int totalGas = 0;
    int totalCost = 0;

    for (int i = 0; i < n; i++) {
        totalGas += gas[i];
        totalCost += cost[i];
    }

    if (totalGas < totalCost) {
        cout << "Starting station = -1" << endl;
        return 0;
    }

    int start = -1;

    for (int i = 0; i < n; i++) {

        int fuel = 0;
        bool possible = true;

        for (int j = 0; j < n; j++) {

            int station = (i + j) % n;

            fuel = fuel + gas[station] - cost[station];

            if (fuel < 0) {
                possible = false;
                break;
            }
        }

        if (possible) {
            start = i;
            break;
        }
    }

    cout << "Starting station = " << start << endl;

    return 0;
}
```

## Input

```text
Enter number of gas stations: 5
Enter gas values: 1 2 3 4 5
Enter cost values: 3 4 5 1 2
```

## Output

```text
Starting station = 3
```

## Simple Explanation

Start from station `3`.

The available gas and cost allow us to travel:

`3 → 4 → 0 → 1 → 2 → 3`

We have enough fuel at every station and can complete the full circuit.

Therefore, the starting station is:

`3`

---

# Quick Revision

| Program | Main Concept | Easy Idea |
|---|---|---|
| Daily Temperatures | Array searching | Find the next warmer day |
| Largest Rectangle in Histogram | Nested loops | Find the largest height × width |
| Gas Station | Arrays + simulation | Check a starting station and travel around |

## Important C++ Concepts Used

### 1. Array

```cpp
int gas[5];
```

Stores multiple values.

### 2. Nested Loop

A loop inside another loop is used to check multiple elements.

### 3. Modulo `%`

```cpp
int station = (i + j) % n;
```

The modulo operator helps us move back to the first station after reaching the last station.

### 4. Boolean

```cpp
bool possible = true;
```

Stores either `true` or `false`.

### 5. Area Formula

For a rectangle:

```text
Area = Height × Width
```

This formula is used in the histogram problem.

---

# Beginner Note

All programs are written using simple logic so they are easy to read, understand, and explain in a practical examination. Each algorithm contains **exactly 5 short points**.
