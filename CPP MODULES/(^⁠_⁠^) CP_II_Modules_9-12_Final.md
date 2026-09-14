# CP-II Programs — Modules 9–12 (Verified & Corrected)

This is the consolidated, fact-checked version of the Module 9, Module 10, and Modules 11–12 program sets, cross-checked against the CP-II Index and verified by compiling and running each program with g++.

**Correction made:** In Module 9, Program 3 (Sort Characters By Frequency), the sample output for input `"tree"` was corrected from `eetr` to `eert` — the actual output this exact code produces. The program logic itself was already correct; only the shown sample output/explanation was wrong.

All other programs across Modules 9, 10, 11, and 12 were compiled and tested and match their stated outputs and the CP-II Index question list exactly.

---

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
Sorted string: eert
```

### Simple Explanation

In `tree`:

- `e` occurs 2 times.
- `t` occurs 1 time.
- `r` occurs 1 time.

So, `e` is printed first (both copies), followed by the remaining characters in the order the code encounters them while scanning ASCII values 0–255. That gives `eert`. (Any arrangement with both `e`s together and `t`/`r` somewhere after is also a valid answer for this problem, but `eert` is exactly what this program outputs.)

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

---

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

---

These programs are based on the CP-II Index. Module 11 contains Binary Tree Inorder Traversal, Binary Tree Preorder Traversal, Binary Tree Postorder Traversal, and Path Sum. Module 12 contains DFS Traversal, Find if Path Exists in Graph, and Keys and Rooms. fileciteturn5file0L221-L257

---

# MODULE 11

# Program 1: Binary Tree Inorder Traversal

## Question

Given the root of a binary tree, return the inorder traversal of its nodes' values.

## Aim

To write a C++ program to perform inorder traversal of a binary tree.

## Algorithm

1. Create the binary tree.
2. Start traversal from the root node.
3. Traverse the left subtree first.
4. Visit the root and then traverse the right subtree.
5. Print the nodes in inorder sequence.

## Program

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* left;
    Node* right;

    Node(int value) {
        data = value;
        left = NULL;
        right = NULL;
    }
};

void inorder(Node* root) {
    if (root == NULL) {
        return;
    }

    inorder(root->left);
    cout << root->data << " ";
    inorder(root->right);
}

int main() {
    // Creating a simple binary tree
    Node* root = new Node(1);
    root->left = new Node(2);
    root->right = new Node(3);
    root->left->left = new Node(4);
    root->left->right = new Node(5);

    cout << "Inorder traversal: ";
    inorder(root);

    return 0;
}
```

## Input

The tree is created in the program:

```text
        1
       / \
      2   3
     / \
    4   5
```

## Output

```text
Inorder traversal: 4 2 5 1 3
```

## Simple Explanation

In inorder traversal, we follow:

**Left → Root → Right**

For the given tree:

`4 → 2 → 5 → 1 → 3`

So the output is:

`4 2 5 1 3`

---

# Program 2: Binary Tree Preorder Traversal

## Question

Given the root of a binary tree, return the preorder traversal of its nodes' values.

## Aim

To write a C++ program to perform preorder traversal of a binary tree.

## Algorithm

1. Create the binary tree.
2. Start traversal from the root node.
3. Visit the root node first.
4. Traverse the left subtree and then the right subtree.
5. Print the nodes in preorder sequence.

## Program

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* left;
    Node* right;

    Node(int value) {
        data = value;
        left = NULL;
        right = NULL;
    }
};

void preorder(Node* root) {
    if (root == NULL) {
        return;
    }

    cout << root->data << " ";
    preorder(root->left);
    preorder(root->right);
}

int main() {
    // Creating a simple binary tree
    Node* root = new Node(1);
    root->left = new Node(2);
    root->right = new Node(3);
    root->left->left = new Node(4);
    root->left->right = new Node(5);

    cout << "Preorder traversal: ";
    preorder(root);

    return 0;
}
```

## Input

The tree is created in the program:

```text
        1
       / \
      2   3
     / \
    4   5
```

## Output

```text
Preorder traversal: 1 2 4 5 3
```

## Simple Explanation

In preorder traversal, we follow:

**Root → Left → Right**

For the given tree:

`1 → 2 → 4 → 5 → 3`

So the output is:

`1 2 4 5 3`

---

# Program 3: Binary Tree Postorder Traversal

## Question

Given the root of a binary tree, return the postorder traversal of its nodes' values.

## Aim

To write a C++ program to perform postorder traversal of a binary tree.

## Algorithm

1. Create the binary tree.
2. Start traversal from the root node.
3. Traverse the left subtree first.
4. Traverse the right subtree and then visit the root.
5. Print the nodes in postorder sequence.

## Program

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* left;
    Node* right;

    Node(int value) {
        data = value;
        left = NULL;
        right = NULL;
    }
};

void postorder(Node* root) {
    if (root == NULL) {
        return;
    }

    postorder(root->left);
    postorder(root->right);
    cout << root->data << " ";
}

int main() {
    // Creating a simple binary tree
    Node* root = new Node(1);
    root->left = new Node(2);
    root->right = new Node(3);
    root->left->left = new Node(4);
    root->left->right = new Node(5);

    cout << "Postorder traversal: ";
    postorder(root);

    return 0;
}
```

## Input

The tree is created in the program:

```text
        1
       / \
      2   3
     / \
    4   5
```

## Output

```text
Postorder traversal: 4 5 2 3 1
```

## Simple Explanation

In postorder traversal, we follow:

**Left → Right → Root**

For the given tree:

`4 → 5 → 2 → 3 → 1`

So the output is:

`4 5 2 3 1`

---

# Program 4: Path Sum

## Question

Given the root of a binary tree and an integer `targetSum`, return `true` if the tree has a root-to-leaf path such that adding up all the values along the path equals `targetSum`.

## Aim

To write a C++ program to check whether a root-to-leaf path has a sum equal to the given target sum.

## Algorithm

1. Create the binary tree and read the target sum.
2. Start from the root and subtract its value from the target.
3. Recursively check the left and right child nodes.
4. At a leaf node, check whether the remaining sum is equal to the leaf value.
5. Print `true` if such a path exists; otherwise print `false`.

## Program

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* left;
    Node* right;

    Node(int value) {
        data = value;
        left = NULL;
        right = NULL;
    }
};

bool hasPathSum(Node* root, int targetSum) {
    if (root == NULL) {
        return false;
    }

    // If the node is a leaf
    if (root->left == NULL && root->right == NULL) {
        return targetSum == root->data;
    }

    int remaining = targetSum - root->data;

    return hasPathSum(root->left, remaining) ||
           hasPathSum(root->right, remaining);
}

int main() {
    Node* root = new Node(5);
    root->left = new Node(4);
    root->right = new Node(8);
    root->left->left = new Node(11);
    root->left->left->left = new Node(7);
    root->left->left->right = new Node(2);
    root->right->left = new Node(13);
    root->right->right = new Node(4);

    int targetSum;

    cout << "Enter target sum: ";
    cin >> targetSum;

    if (hasPathSum(root, targetSum)) {
        cout << "true" << endl;
    } else {
        cout << "false" << endl;
    }

    return 0;
}
```

## Input

```text
Enter target sum: 22
```

## Output

```text
true
```

## Simple Explanation

One root-to-leaf path is:

`5 → 4 → 11 → 2`

Its sum is:

`5 + 4 + 11 + 2 = 22`

Since the path sum is equal to the target, the answer is `true`.

---

# MODULE 12

# Program 1: DFS Traversal

## Question

Given an undirected and disconnected graph `G(V, E)`, containing `V` vertices and `E` edges, the information about edges is given using a `GRAPH` matrix, where the `i`-th edge is between `GRAPH[i][0]` and `GRAPH[i][1]`. Print its DFS traversal.

## Aim

To write a C++ program to perform Depth First Search (DFS) traversal of an undirected and disconnected graph.

## Algorithm

1. Read the number of vertices and edges and create the graph.
2. Create a `visited` array and mark all vertices as unvisited.
3. Start DFS from each unvisited vertex.
4. Mark the vertex visited and visit all its unvisited neighbours.
5. Print the vertices in DFS order.

## Program

```cpp
#include <iostream>
#include <vector>
using namespace std;

void dfs(int vertex, vector<vector<int>>& graph, vector<bool>& visited) {
    visited[vertex] = true;
    cout << vertex << " ";

    for (int i = 0; i < graph[vertex].size(); i++) {
        int next = graph[vertex][i];

        if (!visited[next]) {
            dfs(next, graph, visited);
        }
    }
}

int main() {
    int V, E;

    cout << "Enter number of vertices: ";
    cin >> V;

    cout << "Enter number of edges: ";
    cin >> E;

    vector<vector<int>> graph(V);

    cout << "Enter edges:" << endl;

    for (int i = 0; i < E; i++) {
        int u, v;
        cin >> u >> v;

        graph[u].push_back(v);
        graph[v].push_back(u);
    }

    vector<bool> visited(V, false);

    cout << "DFS traversal: ";

    // Needed because the graph can be disconnected
    for (int i = 0; i < V; i++) {
        if (!visited[i]) {
            dfs(i, graph, visited);
        }
    }

    return 0;
}
```

## Input

```text
Enter number of vertices: 5
Enter number of edges: 3
Enter edges:
0 1
0 2
3 4
```

## Output

```text
DFS traversal: 0 1 2 3 4
```

## Simple Explanation

The graph has two separate parts:

```text
0
/ \
1  2

3
|
4
```

DFS first visits `0`, then its neighbours `1` and `2`.

After that, it starts from the unvisited vertex `3` and visits `4`.

So the DFS traversal is:

`0 1 2 3 4`

---

# Program 2: Find if Path Exists in Graph

## Question

Given edges and the integers `n`, `source`, and `destination`, return `true` if there is a valid path from `source` to `destination`, or `false` otherwise.

## Aim

To write a C++ program to check whether a valid path exists between a source vertex and a destination vertex.

## Algorithm

1. Read the number of vertices, edges, source, and destination.
2. Create the graph using the given edges.
3. Start DFS from the source vertex.
4. Mark visited vertices and continue until the destination is found.
5. Print `true` if the destination is reached; otherwise print `false`.

## Program

```cpp
#include <iostream>
#include <vector>
using namespace std;

bool dfs(int current, int destination,
         vector<vector<int>>& graph,
         vector<bool>& visited) {

    if (current == destination) {
        return true;
    }

    visited[current] = true;

    for (int i = 0; i < graph[current].size(); i++) {
        int next = graph[current][i];

        if (!visited[next]) {
            if (dfs(next, destination, graph, visited)) {
                return true;
            }
        }
    }

    return false;
}

int main() {
    int n, edges;

    cout << "Enter number of vertices: ";
    cin >> n;

    cout << "Enter number of edges: ";
    cin >> edges;

    vector<vector<int>> graph(n);

    cout << "Enter edges:" << endl;

    for (int i = 0; i < edges; i++) {
        int u, v;
        cin >> u >> v;

        graph[u].push_back(v);
        graph[v].push_back(u);
    }

    int source, destination;

    cout << "Enter source: ";
    cin >> source;

    cout << "Enter destination: ";
    cin >> destination;

    vector<bool> visited(n, false);

    if (dfs(source, destination, graph, visited)) {
        cout << "true" << endl;
    } else {
        cout << "false" << endl;
    }

    return 0;
}
```

## Input

```text
Enter number of vertices: 5
Enter number of edges: 4
Enter edges:
0 1
1 2
2 3
3 4
Enter source: 0
Enter destination: 4
```

## Output

```text
true
```

## Simple Explanation

The path is:

`0 → 1 → 2 → 3 → 4`

So there is a valid path from `0` to `4`.

Therefore, the answer is `true`.

---

# Program 3: Keys and Rooms

## Question

Given an array `rooms` where `rooms[i]` is the set of keys that you can obtain if you visited room `i`, return `true` if you can visit all the rooms, or `false` otherwise.

## Aim

To write a C++ program to check whether all rooms can be visited using the keys obtained from the rooms.

## Algorithm

1. Read the number of rooms and the keys available in each room.
2. Start from room `0` and mark it as visited.
3. Use the keys in a visited room to enter other rooms.
4. Continue until no new room can be visited.
5. Print `true` if all rooms are visited; otherwise print `false`.

## Program

```cpp
#include <iostream>
#include <vector>
using namespace std;

void visitRoom(int room, vector<vector<int>>& rooms,
               vector<bool>& visited) {

    visited[room] = true;

    for (int i = 0; i < rooms[room].size(); i++) {
        int nextRoom = rooms[room][i];

        if (!visited[nextRoom]) {
            visitRoom(nextRoom, rooms, visited);
        }
    }
}

int main() {
    int n;

    cout << "Enter number of rooms: ";
    cin >> n;

    vector<vector<int>> rooms(n);

    for (int i = 0; i < n; i++) {
        int keyCount;

        cout << "Enter number of keys in room " << i << ": ";
        cin >> keyCount;

        cout << "Enter keys: ";

        for (int j = 0; j < keyCount; j++) {
            int key;
            cin >> key;
            rooms[i].push_back(key);
        }
    }

    vector<bool> visited(n, false);

    // We can always enter room 0
    visitRoom(0, rooms, visited);

    bool allVisited = true;

    for (int i = 0; i < n; i++) {
        if (!visited[i]) {
            allVisited = false;
            break;
        }
    }

    if (allVisited) {
        cout << "true" << endl;
    } else {
        cout << "false" << endl;
    }

    return 0;
}
```

## Input

```text
Enter number of rooms: 4
Enter number of keys in room 0: 1
Enter keys: 1
Enter number of keys in room 1: 1
Enter keys: 2
Enter number of keys in room 2: 1
Enter keys: 3
Enter number of keys in room 3: 0
Enter keys:
```

## Output

```text
true
```

## Simple Explanation

We start from room `0`.

- Room `0` gives key `1`.
- Room `1` gives key `2`.
- Room `2` gives key `3`.
- Room `3` has no keys.

Therefore, all 4 rooms can be visited.

So the answer is `true`.

---

# Quick Revision

## Module 11

| Program | Main Concept | Easy Idea |
|---|---|---|
| Binary Tree Inorder Traversal | Tree Traversal | Left → Root → Right |
| Binary Tree Preorder Traversal | Tree Traversal | Root → Left → Right |
| Binary Tree Postorder Traversal | Tree Traversal | Left → Right → Root |
| Path Sum | Tree + Recursion | Check root-to-leaf sum |

## Module 12

| Program | Main Concept | Easy Idea |
|---|---|---|
| DFS Traversal | Graph + DFS | Visit a vertex and go deeper |
| Find if Path Exists in Graph | Graph + DFS | Search from source to destination |
| Keys and Rooms | DFS + Graph | Use keys to visit rooms |

## Important C++ Concepts Used

### Structure

```cpp
struct Node {
    int data;
    Node* left;
    Node* right;
};
```

A structure is used to create a binary tree node.

### Recursion

A function calling itself is called recursion.

Example:

```cpp
inorder(root->left);
inorder(root->right);
```

### Vector

```cpp
vector<int> numbers;
```

A vector stores multiple values and can grow as needed.

### Boolean Array

```cpp
vector<bool> visited(n, false);
```

It is used to remember which vertices or rooms have already been visited.

### DFS

DFS means **Depth First Search**. It visits one node and continues deeper before coming back.

---

# Beginner Note

All programs are written using simple logic so they are easier to understand, learn, and explain in a practical examination. Each algorithm contains **exactly 5 short points**.
