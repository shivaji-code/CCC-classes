# CP-II Module 3 & 4 Programs

## Module 3

### 3.1 Find First and Last Position of Element in Sorted Array

**Question:** Given an array of integers nums sorted in non-decreasing order, find the starting and ending position of a given target value. If the target is not found in the array, return [-1, -1]. You must write an algorithm with O(log n) runtime complexity.

**Aim:** To write a C++ program to find the first and last position of a given element in a sorted array using binary search.

**Algorithm**
1. Read the number of elements n.
2. Read the sorted array.
3. Read the target element.
4. Use binary search to find the target.
5. When the target is found, store its position.
6. Continue searching on the left side to find the first position.
7. Continue searching on the right side to find the last position.
8. If the target is not found, print -1 -1.
9. Otherwise, print the first and last positions.

**Program**
```cpp
#include <iostream>
using namespace std;

int main()
{
    int n, i, target;
    int a[100];

    cout << "Enter number of elements: ";
    cin >> n;

    cout << "Enter sorted elements: ";
    for(i = 0; i < n; i++)
    {
        cin >> a[i];
    }

    cout << "Enter target element: ";
    cin >> target;

    // Find first position
    int low = 0;
    int high = n - 1;
    int first = -1;

    while(low <= high)
    {
        int mid = (low + high) / 2;

        if(a[mid] == target)
        {
            first = mid;
            high = mid - 1;
        }
        else if(a[mid] < target)
        {
            low = mid + 1;
        }
        else
        {
            high = mid - 1;
        }
    }

    // Find last position
    low = 0;
    high = n - 1;
    int last = -1;

    while(low <= high)
    {
        int mid = (low + high) / 2;

        if(a[mid] == target)
        {
            last = mid;
            low = mid + 1;
        }
        else if(a[mid] < target)
        {
            low = mid + 1;
        }
        else
        {
            high = mid - 1;
        }
    }

    cout << "First position = " << first << endl;
    cout << "Last position = " << last << endl;

    return 0;
}
```

**Input**
```
Enter number of elements: 7
Enter sorted elements: 2 4 4 4 6 8 9
Enter target element: 4
```

**Output**
```
First position = 1
Last position = 3
```

---

### 3.2 Search in Rotated Sorted Array

**Question:** There is an integer array nums sorted in ascending order. Given the array nums after the possible rotation and an integer target, return the index of target if it is in nums, or -1 if it is not in nums. You must write an algorithm with O(log n) runtime complexity.

**Aim:** To write a C++ program to search for an element in a rotated sorted array using binary search.

**Algorithm**
1. Read the number of elements.
2. Read the rotated sorted array.
3. Read the target element.
4. Set low = 0 and high = n - 1.
5. Find the middle element.
6. If the middle element is the target, print its position.
7. Check which half of the array is sorted.
8. If the target is present in the sorted half, search that half.
9. Otherwise, search the other half.
10. Repeat until the target is found or the search range becomes empty.
11. If the target is not found, print -1.

**Program**
```cpp
#include <iostream>
using namespace std;

int main()
{
    int n, i, target;
    int a[100];

    cout << "Enter number of elements: ";
    cin >> n;

    cout << "Enter rotated sorted elements: ";
    for(i = 0; i < n; i++)
    {
        cin >> a[i];
    }

    cout << "Enter target element: ";
    cin >> target;

    int low = 0;
    int high = n - 1;
    int position = -1;

    while(low <= high)
    {
        int mid = (low + high) / 2;

        if(a[mid] == target)
        {
            position = mid;
            break;
        }

        // Left half is sorted
        if(a[low] <= a[mid])
        {
            if(target >= a[low] && target < a[mid])
            {
                high = mid - 1;
            }
            else
            {
                low = mid + 1;
            }
        }

        // Right half is sorted
        else
        {
            if(target > a[mid] && target <= a[high])
            {
                low = mid + 1;
            }
            else
            {
                high = mid - 1;
            }
        }
    }

    cout << "Position = " << position << endl;

    return 0;
}
```

**Input**
```
Enter number of elements: 7
Enter rotated sorted elements: 6 7 8 1 2 3 4
Enter target element: 3
```

**Output**
```
Position = 5
```

---

### 3.3 Search a 2D Matrix

**Question:** You are given an m x n integer matrix with the following two properties: Each row is sorted in non-decreasing order. The first integer of each row is greater than the last integer of the previous row. Given an integer target, return true if target is in matrix or false otherwise. You must write a solution in O(log(m * n)) time complexity.

**Aim:** To write a C++ program to search for an element in a sorted 2D matrix using binary search.

**Algorithm**
1. Read the number of rows and columns.
2. Read the matrix elements.
3. Read the target element.
4. Consider the complete matrix as one sorted array.
5. Set low = 0 and high = rows × columns - 1.
6. Find the middle position.
7. Convert the middle position into row and column.
8. Compare the matrix element with the target.
9. If equal, the target is found.
10. If the target is smaller, search the left part.
11. If the target is larger, search the right part.
12. If the search ends without finding the target, print false.

**Program**
```cpp
#include <iostream>
using namespace std;

int main()
{
    int rows, cols;
    int a[10][10];
    int target;

    cout << "Enter number of rows: ";
    cin >> rows;

    cout << "Enter number of columns: ";
    cin >> cols;

    cout << "Enter matrix elements: ";
    for(int i = 0; i < rows; i++)
    {
        for(int j = 0; j < cols; j++)
        {
            cin >> a[i][j];
        }
    }

    cout << "Enter target element: ";
    cin >> target;

    int low = 0;
    int high = rows * cols - 1;
    bool found = false;

    while(low <= high)
    {
        int mid = (low + high) / 2;

        int row = mid / cols;
        int col = mid % cols;

        if(a[row][col] == target)
        {
            found = true;
            break;
        }
        else if(a[row][col] < target)
        {
            low = mid + 1;
        }
        else
        {
            high = mid - 1;
        }
    }

    if(found == true)
    {
        cout << "Target found" << endl;
    }
    else
    {
        cout << "Target not found" << endl;
    }

    return 0;
}
```

**Input**
```
Enter number of rows: 3
Enter number of columns: 4
Enter matrix elements:
1 3 5 7
10 11 16 20
23 30 34 60
Enter target element: 16
```

**Output**
```
Target found
```

---

## Module 4

### 4.1 Minimum Moves to Equal Array Elements

**Question:** Given an integer array nums of size n, return the minimum number of moves required to make all array elements equal. In one move, you can increment n - 1 elements of the array by 1.

**Aim:** To write a C++ program to find the minimum number of moves required to make all elements of an array equal.

**Algorithm**
1. Read the number of elements.
2. Read the array elements.
3. Find the smallest element in the array.
4. For every element, find the difference between that element and the smallest element.
5. Add all the differences.
6. The obtained sum is the minimum number of moves.
7. Display the result.

**Program**
```cpp
#include <iostream>
using namespace std;

int main()
{
    int n;
    int a[100];

    cout << "Enter number of elements: ";
    cin >> n;

    cout << "Enter array elements: ";
    for(int i = 0; i < n; i++)
    {
        cin >> a[i];
    }

    // Find the smallest element
    int small = a[0];

    for(int i = 1; i < n; i++)
    {
        if(a[i] < small)
        {
            small = a[i];
        }
    }

    // Find minimum moves
    int moves = 0;

    for(int i = 0; i < n; i++)
    {
        moves = moves + (a[i] - small);
    }

    cout << "Minimum number of moves = " << moves << endl;

    return 0;
}
```

**Input**
```
Enter number of elements: 4
Enter array elements: 1 2 3 4
```

**Output**
```
Minimum number of moves = 6
```

---

### 4.2 Kth Largest Element in an Array

**Question:** Given an integer array nums and an integer k, return the kth largest element in the array. Note that it is the kth largest element in the sorted order, not the kth distinct element. Can you solve it without sorting?

**Aim:** To write a C++ program to find the kth largest element in an array without using sorting.

**Algorithm**
1. Read the number of elements.
2. Read the array elements.
3. Read the value of k.
4. Find the largest element in the array.
5. Count it as the first largest element.
6. After finding a largest element, mark that element as already selected.
7. Find the next largest element.
8. Repeat this process until the kth largest element is found.
9. Display the kth largest element.

**Program**
```cpp
#include <iostream>
using namespace std;

int main()
{
    int n, k;
    int a[100];

    cout << "Enter number of elements: ";
    cin >> n;

    cout << "Enter array elements: ";
    for(int i = 0; i < n; i++)
    {
        cin >> a[i];
    }

    cout << "Enter k: ";
    cin >> k;

    int answer = 0;

    for(int count = 1; count <= k; count++)
    {
        int max = -999999;
        int position = 0;

        for(int i = 0; i < n; i++)
        {
            if(a[i] > max)
            {
                max = a[i];
                position = i;
            }
        }

        answer = max;

        // Mark the selected element
        a[position] = -999999;
    }

    cout << "Kth largest element = " << answer << endl;

    return 0;
}
```

**Input**
```
Enter number of elements: 6
Enter array elements: 3 2 1 5 6 4
Enter k: 2
```

**Output**
```
Kth largest element = 5
```

---

### 4.3 Sort Array By Parity

**Question:** Given an integer array nums, move all the even integers at the beginning of the array followed by all the odd integers. Return any array that satisfies this condition.

**Aim:** To write a C++ program to arrange all even numbers first and all odd numbers after them.

**Algorithm**
1. Read the number of elements.
2. Read the array elements.
3. Create a new array.
4. First check every element.
5. If the element is even, store it in the new array.
6. Then check every element again.
7. If the element is odd, store it in the new array.
8. Print the new array.

**Program**
```cpp
#include <iostream>
using namespace std;

int main()
{
    int n;
    int a[100];
    int result[100];
    int position = 0;

    cout << "Enter number of elements: ";
    cin >> n;

    cout << "Enter array elements: ";
    for(int i = 0; i < n; i++)
    {
        cin >> a[i];
    }

    // Store even numbers first
    for(int i = 0; i < n; i++)
    {
        if(a[i] % 2 == 0)
        {
            result[position] = a[i];
            position++;
        }
    }

    // Store odd numbers next
    for(int i = 0; i < n; i++)
    {
        if(a[i] % 2 != 0)
        {
            result[position] = a[i];
            position++;
        }
    }

    cout << "Array after sorting by parity: ";

    for(int i = 0; i < n; i++)
    {
        cout << result[i] << " ";
    }

    return 0;
}
```

**Input**
```
Enter number of elements: 6
Enter array elements: 3 1 2 4 6 5
```

**Output**
```
Array after sorting by parity: 2 4 6 3 1 5
```
