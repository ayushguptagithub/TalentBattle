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


### **1. Doubly Linked List (DLL)**

Here’s an example implementation of a **Doubly Linked List**:

```cpp
#include <iostream>
using namespace std;

// Node structure for Doubly Linked List
struct Node {
    int data;
    Node* next;
    Node* prev;
};

// Function to insert a node at the beginning
void insertAtBeginning(Node*& head, int value) {
    Node* newNode = new Node();
    newNode->data = value;
    newNode->next = head;
    newNode->prev = nullptr;

    if (head != nullptr) {
        head->prev = newNode;
    }
    head = newNode;
}

// Function to insert a node at the end
void insertAtEnd(Node*& head, int value) {
    Node* newNode = new Node();
    newNode->data = value;
    newNode->next = nullptr;

    if (head == nullptr) {
        newNode->prev = nullptr;
        head = newNode;
        return;
    }

    Node* temp = head;
    while (temp->next != nullptr) {
        temp = temp->next;
    }
    temp->next = newNode;
    newNode->prev = temp;
}

// Function to display the DLL
void display(Node* head) {
    Node* temp = head;
    while (temp != nullptr) {
        cout << temp->data << " <-> ";
        temp = temp->next;
    }
    cout << "nullptr" << endl;
}

// Function to delete a node from the beginning
void deleteFromBeginning(Node*& head) {
    if (head == nullptr) {
        cout << "List is empty!" << endl;
        return;
    }

    Node* temp = head;
    head = head->next;
    if (head != nullptr) {
        head->prev = nullptr;
    }
    delete temp;
}

// Function to delete a node from the end
void deleteFromEnd(Node*& head) {
    if (head == nullptr) {
        cout << "List is empty!" << endl;
        return;
    }

    if (head->next == nullptr) {
        delete head;
        head = nullptr;
        return;
    }

    Node* temp = head;
    while (temp->next != nullptr) {
        temp = temp->next;
    }

    temp->prev->next = nullptr;
    delete temp;
}

int main() {
    Node* head = nullptr;

    insertAtBeginning(head, 10);
    insertAtBeginning(head, 20);
    insertAtEnd(head, 30);
    display(head);

    deleteFromBeginning(head);
    display(head);

    deleteFromEnd(head);
    display(head);

    return 0;
}
```

---

### **2. Circular Linked List (Singly)**

Here’s an example implementation of a **Circular Linked List**:

```cpp
#include <iostream>
using namespace std;

// Node structure for Circular Linked List
struct Node {
    int data;
    Node* next;
};

// Function to insert a node at the beginning
void insertAtBeginning(Node*& tail, int value) {
    Node* newNode = new Node();
    newNode->data = value;

    if (tail == nullptr) {
        newNode->next = newNode;
        tail = newNode;
        return;
    }

    newNode->next = tail->next;
    tail->next = newNode;
}

// Function to insert a node at the end
void insertAtEnd(Node*& tail, int value) {
    Node* newNode = new Node();
    newNode->data = value;

    if (tail == nullptr) {
        newNode->next = newNode;
        tail = newNode;
        return;
    }

    newNode->next = tail->next;
    tail->next = newNode;
    tail = newNode;
}

// Function to display the Circular Linked List
void display(Node* tail) {
    if (tail == nullptr) {
        cout << "List is empty!" << endl;
        return;
    }

    Node* temp = tail->next;
    do {
        cout << temp->data << " -> ";
        temp = temp->next;
    } while (temp != tail->next);
    cout << "(back to head)" << endl;
}

// Function to delete a node from the beginning
void deleteFromBeginning(Node*& tail) {
    if (tail == nullptr) {
        cout << "List is empty!" << endl;
        return;
    }

    Node* head = tail->next;
    if (head == tail) {
        delete tail;
        tail = nullptr;
        return;
    }

    tail->next = head->next;
    delete head;
}

// Function to delete a node from the end
void deleteFromEnd(Node*& tail) {
    if (tail == nullptr) {
        cout << "List is empty!" << endl;
        return;
    }

    Node* head = tail->next;
    if (head == tail) {
        delete tail;
        tail = nullptr;
        return;
    }

    Node* temp = head;
    while (temp->next != tail) {
        temp = temp->next;
    }

    temp->next = tail->next;
    delete tail;
    tail = temp;
}

int main() {
    Node* tail = nullptr;

    insertAtBeginning(tail, 10);
    insertAtBeginning(tail, 20);
    insertAtEnd(tail, 30);
    display(tail);

    deleteFromBeginning(tail);
    display(tail);

    deleteFromEnd(tail);
    display(tail);

    return 0;
}
```

---

### Explanation of Circular Linked List Code

1. **Circular Behavior**:
   - The `next` pointer of the last node points back to the first node, creating a loop.

2. **Insert at Beginning**:
   - Insert the new node after the tail and adjust the `next` pointers accordingly.

3. **Insert at End**:
   - Insert the new node after the tail and update the tail pointer.

4. **Delete from Beginning**:
   - Adjust the `next` pointer of the tail to skip the current head.

5. **Delete from End**:
   - Traverse to the second-to-last node and update its `next` pointer to the head.

Let me know if you need further clarifications or variations! 😊