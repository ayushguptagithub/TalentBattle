### **Data Structures and Types**

A **data structure** is a way of organizing and storing data so that it can be accessed and modified efficiently. The choice of data structure is crucial for algorithmic performance and resource management.

Data structures can be classified into **two types**:

1. **Linear Data Structures**
2. **Non-Linear Data Structures**

Let's go through each in detail.

---

### **1. Linear Data Structures**
In linear data structures, elements are stored in a sequence, and each element is connected to its previous and next element.

#### **Types of Linear Data Structures**

1. **Arrays**
   - An array is a collection of elements of the same type, stored in contiguous memory locations.
   - It allows random access to elements via indexing.
   - **Operations:** Access, Insert, Delete, Traverse.
   - **Example:** `arr[0]`, `arr[1]`, `arr[2]`

2. **Linked Lists**
   - A linked list consists of a sequence of nodes, where each node contains two parts: the data and a reference (or link) to the next node in the sequence.
   - Unlike arrays, linked lists do not require contiguous memory allocation.
   - **Operations:** Insertion, Deletion, Traversal, Searching.
   - **Types of Linked Lists:**
     - **Singly Linked List:** Each node points to the next node in the list.
     - **Doubly Linked List:** Each node has references to both the next and previous nodes.
     - **Circular Linked List:** The last node points back to the first node.

3. **Stacks**
   - A stack is a linear data structure that follows the **Last In, First Out (LIFO)** principle.
   - **Operations:** `push()` (add element), `pop()` (remove top element), `peek()` (view top element), `isEmpty()` (check if stack is empty).
   - **Applications:** Function calls (call stack), undo operations in applications.

4. **Queues**
   - A queue is a linear data structure that follows the **First In, First Out (FIFO)** principle.
   - **Operations:** `enqueue()` (add element), `dequeue()` (remove front element), `front()` (view front element), `isEmpty()`.
   - **Types of Queues:**
     - **Simple Queue:** Regular FIFO order.
     - **Circular Queue:** The last position is connected back to the first position, making the queue circular.
     - **Priority Queue:** Each element is assigned a priority, and the element with the highest priority is dequeued first.
     - **Deque (Double-Ended Queue):** Elements can be added or removed from both ends.

---

### **2. Non-Linear Data Structures**
In non-linear data structures, elements are not stored in a sequence. They may be connected in hierarchical or interconnected ways.

#### **Types of Non-Linear Data Structures**

1. **Trees**
   - A tree is a hierarchical data structure consisting of nodes, with a single node being the root. Each node can have children nodes.
   - **Properties:** A tree with `n` nodes has `n-1` edges, and there is exactly one path between any two nodes.
   - **Types of Trees:**
     - **Binary Tree:** Each node has at most two children (left and right).
     - **Binary Search Tree (BST):** A binary tree with the left child smaller and the right child larger than the parent.
     - **AVL Tree:** A self-balancing binary search tree.
     - **Heap:** A special tree-based data structure used for priority queues.
     - **Trie (Prefix Tree):** Used for storing strings in a way that helps with efficient search operations.

   **Operations:** Traversal (Pre-order, In-order, Post-order), Insertion, Deletion, Searching.

2. **Graphs**
   - A graph is a collection of nodes (vertices) and edges (connections between nodes). Graphs can be either **directed** (edges have direction) or **undirected** (edges have no direction).
   - **Types of Graphs:**
     - **Directed Graph (Digraph):** Edges have direction, represented as an ordered pair `(u, v)`.
     - **Undirected Graph:** Edges have no direction, represented as an unordered pair `{u, v}`.
     - **Weighted Graph:** Edges have weights (costs, distances).
     - **Unweighted Graph:** Edges have no weights.
     - **Directed Acyclic Graph (DAG):** A directed graph with no cycles.

   **Operations:** BFS (Breadth-First Search), DFS (Depth-First Search), Dijkstra's algorithm, Floyd-Warshall.

3. **Hash Tables (Hash Maps)**
   - A hash table is a data structure that stores key-value pairs. The key is hashed to produce an index in an array, where the corresponding value is stored.
   - **Operations:** Insertion, Deletion, Searching (average time complexity `O(1)`).
   - **Collisions:** When two keys hash to the same index, collisions occur. Methods to handle collisions include **chaining** (linked list at each index) and **open addressing** (finding the next available spot).

---

### **3. Other Specialized Data Structures**

1. **Heaps**
   - A heap is a special tree-based data structure that satisfies the **heap property**.
   - **Types:**
     - **Max-Heap:** The value of each parent node is greater than or equal to the values of its children.
     - **Min-Heap:** The value of each parent node is smaller than or equal to the values of its children.
   - **Operations:** Insertion, Deletion (extracting max/min), Heapify.
   - **Applications:** Priority queues, sorting (heap sort).

2. **Sets**
   - A set is an unordered collection of unique elements.
   - Operations: Insert, Delete, Search, Union, Intersection, Difference.
   - **Applications:** Database indexing, checking membership.

3. **Maps (Dictionaries)**
   - A map (or dictionary) is a collection of key-value pairs, where each key is unique.
   - **Operations:** Insert, Delete, Search, Update.
   - **Applications:** Caching, dictionary lookups.

---

### **Choosing the Right Data Structure**
- **Efficiency:** Consider the time and space complexity of operations when choosing a data structure.
- **Problem Domain:** The structure you choose should be aligned with the specific problem you're solving. For example:
  - If you need to search for elements frequently, a hash table or binary search tree might be a good choice.
  - If you need to maintain an ordered collection, a balanced binary search tree might be better.
  - If you need to process elements in a specific order (e.g., LIFO or FIFO), stacks or queues should be considered.

### **Conclusion**
Data structures are fundamental to computer science and software development. They allow efficient storage, retrieval, and modification of data, enabling the development of algorithms that solve complex problems. By understanding various data structures and their operations, you can make informed decisions when designing systems and algorithms.



### **Stack Data Structure**

A **Stack** is a linear data structure that follows the **Last In, First Out (LIFO)** principle. This means that the last element added to the stack is the first one to be removed. You can think of a stack as a collection of plates in a cafeteria; the last plate placed on top is the first one that is taken away.

#### **Stack Operations**
1. **Push (Insert):** Adds an element to the top of the stack.
2. **Pop (Remove):** Removes the top element of the stack.
3. **Peek/Top:** Returns the top element of the stack without removing it.
4. **isEmpty:** Checks whether the stack is empty.
5. **Size:** Returns the number of elements in the stack.

---

### **Types of Stacks**
1. **Simple Stack:** A basic stack where elements are added at the top and removed from the top.
2. **Dynamic Stack:** A stack where the size is not fixed and dynamically resizes based on the number of elements.
3. **Stack using Linked List:** A stack implementation using linked list nodes instead of arrays.

---

### **Code Examples in C++**

#### **1. Simple Stack Implementation using an Array**

Here we will implement a stack using a fixed-size array.

```cpp
#include <iostream>
using namespace std;

#define MAX 5

class Stack {
    int arr[MAX];
    int top;

public:
    Stack() {
        top = -1;  // Initialize stack as empty
    }

    // Check if the stack is empty
    bool isEmpty() {
        return top == -1;
    }

    // Check if the stack is full
    bool isFull() {
        return top == MAX - 1;
    }

    // Push operation (Insert)
    void push(int value) {
        if (isFull()) {
            cout << "Stack is full!" << endl;
        } else {
            arr[++top] = value;
            cout << value << " pushed onto the stack." << endl;
        }
    }

    // Pop operation (Remove)
    void pop() {
        if (isEmpty()) {
            cout << "Stack is empty!" << endl;
        } else {
            cout << arr[top--] << " popped from the stack." << endl;
        }
    }

    // Peek operation (View the top element)
    void peek() {
        if (isEmpty()) {
            cout << "Stack is empty!" << endl;
        } else {
            cout << "Top element: " << arr[top] << endl;
        }
    }

    // Display all elements in the stack
    void display() {
        if (isEmpty()) {
            cout << "Stack is empty!" << endl;
        } else {
            cout << "Stack elements: ";
            for (int i = top; i >= 0; i--) {
                cout << arr[i] << " ";
            }
            cout << endl;
        }
    }
};

int main() {
    Stack s;
    s.push(10);
    s.push(20);
    s.push(30);
    s.push(40);
    s.push(50);
    s.push(60);  // Stack full
    s.display();
    s.peek();
    s.pop();
    s.pop();
    s.display();
    s.peek();

    return 0;
}
```

**Explanation:**
- **Array-based stack:** This implementation uses a fixed-size array `arr[MAX]` to store elements in the stack.
- **`top` pointer:** The `top` pointer keeps track of the last inserted element (top of the stack).
- **`push`:** Adds an element to the top of the stack. If the stack is full, a message is displayed.
- **`pop`:** Removes the top element of the stack. If the stack is empty, a message is displayed.
- **`peek`:** Returns the element at the top of the stack without removing it.
- **`display`:** Displays all elements in the stack from top to bottom.

---


### **2. Stack using STL (Standard Template Library)**

The **C++ Standard Library** provides a built-in `stack` class that allows easy stack operations. Below is an example using the STL stack:

```cpp
#include <iostream>
#include <stack>
using namespace std;

int main() {
    stack<int> s;

    s.push(10);
    s.push(20);
    s.push(30);
    s.push(40);
    s.push(50);

    cout << "Top element: " << s.top() << endl;

    s.pop();
    cout << "After popping, top element: " << s.top() << endl;

    cout << "Stack elements: ";
    while (!s.empty()) {
        cout << s.top() << " ";
        s.pop();
    }
    cout << endl;

    return 0;
}
```

**Explanation:**
- **STL stack:** The `stack` container is part of the C++ Standard Library, which internally uses a container like a deque or list to store elements.
- **`push`:** Adds an element to the stack.
- **`top`:** Returns the top element of the stack.
- **`pop`:** Removes the top element.
- **`empty`:** Checks whether the stack is empty.

---

### **Applications of Stack**
1. **Expression Evaluation:** Used to evaluate arithmetic expressions (infix, postfix, or prefix).
2. **Function Call Stack:** The system uses a stack to manage function calls and returns.
3. **Backtracking Algorithms:** For solving problems like maze traversal or pathfinding.
4. **Undo/Redo operations:** In text editors or drawing applications.

### **Conclusion**
- **Simple Stack:** A basic stack implementation using arrays or linked lists.
- **Dynamic Stack:** A stack with a dynamic size, often implemented with linked lists.
- **STL Stack:** A built-in stack in C++ with simple operations like `push()`, `pop()`, and `top()`.

