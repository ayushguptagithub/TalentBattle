### **Queue Data Structure**

A **Queue** is a linear data structure that follows the **First In, First Out (FIFO)** principle. This means that the first element added to the queue is the first one to be removed, similar to a real-world queue, such as a line at a ticket counter.

---

### **Characteristics of a Queue**
1. **FIFO Principle:** The first element added is the first one removed.
2. **Two Main Operations:**
   - **Enqueue:** Adding an element to the end of the queue.
   - **Dequeue:** Removing an element from the front of the queue.
3. **Front and Rear:** Elements are added at the rear and removed from the front.
4. **Static or Dynamic:** Queues can be implemented using arrays (static) or linked lists (dynamic).

---

### **Types of Queues**
1. **Simple Queue:** Follows FIFO; operations occur at the front and rear.
2. **Circular Queue:** The last position is connected back to the first position to make a circular structure, optimizing space.
3. **Priority Queue:** Each element has a priority, and elements with higher priority are dequeued first.
4. **Double-Ended Queue (Deque):** Elements can be added or removed from both ends.

---

### **Queue Operations**
1. **Enqueue:** Add an element to the end of the queue.
2. **Dequeue:** Remove the front element of the queue.
3. **isEmpty:** Check if the queue is empty.
4. **isFull:** Check if the queue is full (in case of a static array).
5. **Front:** Return the front element without removing it.
6. **Rear:** Return the last element without removing it.

---

### **Queue Implementation in C++**

#### **1. Simple Queue Using an Array**

```cpp
#include <iostream>
using namespace std;

#define MAX 5

class Queue {
    int arr[MAX];
    int front, rear;

public:
    Queue() {
        front = -1;
        rear = -1;
    }

    // Check if the queue is empty
    bool isEmpty() {
        return front == -1;
    }

    // Check if the queue is full
    bool isFull() {
        return rear == MAX - 1;
    }

    // Enqueue operation
    void enqueue(int value) {
        if (isFull()) {
            cout << "Queue is full!" << endl;
        } else {
            if (front == -1) front = 0;  // Initialize front if inserting the first element
            arr[++rear] = value;
            cout << value << " added to the queue." << endl;
        }
    }

    // Dequeue operation
    void dequeue() {
        if (isEmpty()) {
            cout << "Queue is empty!" << endl;
        } else {
            cout << arr[front] << " removed from the queue." << endl;
            if (front == rear) {
                front = rear = -1;  // Reset queue if it becomes empty
            } else {
                front++;
            }
        }
    }

    // Display the queue
    void display() {
        if (isEmpty()) {
            cout << "Queue is empty!" << endl;
        } else {
            cout << "Queue elements: ";
            for (int i = front; i <= rear; i++) {
                cout << arr[i] << " ";
            }
            cout << endl;
        }
    }
};

int main() {
    Queue q;
    q.enqueue(10);
    q.enqueue(20);
    q.enqueue(30);
    q.enqueue(40);
    q.enqueue(50);
    q.enqueue(60);  // Queue full
    q.display();
    q.dequeue();
    q.dequeue();
    q.display();

    return 0;
}
```

**Explanation:**
- The `front` pointer tracks the first element, and the `rear` pointer tracks the last element.
- `enqueue` inserts elements at the `rear` position.
- `dequeue` removes elements from the `front` position.
- When the queue is empty, both `front` and `rear` are reset to `-1`.

---

#### **2. Circular Queue**

```cpp
#include <iostream>
using namespace std;

#define MAX 5

class CircularQueue {
    int arr[MAX];
    int front, rear;

public:
    CircularQueue() {
        front = -1;
        rear = -1;
    }

    // Check if the queue is empty
    bool isEmpty() {
        return front == -1;
    }

    // Check if the queue is full
    bool isFull() {
        return (rear + 1) % MAX == front;
    }

    // Enqueue operation
    void enqueue(int value) {
        if (isFull()) {
            cout << "Queue is full!" << endl;
        } else {
            if (front == -1) front = 0;  // Initialize front if inserting the first element
            rear = (rear + 1) % MAX;
            arr[rear] = value;
            cout << value << " added to the circular queue." << endl;
        }
    }

    // Dequeue operation
    void dequeue() {
        if (isEmpty()) {
            cout << "Queue is empty!" << endl;
        } else {
            cout << arr[front] << " removed from the circular queue." << endl;
            if (front == rear) {
                front = rear = -1;  // Reset queue if it becomes empty
            } else {
                front = (front + 1) % MAX;
            }
        }
    }

    // Display the queue
    void display() {
        if (isEmpty()) {
            cout << "Queue is empty!" << endl;
        } else {
            cout << "Queue elements: ";
            int i = front;
            while (true) {
                cout << arr[i] << " ";
                if (i == rear) break;
                i = (i + 1) % MAX;
            }
            cout << endl;
        }
    }
};

int main() {
    CircularQueue cq;
    cq.enqueue(10);
    cq.enqueue(20);
    cq.enqueue(30);
    cq.enqueue(40);
    cq.enqueue(50);
    cq.enqueue(60);  // Queue full
    cq.display();
    cq.dequeue();
    cq.dequeue();
    cq.display();
    cq.enqueue(60);
    cq.display();

    return 0;
}
```

**Explanation:**
- Circular queues optimize space by wrapping around when the end of the array is reached.
- The `rear` pointer moves to the start of the array (`(rear + 1) % MAX`) after reaching the end.

---

#### **3. Queue Using Linked List**

```cpp
#include <iostream>
using namespace std;

class Node {
public:
    int data;
    Node* next;
};

class Queue {
    Node *front, *rear;

public:
    Queue() {
        front = rear = nullptr;
    }

    // Check if the queue is empty
    bool isEmpty() {
        return front == nullptr;
    }

    // Enqueue operation
    void enqueue(int value) {
        Node* newNode = new Node();
        newNode->data = value;
        newNode->next = nullptr;

        if (rear == nullptr) {
            front = rear = newNode;
        } else {
            rear->next = newNode;
            rear = newNode;
        }

        cout << value << " added to the queue." << endl;
    }

    // Dequeue operation
    void dequeue() {
        if (isEmpty()) {
            cout << "Queue is empty!" << endl;
        } else {
            Node* temp = front;
            cout << front->data << " removed from the queue." << endl;
            front = front->next;

            if (front == nullptr) rear = nullptr;  // Reset rear if the queue becomes empty
            delete temp;
        }
    }

    // Display the queue
    void display() {
        if (isEmpty()) {
            cout << "Queue is empty!" << endl;
        } else {
            Node* temp = front;
            cout << "Queue elements: ";
            while (temp != nullptr) {
                cout << temp->data << " ";
                temp = temp->next;
            }
            cout << endl;
        }
    }
};

int main() {
    Queue q;
    q.enqueue(10);
    q.enqueue(20);
    q.enqueue(30);
    q.display();
    q.dequeue();
    q.display();
    return 0;
}
```

**Explanation:**
- Uses a dynamic linked list to handle queues.
- Each node contains `data` and a `next` pointer.
- Efficient for dynamic memory allocation as it doesn’t require a fixed size.

---

### **Applications of Queue**
1. **Process Scheduling:** Used in operating systems to manage processes.
2. **Data Buffering:** For example, IO Buffers, Network Buffers.
3. **Print Queue:** Managing print jobs.
4. **Breadth-First Search (BFS):** A queue is used to explore nodes level by level.

### **Double-Ended Queue (Deque)**

A **Double-Ended Queue (Deque)** is a linear data structure in which elements can be added or removed from both ends (front and rear). It is a generalized form of the queue and supports operations at both ends, unlike a regular queue that follows the **First In, First Out (FIFO)** principle.

---

### **Characteristics of a Deque**
1. **Flexible Operations:** Elements can be added or removed from both the front and the rear.
2. **Dynamic Behavior:** Can act as both a stack (LIFO) and a queue (FIFO).
3. **Types of Deque:**
   - **Input-Restricted Deque:** Insertion is allowed only at one end, but deletion can be performed at both ends.
   - **Output-Restricted Deque:** Deletion is allowed only at one end, but insertion can be performed at both ends.

---

### **Operations in a Deque**
1. **Insert at Front (`enqueueFront`)**
2. **Insert at Rear (`enqueueRear`)**
3. **Delete from Front (`dequeueFront`)**
4. **Delete from Rear (`dequeueRear`)**
5. **isEmpty:** Check if the deque is empty.
6. **isFull:** Check if the deque is full (in case of an array-based implementation).
7. **Display:** Print the contents of the deque.

---

### **Deque Implementation in C++**

#### **1. Deque Using Arrays**
```cpp
#include <iostream>
using namespace std;

#define MAX 5

class Deque {
    int arr[MAX];
    int front, rear, size;

public:
    Deque() {
        front = -1;
        rear = 0;
        size = MAX;
    }

    // Check if the deque is full
    bool isFull() {
        return (front == 0 && rear == size - 1) || (front == rear + 1);
    }

    // Check if the deque is empty
    bool isEmpty() {
        return front == -1;
    }

    // Insert at the front
    void enqueueFront(int value) {
        if (isFull()) {
            cout << "Deque is full!" << endl;
            return;
        }
        if (front == -1) {  // Empty deque
            front = rear = 0;
        } else if (front == 0) {  // Wrap around
            front = size - 1;
        } else {
            front--;
        }
        arr[front] = value;
        cout << value << " added to the front." << endl;
    }

    // Insert at the rear
    void enqueueRear(int value) {
        if (isFull()) {
            cout << "Deque is full!" << endl;
            return;
        }
        if (front == -1) {  // Empty deque
            front = rear = 0;
        } else if (rear == size - 1) {  // Wrap around
            rear = 0;
        } else {
            rear++;
        }
        arr[rear] = value;
        cout << value << " added to the rear." << endl;
    }

    // Delete from the front
    void dequeueFront() {
        if (isEmpty()) {
            cout << "Deque is empty!" << endl;
            return;
        }
        cout << arr[front] << " removed from the front." << endl;
        if (front == rear) {  // Only one element
            front = rear = -1;
        } else if (front == size - 1) {  // Wrap around
            front = 0;
        } else {
            front++;
        }
    }

    // Delete from the rear
    void dequeueRear() {
        if (isEmpty()) {
            cout << "Deque is empty!" << endl;
            return;
        }
        cout << arr[rear] << " removed from the rear." << endl;
        if (front == rear) {  // Only one element
            front = rear = -1;
        } else if (rear == 0) {  // Wrap around
            rear = size - 1;
        } else {
            rear--;
        }
    }

    // Display the deque
    void display() {
        if (isEmpty()) {
            cout << "Deque is empty!" << endl;
            return;
        }
        cout << "Deque elements: ";
        if (front <= rear) {
            for (int i = front; i <= rear; i++) {
                cout << arr[i] << " ";
            }
        } else {
            for (int i = front; i < size; i++) {
                cout << arr[i] << " ";
            }
            for (int i = 0; i <= rear; i++) {
                cout << arr[i] << " ";
            }
        }
        cout << endl;
    }
};

int main() {
    Deque dq;
    dq.enqueueRear(10);
    dq.enqueueRear(20);
    dq.enqueueFront(5);
    dq.enqueueFront(3);
    dq.display();
    dq.dequeueFront();
    dq.dequeueRear();
    dq.display();

    return 0;
}
```

**Explanation:**
- Circular indexing is used to make efficient use of the array.
- Insertion and deletion operations are performed at both ends (`front` and `rear`).

---

#### **2. Deque Using Linked List**
```cpp
#include <iostream>
using namespace std;

class Node {
public:
    int data;
    Node* next;
    Node* prev;

    Node(int value) {
        data = value;
        next = prev = nullptr;
    }
};

class Deque {
    Node *front, *rear;

public:
    Deque() {
        front = rear = nullptr;
    }

    // Check if the deque is empty
    bool isEmpty() {
        return front == nullptr;
    }

    // Insert at the front
    void enqueueFront(int value) {
        Node* newNode = new Node(value);
        if (isEmpty()) {
            front = rear = newNode;
        } else {
            newNode->next = front;
            front->prev = newNode;
            front = newNode;
        }
        cout << value << " added to the front." << endl;
    }

    // Insert at the rear
    void enqueueRear(int value) {
        Node* newNode = new Node(value);
        if (isEmpty()) {
            front = rear = newNode;
        } else {
            newNode->prev = rear;
            rear->next = newNode;
            rear = newNode;
        }
        cout << value << " added to the rear." << endl;
    }

    // Delete from the front
    void dequeueFront() {
        if (isEmpty()) {
            cout << "Deque is empty!" << endl;
            return;
        }
        Node* temp = front;
        cout << front->data << " removed from the front." << endl;
        front = front->next;
        if (front == nullptr) {
            rear = nullptr;
        } else {
            front->prev = nullptr;
        }
        delete temp;
    }

    // Delete from the rear
    void dequeueRear() {
        if (isEmpty()) {
            cout << "Deque is empty!" << endl;
            return;
        }
        Node* temp = rear;
        cout << rear->data << " removed from the rear." << endl;
        rear = rear->prev;
        if (rear == nullptr) {
            front = nullptr;
        } else {
            rear->next = nullptr;
        }
        delete temp;
    }

    // Display the deque
    void display() {
        if (isEmpty()) {
            cout << "Deque is empty!" << endl;
            return;
        }
        Node* temp = front;
        cout << "Deque elements: ";
        while (temp != nullptr) {
            cout << temp->data << " ";
            temp = temp->next;
        }
        cout << endl;
    }
};

int main() {
    Deque dq;
    dq.enqueueRear(10);
    dq.enqueueRear(20);
    dq.enqueueFront(5);
    dq.enqueueFront(3);
    dq.display();
    dq.dequeueFront();
    dq.dequeueRear();
    dq.display();

    return 0;
}
```

**Explanation:**
- Each node has `data`, a `next` pointer, and a `prev` pointer.
- Nodes are dynamically allocated and deallocated as needed.

---

### **Applications of Deque**
1. **Palindrome Checking:** Efficiently check for palindromes using front and rear comparisons.
2. **Sliding Window Maximum:** Used in algorithms to find the maximum in a sliding window.
3. **Undo/Redo Operations:** Store history for user actions.
4. **Scheduling:** Can act as both a stack and a queue.


A **Linked List** is a linear data structure where elements (called **nodes**) are stored in a sequence, but each node points to the next node in the sequence, rather than being stored in contiguous memory locations like an array.  

### Key Concepts of Linked List

1. **Node Structure**:
   - Each node has two components:
     - **Data**: Stores the actual information.
     - **Pointer** (or **Link**): Points to the next node in the list.
   
2. **Types of Linked Lists**:
   - **Singly Linked List (SLL)**: Each node points to the next node, and the last node points to `nullptr`.
   - **Doubly Linked List (DLL)**: Each node contains pointers to both the next and previous nodes.
   - **Circular Linked List (CLL)**: The last node points back to the first node, forming a circular structure. This can be singly or doubly linked.
   
3. **Advantages**:
   - Dynamic size: Can grow or shrink during runtime.
   - Efficient insertion and deletion compared to arrays (no shifting required).

4. **Disadvantages**:
   - Extra memory required for pointers.
   - Sequential access: Cannot directly access elements like an array.

---

### Basic Operations on Linked Lists

1. **Insertion**:
   - At the beginning.
   - At the end.
   - At a specific position.

2. **Deletion**:
   - From the beginning.
   - From the end.
   - From a specific position.

3. **Traversal**:
   - Visit each node sequentially to access or print data.

4. **Search**:
   - Find a node with a specific value.

---

### Singly Linked List Implementation in C++

Here is an example:

```cpp
#include <iostream>
using namespace std;

// Node structure
struct Node {
    int data;
    Node* next;
};

// Function to insert a node at the beginning
void insertAtBeginning(Node*& head, int value) {
    Node* newNode = new Node(); // Allocate memory
    newNode->data = value;      // Set the data
    newNode->next = head;       // Point to the current head
    head = newNode;             // Update the head
}

// Function to insert a node at the end
void insertAtEnd(Node*& head, int value) {
    Node* newNode = new Node();
    newNode->data = value;
    newNode->next = nullptr;

    if (head == nullptr) {
        head = newNode;
        return;
    }

    Node* temp = head;
    while (temp->next != nullptr) {
        temp = temp->next;
    }
    temp->next = newNode;
}

// Function to delete a node from the beginning
void deleteFromBeginning(Node*& head) {
    if (head == nullptr) {
        cout << "List is empty!" << endl;
        return;
    }

    Node* temp = head;
    head = head->next;
    delete temp;
}

// Function to display the linked list
void display(Node* head) {
    if (head == nullptr) {
        cout << "List is empty!" << endl;
        return;
    }

    Node* temp = head;
    while (temp != nullptr) {
        cout << temp->data << " -> ";
        temp = temp->next;
    }
    cout << "nullptr" << endl;
}

int main() {
    Node* head = nullptr; // Initialize the head to null

    insertAtBeginning(head, 10);
    insertAtBeginning(head, 20);
    insertAtEnd(head, 30);
    display(head);

    deleteFromBeginning(head);
    display(head);

    return 0;
}
```

---

### Explanation of the Code

1. **Node Structure**:
   - The `Node` structure contains an integer `data` and a pointer `next` to the next node.

2. **Insert at Beginning**:
   - Create a new node.
   - Link it to the current head.
   - Update the head to point to the new node.

3. **Insert at End**:
   - Traverse to the last node.
   - Set its `next` to point to the new node.

4. **Delete from Beginning**:
   - Update the head to the next node.
   - Free the memory of the old head.

5. **Display**:
   - Traverse the list and print the `data` of each node.

---

### Linked List Variations

#### 1. **Doubly Linked List Example**

```cpp
struct Node {
    int data;
    Node* next;
    Node* prev; // Pointer to the previous node
};
```

#### 2. **Circular Linked List Example**

```cpp
struct Node {
    int data;
    Node* next; // Points back to the head for circular behavior
};
```
