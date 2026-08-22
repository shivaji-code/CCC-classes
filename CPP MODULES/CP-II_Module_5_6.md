# CP-II Module 5 & 6 Programs

## Module 5

### 5.1 Subsets

**Question:** Given an integer array nums of unique elements, return all possible subsets (the power set). The solution set must not contain duplicate subsets. Return the solution in any order.

**Aim:** To write a C++ program to find all possible subsets of an array.

**Algorithm**
1. Read the array elements.
2. Start with an empty subset.
3. For each element, either include it or skip it.
4. Repeat until all elements are considered.
5. Print every subset.

**Program**
```cpp
#include <iostream>
using namespace std;

int a[10], subset[10], n;

void findSubsets(int index, int size)
{
    // Print current subset
    cout << "{ ";

    for(int i = 0; i < size; i++)
        cout << subset[i] << " ";

    cout << "}" << endl;

    // Add elements one by one
    for(int i = index; i < n; i++)
    {
        subset[size] = a[i];

        findSubsets(i + 1, size + 1);
    }
}

int main()
{
    cout << "Enter number of elements: ";
    cin >> n;

    cout << "Enter elements: ";

    for(int i = 0; i < n; i++)
        cin >> a[i];

    cout << "All subsets are:" << endl;

    findSubsets(0, 0);

    return 0;
}
```

**Input**
```
Enter number of elements: 3
Enter elements: 1 2 3
```

**Output**
```
All subsets are:
{ }
{ 1 }
{ 1 2 }
{ 1 2 3 }
{ 1 3 }
{ 2 }
{ 2 3 }
{ 3 }
```

---

### 5.2 Permutations

**Question:** Given an array nums of distinct integers, return all the possible permutations. You can return the answer in any order.

**Aim:** To write a C++ program to find all possible permutations of an array.

**Algorithm**
1. Read the array elements.
2. Select an element for the current position.
3. Swap it with the current position.
4. Repeat for the remaining positions.
5. When all positions are filled, print the permutation.
6. Swap back and continue.

**Program**
```cpp
#include <iostream>
using namespace std;

int a[10], n;

void swapNumbers(int &x, int &y)
{
    int temp = x;
    x = y;
    y = temp;
}

void permutations(int position)
{
    if(position == n)
    {
        for(int i = 0; i < n; i++)
            cout << a[i] << " ";

        cout << endl;
        return;
    }

    for(int i = position; i < n; i++)
    {
        swapNumbers(a[position], a[i]);

        permutations(position + 1);

        swapNumbers(a[position], a[i]);
    }
}

int main()
{
    cout << "Enter number of elements: ";
    cin >> n;

    cout << "Enter elements: ";

    for(int i = 0; i < n; i++)
        cin >> a[i];

    cout << "All permutations are:" << endl;

    permutations(0);

    return 0;
}
```

**Input**
```
Enter number of elements: 3
Enter elements: 1 2 3
```

**Output**
```
All permutations are:
1 2 3
1 3 2
2 1 3
2 3 1
3 2 1
3 1 2
```

---

### 5.3 Permutations II

**Question:** Given a collection of numbers, nums, that might contain duplicates, return all possible unique permutations in any order.

**Aim:** To write a C++ program to find all unique permutations of an array that may contain duplicate elements.

**Algorithm**
1. Read the array elements.
2. Arrange the elements in ascending order.
3. Generate permutations using swapping.
4. Skip an element if the same element is already used at that position.
5. Print all unique permutations.

**Program**
```cpp
#include <iostream>
using namespace std;

int a[10], n;

void swapNumbers(int &x, int &y)
{
    int temp = x;
    x = y;
    y = temp;
}

// Simple sorting
void sortArray()
{
    for(int i = 0; i < n - 1; i++)
    {
        for(int j = 0; j < n - i - 1; j++)
        {
            if(a[j] > a[j + 1])
            {
                swapNumbers(a[j], a[j + 1]);
            }
        }
    }
}

void permutations(int position)
{
    if(position == n)
    {
        for(int i = 0; i < n; i++)
            cout << a[i] << " ";

        cout << endl;
        return;
    }

    for(int i = position; i < n; i++)
    {
        bool used = false;

        for(int j = position; j < i; j++)
        {
            if(a[j] == a[i])
            {
                used = true;
                break;
            }
        }

        if(used == true)
            continue;

        swapNumbers(a[position], a[i]);

        permutations(position + 1);

        swapNumbers(a[position], a[i]);
    }
}

int main()
{
    cout << "Enter number of elements: ";
    cin >> n;

    cout << "Enter elements: ";

    for(int i = 0; i < n; i++)
        cin >> a[i];

    sortArray();

    cout << "Unique permutations are:" << endl;

    permutations(0);

    return 0;
}
```

**Input**
```
Enter number of elements: 3
Enter elements: 1 1 2
```

**Output**
```
Unique permutations are:
1 1 2
1 2 1
2 1 1
```

---

## Module 6

### 6.1 Middle of the Linked List

**Question:** Given the head of a singly linked list, return the middle node of the linked list. If there are two middle nodes, return the second middle node.

**Aim:** To write a C++ program to find the middle node of a singly linked list.

**Algorithm**
1. Create the linked list.
2. Count the number of nodes.
3. Find the middle position using count / 2.
4. Move to that position.
5. Print the middle element.

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

    // Count nodes
    int count = 0;

    temp = head;

    while(temp != NULL)
    {
        count++;
        temp = temp->next;
    }

    // Find middle
    int middle = count / 2;

    temp = head;

    for(int i = 0; i < middle; i++)
        temp = temp->next;

    cout << "Middle element = " << temp->data;

    return 0;
}
```

**Input**
```
Enter number of nodes: 5
Enter element: 10
Enter element: 20
Enter element: 30
Enter element: 40
Enter element: 50
```

**Output**
```
Middle element = 30
```

---

### 6.2 Delete Node in a Linked List

**Question:** There is a singly-linked list head and we want to delete a node node in it. You are given the node to be deleted node. You will not be given access to the first node of head. Delete the given node. Note that by deleting the node, we do not mean removing it from memory. We mean:
- The value of the given node should not exist in the linked list.
- The number of nodes in the linked list should decrease by one.
- All the values before node should be in the same order.
- All the values after node should be in the same order.

**Aim:** To write a C++ program to delete a given node from a singly linked list without using the head node inside the delete function.

**Algorithm**
1. Create the linked list.
2. Select the node to be deleted.
3. Copy the next node's data into the selected node.
4. Connect the selected node to the node after the next node.
5. Display the linked list.

**Program**
```cpp
#include <iostream>
using namespace std;

struct Node
{
    int data;
    Node *next;
};

// Delete without using head
void deleteNode(Node *node)
{
    Node *temp = node->next;

    node->data = temp->data;
    node->next = temp->next;
}

int main()
{
    Node *head = NULL;
    Node *temp;
    Node *newNode;
    Node *deleteThis;

    int n, position;

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

    cout << "Enter position of node to delete: ";
    cin >> position;

    deleteThis = head;

    for(int i = 0; i < position; i++)
        deleteThis = deleteThis->next;

    deleteNode(deleteThis);

    cout << "Linked list after deletion: ";

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
Enter number of nodes: 5
Enter element: 10
Enter element: 20
Enter element: 30
Enter element: 40
Enter element: 50
Enter position of node to delete: 2
```

**Output**
```
Linked list after deletion: 10 20 40 50
```

---

### 6.3 Reverse Linked List

**Question:** Given the head of a singly linked list, reverse the list, and return the reversed list.

**Aim:** To write a C++ program to reverse a singly linked list.

**Algorithm**
1. Create the linked list.
2. Use previous, current, and next pointers.
3. Reverse each link.
4. Move the pointers forward.
5. Make previous the new head.
6. Print the reversed list.

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

    // Reverse linked list
    Node *previous = NULL;
    Node *current = head;
    Node *next;

    while(current != NULL)
    {
        next = current->next;
        current->next = previous;

        previous = current;
        current = next;
    }

    head = previous;

    cout << "Reversed linked list: ";

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
Enter number of nodes: 5
Enter element: 10
Enter element: 20
Enter element: 30
Enter element: 40
Enter element: 50
```

**Output**
```
Reversed linked list: 50 40 30 20 10
```
