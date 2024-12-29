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


### **What is Hashing?**

Hashing is a process of mapping large data sets to smaller fixed-size values, called hash values or hash codes, using a function called a **hash function**. Hashing is widely used in data storage, retrieval, and security applications.

The main goal of hashing is to ensure efficient searching and retrieval of data.

---

### **Key Concepts in Hashing**

1. **Hash Function**:
   - A function \( H(x) \) that takes an input \( x \) and produces a fixed-size hash value.
   - Example: For a string "apple", a hash function might output a hash value of 42.

2. **Hash Table**:
   - A data structure that stores data in an associative manner using hash values as indices.
   - Example: Keys and values are stored, where the hash function determines the location.

3. **Collision**:
   - When two different inputs produce the same hash value.
   - Example: "abc" and "xyz" might both produce the hash value 45.
   - **Resolution Techniques**:
     - **Chaining**: Store multiple elements at the same hash index using a linked list.
     - **Open Addressing**: Probe for the next available slot.

4. **Load Factor**:
   - Ratio of the number of elements stored to the total number of slots in the table.
   - \( \text{Load Factor} = \frac{\text{Number of Elements}}{\text{Size of Hash Table}} \)

5. **Applications**:
   - Database indexing
   - Password storage
   - Caches
   - Data deduplication

---

### **Types of Hashing Techniques**

1. **Direct Hashing**:
   - The key itself is used as the hash index.
   - Simple but requires a large table size.

2. **Modulo-Division Method**:
   - Hash index = \( \text{Key} \% \text{Table Size} \)
   - Effective for uniformly distributed data.

3. **Multiplicative Hashing**:
   - Use a multiplication factor to derive the hash value.
   - Formula: \( h(k) = \lfloor M \times (k \times A \mod 1) \rfloor \)
     - \( M \): Table size, \( A \): Constant.

4. **Mid-Square Method**:
   - Square the key and extract a portion of the result to determine the index.

5. **Folding Method**:
   - Divide the key into parts, add them together, and use modulo.

---

### **C++ Implementation of Hashing**

Here’s an example implementation of a hash table using chaining to resolve collisions:

```cpp
#include <iostream>
#include <list>
using namespace std;

class HashTable {
    int size;                // Size of hash table
    list<int>* table;        // Array of linked lists

public:
    HashTable(int size) {
        this->size = size;
        table = new list<int>[size];
    }

    // Hash function
    int hashFunction(int key) {
        return key % size;
    }

    // Insert a key into the hash table
    void insert(int key) {
        int index = hashFunction(key);
        table[index].push_back(key);
    }

    // Remove a key from the hash table
    void remove(int key) {
        int index = hashFunction(key);
        table[index].remove(key);
    }

    // Search for a key in the hash table
    bool search(int key) {
        int index = hashFunction(key);
        for (int element : table[index]) {
            if (element == key) {
                return true;
            }
        }
        return false;
    }

    // Display the hash table
    void display() {
        for (int i = 0; i < size; i++) {
            cout << "Index " << i << ": ";
            for (int element : table[i]) {
                cout << element << " -> ";
            }
            cout << "nullptr" << endl;
        }
    }

    ~HashTable() {
        delete[] table;
    }
};

int main() {
    HashTable hashTable(7);

    hashTable.insert(10);
    hashTable.insert(20);
    hashTable.insert(15);
    hashTable.insert(7);
    hashTable.insert(22);

    hashTable.display();

    cout << "Searching for 15: " << (hashTable.search(15) ? "Found" : "Not Found") << endl;

    hashTable.remove(15);
    cout << "After removing 15:" << endl;
    hashTable.display();

    return 0;
}
```

---

### **Explanation of the Code**

1. **Structure**:
   - The hash table is implemented using an array of linked lists.
   - Each index of the array is a bucket.

2. **Hash Function**:
   - \( \text{Key} \% \text{Size} \) is used to determine the index for a key.

3. **Insertion**:
   - The key is inserted into the linked list at the calculated index.

4. **Search**:
   - The linked list at the hashed index is traversed to find the key.

5. **Deletion**:
   - The key is removed from the linked list at the hashed index.

6. **Display**:
   - Each index and its contents are displayed.

---

### **Simplified Hash Table Code using Vectors Vector**

```cpp
#include <iostream>
#include <vector>
using namespace std;

// Simple Hash Table class using chaining
class HashTable {
    int size;                        // Size of the hash table
    vector<vector<int>> table;       // Vector of vectors to store chains

public:
    HashTable(int size) {
        this->size = size;
        table.resize(size);          // Initialize with empty chains
    }

    // Hash function to calculate index
    int hashFunction(int key) {
        return key % size;
    }

    // Insert a key into the hash table
    void insert(int key) {
        int index = hashFunction(key);
        table[index].push_back(key); // Add key to the appropriate chain
    }

    // Search for a key in the hash table
    bool search(int key) {
        int index = hashFunction(key);
        for (int element : table[index]) {
            if (element == key) {
                return true;         // Key found
            }
        }
        return false;                // Key not found
    }

    // Display the hash table
    void display() {
        for (int i = 0; i < size; i++) {
            cout << "Index " << i << ": ";
            for (int element : table[i]) {
                cout << element << " ";
            }
            cout << endl;
        }
    }
};

int main() {
    HashTable hashTable(5);  // Create a hash table with 5 slots

    // Insert keys into the hash table
    hashTable.insert(10);
    hashTable.insert(15);
    hashTable.insert(20);
    hashTable.insert(25);
    hashTable.insert(30);

    // Display the hash table
    cout << "Hash Table:" << endl;
    hashTable.display();

    // Search for keys
    cout << "Searching for 15: " << (hashTable.search(15) ? "Found" : "Not Found") << endl;
    cout << "Searching for 40: " << (hashTable.search(40) ? "Found" : "Not Found") << endl;

    return 0;
}
```

---

### **Explanation**

1. **Hash Function**:
   - \( \text{Key} \% \text{Size} \) determines the index for a key. For example, if the size is 5 and the key is 10, \( 10 \% 5 = 0 \).

2. **Data Storage**:
   - The hash table is implemented using a vector of vectors, where each vector at an index represents a chain.

3. **Insertion**:
   - Keys are added to the chain at the calculated index.

4. **Search**:
   - The chain at the hashed index is traversed to find the key.

5. **Display**:
   - All indices and their corresponding keys are printed.

---

### **Output**

```
Hash Table:
Index 0: 10 15 20 25 30
Index 1: 
Index 2: 
Index 3: 
Index 4: 
Searching for 15: Found
Searching for 40: Not Found
```