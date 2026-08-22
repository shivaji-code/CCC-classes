# CP-II Module 7 & 8 Programs

## Module 7

### 7.1 Remove Duplicates from Sorted List

**Question:** Given the head of a sorted linked list, delete all duplicates such that each element appears only once. Return the linked list sorted as well.

**Aim:** To write a C++ program to remove duplicate elements from a sorted singly linked list.

**Algorithm**
1. Create the sorted linked list.
2. Start from the first node.
3. Compare the current node with the next node.
4. If both are equal, skip the next node.
5. Otherwise, move to the next node.
6. Display the list.

**Program**
```cpp
#include <iostream>
using namespace std;

struct Node
{
    int data;
    Node *next;
};

int main()
{
    Node *head = NULL;
    Node *temp;
    Node *newNode;

    int n;

    cout << "Enter number of nodes: ";
    cin >> n;

    // Create sorted linked list
    for(int i = 0; i < n; i++)
    {
        newNode = new Node;

        cout << "Enter element: ";
        cin >> newNode->data;

        newNode->next = NULL;

        if(head == NULL)
        {
            head = newNode;
        }
        else
        {
            temp = head;

            while(temp->next != NULL)
                temp = temp->next;

            temp->next = newNode;
        }
    }

    // Remove duplicates
    temp = head;

    while(temp != NULL && temp->next != NULL)
    {
        if(temp->data == temp->next->data)
        {
            temp->next = temp->next->next;
        }
        else
        {
            temp = temp->next;
        }
    }

    cout << "List after removing duplicates: ";

    temp = head;

    while(temp != NULL)
    {
        cout << temp->data << " ";
        temp = temp->next;
    }

    return 0;
}
```

**Input**
```
Enter number of nodes: 6
Enter element: 1
Enter element: 1
Enter element: 2
Enter element: 3
Enter element: 3
Enter element: 4
```

**Output**
```
List after removing duplicates: 1 2 3 4
```

---

### 7.2 Merge Two Sorted Lists

**Question:** You are given the heads of two sorted linked lists list1 and list2. Merge the two lists into one sorted list. The list should be made by splicing together the nodes of the first two lists. Return the head of the merged linked list.

**Aim:** To write a C++ program to merge two sorted linked lists into one sorted linked list.

**Algorithm**
1. Create two sorted linked lists.
2. Compare the first nodes of both lists.
3. Add the smaller node to the result.
4. Move that list to its next node.
5. Repeat until one list becomes empty.
6. Add the remaining nodes.
7. Display the merged list.

**Program**
```cpp
#include <iostream>
using namespace std;

struct Node
{
    int data;
    Node *next;
};

Node* createList(int n)
{
    Node *head = NULL;
    Node *temp;
    Node *newNode;

    for(int i = 0; i < n; i++)
    {
        newNode = new Node;

        cin >> newNode->data;
        newNode->next = NULL;

        if(head == NULL)
        {
            head = newNode;
        }
        else
        {
            temp = head;

            while(temp->next != NULL)
                temp = temp->next;

            temp->next = newNode;
        }
    }

    return head;
}

Node* mergeLists(Node *list1, Node *list2)
{
    Node *head = NULL;
    Node *temp = NULL;

    while(list1 != NULL && list2 != NULL)
    {
        Node *newNode = new Node;

        if(list1->data < list2->data)
        {
            newNode->data = list1->data;
            list1 = list1->next;
        }
        else
        {
            newNode->data = list2->data;
            list2 = list2->next;
        }

        newNode->next = NULL;

        if(head == NULL)
        {
            head = newNode;
        }
        else
        {
            temp->next = newNode;
        }

        temp = newNode;
    }

    while(list1 != NULL)
    {
        Node *newNode = new Node;

        newNode->data = list1->data;
        newNode->next = NULL;

        if(head == NULL)
            head = newNode;
        else
            temp->next = newNode;

        temp = newNode;
        list1 = list1->next;
    }

    while(list2 != NULL)
    {
        Node *newNode = new Node;

        newNode->data = list2->data;
        newNode->next = NULL;

        if(head == NULL)
            head = newNode;
        else
            temp->next = newNode;

        temp = newNode;
        list2 = list2->next;
    }

    return head;
}

int main()
{
    int n1, n2;

    cout << "Enter number of nodes in first list: ";
    cin >> n1;

    cout << "Enter first sorted list: ";
    Node *list1 = createList(n1);

    cout << "Enter number of nodes in second list: ";
    cin >> n2;

    cout << "Enter second sorted list: ";
    Node *list2 = createList(n2);

    Node *head = mergeLists(list1, list2);

    cout << "Merged sorted list: ";

    Node *temp = head;

    while(temp != NULL)
    {
        cout << temp->data << " ";
        temp = temp->next;
    }

    return 0;
}
```

**Input**
```
Enter number of nodes in first list: 3
Enter first sorted list: 1 3 5
Enter number of nodes in second list: 3
Enter second sorted list: 2 4 6
```

**Output**
```
Merged sorted list: 1 2 3 4 5 6
```

---

### 7.3 Linked List Cycle

**Question:** Given head, the head of a linked list, determine if the linked list has a cycle in it. Return true if there is a cycle in the linked list. Otherwise, return false.

**Aim:** To write a C++ program to check whether a singly linked list contains a cycle.

**Algorithm**
1. Create the linked list.
2. Use two pointers: slow and fast.
3. Move slow one step at a time.
4. Move fast two steps at a time.
5. If they meet, a cycle exists.
6. If fast reaches NULL, there is no cycle.

**Program**
```cpp
#include <iostream>
using namespace std;

struct Node
{
    int data;
    Node *next;
};

int main()
{
    Node *head = NULL;
    Node *temp;
    Node *newNode;

    int n;

    cout << "Enter number of nodes: ";
    cin >> n;

    // Create linked list
    for(int i = 0; i < n; i++)
    {
        newNode = new Node;

        cout << "Enter element: ";
        cin >> newNode->data;

        newNode->next = NULL;

        if(head == NULL)
        {
            head = newNode;
        }
        else
        {
            temp = head;

            while(temp->next != NULL)
                temp = temp->next;

            temp->next = newNode;
        }
    }

    int position;

    cout << "Enter position to create cycle (-1 for no cycle): ";
    cin >> position;

    // Create cycle
    if(position >= 0)
    {
        Node *cycleNode = head;

        for(int i = 0; i < position; i++)
            cycleNode = cycleNode->next;

        temp = head;

        while(temp->next != NULL)
            temp = temp->next;

        temp->next = cycleNode;
    }

    // Check cycle
    Node *slow = head;
    Node *fast = head;

    bool cycle = false;

    while(fast != NULL && fast->next != NULL)
    {
        slow = slow->next;
        fast = fast->next->next;

        if(slow == fast)
        {
            cycle = true;
            break;
        }
    }

    if(cycle == true)
        cout << "Cycle exists";
    else
        cout << "Cycle does not exist";

    return 0;
}
```

**Input**
```
Enter number of nodes: 4
Enter element: 10
Enter element: 20
Enter element: 30
Enter element: 40
Enter position to create cycle (-1 for no cycle): 1
```

**Output**
```
Cycle exists
```

---

## Module 8

### 8.1 Daily Temperatures

**Question:** Given an array of integer's temperatures represents the daily temperatures, return an array answer such that answer[i] is the number of days you have to wait after the ith day to get a warmer temperature. If there is no future day for which this is possible, keep answer[i] == 0 instead.

**Aim:** To write a C++ program to find how many days are required to get a warmer temperature for each day.

**Algorithm**
1. Read the temperatures.
2. For each day, check the following days.
3. Find the first warmer temperature.
4. Store the number of days waited.
5. If no warmer day exists, store 0.
6. Print the answer array.

**Program**
```cpp
#include <iostream>
using namespace std;

int main()
{
    int n;
    int temp[100];
    int answer[100];

    cout << "Enter number of days: ";
    cin >> n;

    cout << "Enter temperatures: ";

    for(int i = 0; i < n; i++)
        cin >> temp[i];

    for(int i = 0; i < n; i++)
    {
        answer[i] = 0;

        for(int j = i + 1; j < n; j++)
        {
            if(temp[j] > temp[i])
            {
                answer[i] = j - i;
                break;
            }
        }
    }

    cout << "Answer: ";

    for(int i = 0; i < n; i++)
        cout << answer[i] << " ";

    return 0;
}
```

**Input**
```
Enter number of days: 8
Enter temperatures: 73 74 75 71 69 72 76 73
```

**Output**
```
Answer: 1 1 3 2 1 1 0 0
```

---

### 8.2 Largest Rectangle in Histogram

**Question:** Given an array of integers heights representing the histogram's bar height where the width of each bar is 1, return the area of the largest rectangle in the histogram.

**Aim:** To write a C++ program to find the largest rectangular area in a histogram.

**Algorithm**
1. Read the heights of the bars.
2. Select each bar one by one.
3. Expand to the left and right while bars are at least as high.
4. Find the width of the rectangle.
5. Calculate area = height × width.
6. Keep the largest area.
7. Print the largest area.

**Program**
```cpp
#include <iostream>
using namespace std;

int main()
{
    int n;
    int height[100];

    cout << "Enter number of bars: ";
    cin >> n;

    cout << "Enter heights: ";

    for(int i = 0; i < n; i++)
        cin >> height[i];

    int largest = 0;

    for(int i = 0; i < n; i++)
    {
        int left = i;
        int right = i;

        // Move left
        while(left > 0 && height[left - 1] >= height[i])
            left--;

        // Move right
        while(right < n - 1 && height[right + 1] >= height[i])
            right++;

        int width = right - left + 1;

        int area = height[i] * width;

        if(area > largest)
            largest = area;
    }

    cout << "Largest rectangle area = " << largest;

    return 0;
}
```

**Input**
```
Enter number of bars: 6
Enter heights: 2 1 5 6 2 3
```

**Output**
```
Largest rectangle area = 10
```

---

### 8.3 Gas Station

**Question:** Given two integer arrays gas and cost, return the starting gas station's index if you can travel around the circuit once in the clockwise direction, otherwise return -1. If there exists a solution, it is guaranteed to be unique.

**Aim:** To write a C++ program to find the starting gas station from which we can complete the circular journey.

**Algorithm**
1. Read the gas and cost arrays.
2. Try each station as a starting point.
3. Start with zero fuel.
4. Add gas and subtract cost at each station.
5. If fuel becomes negative, that starting station fails.
6. Continue checking the next station.
7. If one station completes the circuit, print its index.
8. If no station works, print -1.

**Program**
```cpp
#include <iostream>
using namespace std;

int main()
{
    int n;
    int gas[100];
    int cost[100];

    cout << "Enter number of gas stations: ";
    cin >> n;

    cout << "Enter gas values: ";

    for(int i = 0; i < n; i++)
        cin >> gas[i];

    cout << "Enter cost values: ";

    for(int i = 0; i < n; i++)
        cin >> cost[i];

    int answer = -1;

    for(int start = 0; start < n; start++)
    {
        int fuel = 0;
        bool possible = true;

        for(int count = 0; count < n; count++)
        {
            int station = (start + count) % n;

            fuel = fuel + gas[station] - cost[station];

            if(fuel < 0)
            {
                possible = false;
                break;
            }
        }

        if(possible == true)
        {
            answer = start;
            break;
        }
    }

    cout << "Starting gas station = " << answer;

    return 0;
}
```

**Input**
```
Enter number of gas stations: 5
Enter gas values: 1 2 3 4 5
Enter cost values: 3 4 5 1 2
```

**Output**
```
Starting gas station = 3
```
