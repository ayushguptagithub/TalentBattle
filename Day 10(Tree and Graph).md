### **Tree Data Structure**

A **Tree** is a hierarchical data structure consisting of nodes, where:

1. The topmost node is called the **root**.
2. Each node has **data** and may have child nodes connected to it by edges.
3. Nodes with no children are called **leaf nodes**.
4. Trees are recursive structures because each subtree of a tree is itself a tree.

---

### **Types of Trees**

1. **Binary Tree**: Each node has at most two children (left and right).
2. **Binary Search Tree (BST)**: A binary tree where the left child contains values less than the parent, and the right child contains values greater than the parent.
3. **Balanced Tree**: A tree where the height difference between left and right subtrees of any node is at most 1.
4. **Heap**: A special tree where the parent node is either greater than (max heap) or less than (min heap) its children.
5. **N-ary Tree**: A tree where each node can have at most N children.

---

### **Basic Operations in a Binary Tree**
1. **Inserting Nodes**
2. **Traversing the Tree**:
   - **In-order Traversal** (Left, Root, Right)
   - **Pre-order Traversal** (Root, Left, Right)
   - **Post-order Traversal** (Left, Right, Root)
3. **Searching for a Node**
4. **Deleting a Node**

---

### **Binary Tree Implementation in C++**

```cpp
#include <iostream>
using namespace std;

// Node structure
struct Node {
    int data;
    Node* left;
    Node* right;

    Node(int value) {
        data = value;
        left = right = nullptr;
    }
};

// Binary Tree class
class BinaryTree {
public:
    Node* root;

    BinaryTree() {
        root = nullptr;
    }

    // Insert a node
    Node* insert(Node* node, int value) {
        if (node == nullptr) {
            return new Node(value);
        }

        if (value < node->data) {
            node->left = insert(node->left, value);
        } else {
            node->right = insert(node->right, value);
        }

        return node;
    }

    // In-order Traversal (Left, Root, Right)
    void inOrder(Node* node) {
        if (node == nullptr) return;
        inOrder(node->left);
        cout << node->data << " ";
        inOrder(node->right);
    }

    // Pre-order Traversal (Root, Left, Right)
    void preOrder(Node* node) {
        if (node == nullptr) return;
        cout << node->data << " ";
        preOrder(node->left);
        preOrder(node->right);
    }

    // Post-order Traversal (Left, Right, Root)
    void postOrder(Node* node) {
        if (node == nullptr) return;
        postOrder(node->left);
        postOrder(node->right);
        cout << node->data << " ";
    }
};

int main() {
    BinaryTree tree;

    // Insert nodes into the binary tree
    tree.root = tree.insert(tree.root, 50);
    tree.insert(tree.root, 30);
    tree.insert(tree.root, 70);
    tree.insert(tree.root, 20);
    tree.insert(tree.root, 40);
    tree.insert(tree.root, 60);
    tree.insert(tree.root, 80);

    // Traversals
    cout << "In-order Traversal: ";
    tree.inOrder(tree.root);
    cout << endl;

    cout << "Pre-order Traversal: ";
    tree.preOrder(tree.root);
    cout << endl;

    cout << "Post-order Traversal: ";
    tree.postOrder(tree.root);
    cout << endl;

    return 0;
}
```

---

### **Explanation of Code**

1. **Node Structure**:
   - Each node contains:
     - `data`: The value of the node.
     - `left`: Pointer to the left child.
     - `right`: Pointer to the right child.

2. **Insert Function**:
   - Inserts a value into the tree.
   - Values smaller than the current node go to the left subtree; larger values go to the right subtree.

3. **Traversals**:
   - **In-order Traversal**: Prints nodes in ascending order.
   - **Pre-order Traversal**: Useful for creating a copy of the tree.
   - **Post-order Traversal**: Useful for deleting or freeing the tree.

---

### **Output**

```
In-order Traversal: 20 30 40 50 60 70 80
Pre-order Traversal: 50 30 20 40 70 60 80
Post-order Traversal: 20 40 30 60 80 70 50
```


### **Code Explanation**

---

#### **1. Node Structure**
```cpp
struct Node {
    int data;
    Node* left;
    Node* right;

    Node(int value) {
        data = value;
        left = right = nullptr;
    }
};
```

- The `Node` struct represents a single node in the tree.
- It contains:
  - `data`: The value stored in the node.
  - `left`: Pointer to the left child node.
  - `right`: Pointer to the right child node.
- The constructor initializes the node's value (`data`) and sets both child pointers (`left` and `right`) to `nullptr`.

---

#### **2. Binary Tree Class**
```cpp
class BinaryTree {
public:
    Node* root;

    BinaryTree() {
        root = nullptr;
    }
};
```

- The `BinaryTree` class encapsulates the operations on the tree.
- It has a single member:
  - `root`: A pointer to the root node of the tree.
- The constructor initializes the tree to be empty by setting the root to `nullptr`.

---

#### **3. Insert Function**
```cpp
Node* insert(Node* node, int value) {
    if (node == nullptr) {
        return new Node(value);
    }

    if (value < node->data) {
        node->left = insert(node->left, value);
    } else {
        node->right = insert(node->right, value);
    }

    return node;
}
```

- The `insert` function is used to add a new value to the binary tree.
- **Logic**:
  1. If the current `node` is `nullptr` (tree is empty or at a leaf position), create a new `Node` with the given `value` and return it.
  2. If the `value` is less than the current node's data:
     - Recursively call `insert` on the left subtree.
  3. If the `value` is greater than or equal to the current node's data:
     - Recursively call `insert` on the right subtree.
  4. Finally, return the updated `node`.

---

#### **4. Traversal Functions**

##### **In-order Traversal**
```cpp
void inOrder(Node* node) {
    if (node == nullptr) return;
    inOrder(node->left);
    cout << node->data << " ";
    inOrder(node->right);
}
```
- Traverses the tree in the order: **Left → Root → Right**.
- Prints the tree's elements in ascending order for a binary search tree (BST).

##### **Pre-order Traversal**
```cpp
void preOrder(Node* node) {
    if (node == nullptr) return;
    cout << node->data << " ";
    preOrder(node->left);
    preOrder(node->right);
}
```
- Traverses the tree in the order: **Root → Left → Right**.
- Useful for copying a tree or generating a prefix expression.

##### **Post-order Traversal**
```cpp
void postOrder(Node* node) {
    if (node == nullptr) return;
    postOrder(node->left);
    postOrder(node->right);
    cout << node->data << " ";
}
```
- Traverses the tree in the order: **Left → Right → Root**.
- Useful for deleting a tree or generating a postfix expression.

---

#### **5. Main Function**
```cpp
int main() {
    BinaryTree tree;

    // Insert nodes into the binary tree
    tree.root = tree.insert(tree.root, 50);
    tree.insert(tree.root, 30);
    tree.insert(tree.root, 70);
    tree.insert(tree.root, 20);
    tree.insert(tree.root, 40);
    tree.insert(tree.root, 60);
    tree.insert(tree.root, 80);

    // Traversals
    cout << "In-order Traversal: ";
    tree.inOrder(tree.root);
    cout << endl;

    cout << "Pre-order Traversal: ";
    tree.preOrder(tree.root);
    cout << endl;

    cout << "Post-order Traversal: ";
    tree.postOrder(tree.root);
    cout << endl;

    return 0;
}
```

- Creates a binary tree and inserts nodes with values `50, 30, 70, 20, 40, 60, 80`.
- Calls and prints the results of the three traversal methods.

---

### **How the Tree Looks**

After inserting the nodes, the tree structure will be:

```
        50
       /  \
     30    70
    / \    / \
   20  40 60  80
```

---

### **Output**

```
In-order Traversal: 20 30 40 50 60 70 80
Pre-order Traversal: 50 30 20 40 70 60 80
Post-order Traversal: 20 40 30 60 80 70 50
```

---

### **Key Points**
1. **Tree Construction**:
   - The `insert` function ensures the binary search tree property is maintained.

2. **Traversals**:
   - **In-order** gives sorted data.
   - **Pre-order** processes the root before its children.
   - **Post-order** processes the root after its children.

3. **Efficiency**:
   - The insertion and traversal functions have time complexity **O(n)** for traversals and **O(log n)** for balanced insertion.



### Graph Implementation and Operations in C++ Using a 2D Matrix

Graphs are a collection of nodes (called vertices) connected by edges. They can be represented in various ways, including adjacency matrices and adjacency lists. Here, we'll focus on the **adjacency matrix representation**.

---

### **Adjacency Matrix Representation**

1. **Adjacency Matrix**:
   - A 2D array where:
     - `matrix[i][j] = 1` if there's an edge between vertex `i` and vertex `j`.
     - `matrix[i][j] = 0` if there's no edge.
   - Suitable for dense graphs.

---

### **Insertion and Deletion Operations**

#### **1. Insertion of Edges**
- To insert an edge between vertices `u` and `v`:
  - Set `matrix[u][v] = 1`.
  - If the graph is undirected, also set `matrix[v][u] = 1`.

#### **2. Deletion of Edges**
- To delete an edge between vertices `u` and `v`:
  - Set `matrix[u][v] = 0`.
  - If the graph is undirected, also set `matrix[v][u] = 0`.

---

### **C++ Implementation**

```cpp
#include <iostream>
using namespace std;

class Graph {
private:
    int** matrix; // Pointer to a 2D array
    int size;     // Number of vertices

public:
    // Constructor
    Graph(int vertices) {
        size = vertices;
        matrix = new int*[size];
        for (int i = 0; i < size; i++) {
            matrix[i] = new int[size];
            for (int j = 0; j < size; j++) {
                matrix[i][j] = 0; // Initialize matrix with 0
            }
        }
    }

    // Destructor to free memory
    ~Graph() {
        for (int i = 0; i < size; i++) {
            delete[] matrix[i];
        }
        delete[] matrix;
    }

    // Insert an edge
    void insertEdge(int u, int v, bool isUndirected = true) {
        if (u >= 0 && u < size && v >= 0 && v < size) {
            matrix[u][v] = 1; // Set edge from u to v
            if (isUndirected) {
                matrix[v][u] = 1; // If undirected, set edge from v to u
            }
        } else {
            cout << "Invalid vertices!" << endl;
        }
    }

    // Delete an edge
    void deleteEdge(int u, int v, bool isUndirected = true) {
        if (u >= 0 && u < size && v >= 0 && v < size) {
            matrix[u][v] = 0; // Remove edge from u to v
            if (isUndirected) {
                matrix[v][u] = 0; // If undirected, remove edge from v to u
            }
        } else {
            cout << "Invalid vertices!" << endl;
        }
    }

    // Display the adjacency matrix
    void display() {
        for (int i = 0; i < size; i++) {
            for (int j = 0; j < size; j++) {
                cout << matrix[i][j] << " ";
            }
            cout << endl;
        }
    }
};

int main() {
    int vertices = 5; // Number of vertices
    Graph g(vertices);

    // Insert edges
    g.insertEdge(0, 1);
    g.insertEdge(0, 4);
    g.insertEdge(1, 2);
    g.insertEdge(1, 3);
    g.insertEdge(1, 4);
    g.insertEdge(3, 4);

    cout << "Adjacency Matrix after inserting edges:" << endl;
    g.display();

    // Delete an edge
    g.deleteEdge(1, 4);

    cout << "\nAdjacency Matrix after deleting edge (1, 4):" << endl;
    g.display();

    return 0;
}
```

---

### **Explanation**

1. **Initialization**:
   - The adjacency matrix is a 2D array, initialized with all elements set to `0`.

2. **Insert an Edge**:
   - `insertEdge(u, v)`: Sets `matrix[u][v] = 1` for a directed graph.
   - For an undirected graph, it also sets `matrix[v][u] = 1`.

3. **Delete an Edge**:
   - `deleteEdge(u, v)`: Sets `matrix[u][v] = 0`.
   - For an undirected graph, it also sets `matrix[v][u] = 0`.

4. **Display**:
   - Prints the adjacency matrix to show the connections between vertices.

---

### **Sample Output**

**After inserting edges:**
```
0 1 0 0 1
1 0 1 1 1
0 1 0 0 0
0 1 0 0 1
1 1 0 1 0
```

**After deleting edge (1, 4):**
```
0 1 0 0 1
1 0 1 1 0
0 1 0 0 0
0 1 0 0 1
1 0 0 1 0
```

---

### **Advantages**
- Simple to implement and easy to understand.
- Efficient for dense graphs (many edges).

### **Disadvantages**
- Requires \(O(V^2)\) space, even for sparse graphs (few edges).