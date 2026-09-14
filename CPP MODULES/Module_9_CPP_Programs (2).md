# C++ Programs – Module 9

## 1. Find Common Elements Between Two Arrays

### Question

You are given two integer arrays `nums1` and `nums2` of sizes `n` and `m`, respectively.

Calculate:

- `answer1`: the number of indices `i` such that `nums1[i]` exists in `nums2`.
- `answer2`: the number of indices `i` such that `nums2[i]` exists in `nums1`.

Return `[answer1, answer2]`.

### Aim

To write a C++ program to find how many elements of the first array are present in the second array and how many elements of the second array are present in the first array.

### Algorithm

1. Read the first array.
2. Read the second array.
3. Search each element of the first array in the second array and count it.
4. Search each element of the second array in the first array and count it.
5. Print `answer1` and `answer2`.

### Program

```cpp
#include <iostream>
using namespace std;

int main() {
    int n, m;

    cout << "Enter size of first array: ";
    cin >> n;

    int nums1[n];

    cout << "Enter elements of first array: ";
    for (int i = 0; i < n; i++) {
        cin >> nums1[i];
    }

    cout << "Enter size of second array: ";
    cin >> m;

    int nums2[m];

    cout << "Enter elements of second array: ";
    for (int i = 0; i < m; i++) {
        cin >> nums2[i];
    }

    int answer1 = 0;
    int answer2 = 0;

    // Check elements of nums1 in nums2
    for (int i = 0; i < n; i++) {
        bool found = false;

        for (int j = 0; j < m; j++) {
            if (nums1[i] == nums2[j]) {
                found = true;
                break;
            }
        }

        if (found) {
            answer1++;
        }
    }

    // Check elements of nums2 in nums1
    for (int i = 0; i < m; i++) {
        bool found = false;

        for (int j = 0; j < n; j++) {
            if (nums2[i] == nums1[j]) {
                found = true;
                break;
            }
        }

        if (found) {
            answer2++;
        }
    }

    cout << "Answer1 = " << answer1 << endl;
    cout << "Answer2 = " << answer2 << endl;

    return 0;
}
```

### Input

```text
Enter size of first array: 4
Enter elements of first array: 1 2 3 4
Enter size of second array: 5
Enter elements of second array: 2 4 5 6 7
```

### Output

```text
Answer1 = 2
Answer2 = 2
```

### Simple Explanation

The common elements are `2` and `4`.

Therefore:

- `answer1 = 2`
- `answer2 = 2`

---

## 2. Contains Duplicate

### Question

Given an integer array `nums`, return `true` if any value appears at least twice in the array, and return `false` if every element is distinct.

### Aim

To write a C++ program to check whether an array contains any duplicate element.

### Algorithm

1. Read the size and elements of the array.
2. Compare each element with the elements after it.
3. Check whether any two elements are equal.
4. If equal elements are found, set the duplicate value to `true`.
5. Print `true` if a duplicate exists, otherwise print `false`.

### Program

```cpp
#include <iostream>
using namespace std;

int main() {
    int n;

    cout << "Enter size of array: ";
    cin >> n;

    int nums[n];

    cout << "Enter elements of array: ";
    for (int i = 0; i < n; i++) {
        cin >> nums[i];
    }

    bool duplicate = false;

    // Compare every pair of elements
    for (int i = 0; i < n; i++) {
        for (int j = i + 1; j < n; j++) {
            if (nums[i] == nums[j]) {
                duplicate = true;
                break;
            }
        }

        if (duplicate) {
            break;
        }
    }

    if (duplicate) {
        cout << "true" << endl;
    } else {
        cout << "false" << endl;
    }

    return 0;
}
```

### Input

```text
Enter size of array: 5
Enter elements of array: 1 2 3 2 5
```

### Output

```text
true
```

### Simple Explanation

The number `2` occurs two times in the array.

So, the array contains a duplicate and the answer is `true`.

---

## 3. Sort Characters By Frequency

### Question

Given a string `s`, sort it in decreasing order based on the frequency of the characters.

The frequency of a character is the number of times it appears in the string.

Return the sorted string. If there are multiple valid answers, any one of them can be returned.

### Aim

To write a C++ program to arrange the characters of a string according to their frequency, from highest frequency to lowest frequency.

### Algorithm

1. Read the string.
2. Count the frequency of each character.
3. Find the character with the highest frequency.
4. Add that character to the result according to its frequency and mark it as processed.
5. Repeat for all characters and print the result.

### Program

```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string s;

    cout << "Enter a string: ";
    cin >> s;

    // Store frequency of each character
    int frequency[256] = {0};

    // Count each character
    for (int i = 0; i < s.length(); i++) {
        frequency[(unsigned char)s[i]]++;
    }

    string result = "";

    // Find the character with highest frequency
    for (int count = 0; count < s.length(); count++) {

        int maxFrequency = 0;
        int character = -1;

        for (int i = 0; i < 256; i++) {
            if (frequency[i] > maxFrequency) {
                maxFrequency = frequency[i];
                character = i;
            }
        }

        if (character == -1) {
            break;
        }

        // Add the character according to its frequency
        for (int j = 0; j < maxFrequency; j++) {
            result += char(character);
        }

        // Mark character as processed
        frequency[character] = 0;
    }

    cout << "Sorted string: " << result << endl;

    return 0;
}
```

### Input

```text
Enter a string: tree
```

### Output

```text
Sorted string: eetr
```

### Simple Explanation

In `tree`:

- `e` occurs 2 times.
- `t` occurs 1 time.
- `r` occurs 1 time.

So, `e` is printed first. One valid result is `eetr`.

---

# Quick Revision

| Program | Main Concept |
|---|---|
| Find Common Elements Between Two Arrays | Array searching |
| Contains Duplicate | Comparing array elements |
| Sort Characters By Frequency | Frequency counting |

## Beginner C++ Concepts Used

### Array

```cpp
int nums[5];
```

Stores multiple values.

### For Loop

```cpp
for (int i = 0; i < n; i++) {
    // code
}
```

Repeats a block of code.

### Nested Loop

A loop inside another loop. It is used here to compare array elements.

### Boolean

```cpp
bool found = false;
```

Stores either `true` or `false`.

### String

```cpp
string s;
```

Stores a sequence of characters.

### Frequency Array

```cpp
int frequency[256] = {0};
```

Stores how many times each character occurs.
