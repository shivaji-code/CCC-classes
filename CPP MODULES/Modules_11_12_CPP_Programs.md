# C++ Programs – Modules 11 & 12

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
