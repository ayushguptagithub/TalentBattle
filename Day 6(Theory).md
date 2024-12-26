### **Basic Concepts of OOP**

#### **What is Object-Oriented Programming (OOP)?**

Object-Oriented Programming (OOP) is a programming paradigm that organizes and models a software system around **objects**, which are instances of **classes**. These objects represent real-world entities with properties (data) and behaviors (functions). 

The main idea of OOP is to break down a complex system into smaller, manageable pieces by focusing on entities (objects) rather than procedures.

**Key Features of OOP:**
1. **Encapsulation**: Bundling data and methods that operate on that data within a single unit (class).
2. **Abstraction**: Hiding complex implementation details and exposing only essential features.
3. **Inheritance**: Allowing one class to derive properties and behaviors from another class.
4. **Polymorphism**: Enabling one function or method to have multiple forms based on context.

---

#### **Difference between OOP and Procedural Programming**

| **Aspect**               | **Object-Oriented Programming (OOP)**                               | **Procedural Programming**                                      |
|---------------------------|---------------------------------------------------------------------|-----------------------------------------------------------------|
| **Approach**             | Focuses on **objects** (data and methods) and their interactions.   | Focuses on **procedures** (functions) and their sequential execution. |
| **Modularity**           | Modularizes code using **classes** and **objects**.                | Organizes code into **functions** or **procedures**.           |
| **Data Handling**         | Emphasizes **data encapsulation** and access control.              | Data is often shared globally and lacks robust encapsulation.  |
| **Reusability**           | Encourages reuse through **inheritance** and **polymorphism**.     | Limited reuse; primarily uses function calls.                  |
| **Complexity Management** | Handles complexity using abstraction and object hierarchies.       | Relies on dividing the program into smaller functions.         |
| **Examples**              | C++, Java, Python (Object-Oriented features).                     | C, Fortran, older versions of Pascal.                         |

---

#### **Example: Procedural vs. OOP**

**Procedural Programming (C):**
```c
#include <stdio.h>

// Function to calculate area of a rectangle
float calculateArea(float length, float width) {
    return length * width;
}

int main() {
    float length = 5.0, width = 3.0;
    printf("Area: %.2f\n", calculateArea(length, width));
    return 0;
}
```

**Object-Oriented Programming (C++):**
```cpp
#include <iostream>
using namespace std;

// Class to represent a Rectangle
class Rectangle {
private:
    float length, width;

public:
    // Constructor
    Rectangle(float l, float w) : length(l), width(w) {}

    // Method to calculate area
    float calculateArea() {
        return length * width;
    }
};

int main() {
    Rectangle rect(5.0, 3.0); // Create an object of Rectangle
    cout << "Area: " << rect.calculateArea() << endl;
    return 0;
}
```

**Key Differences in the Example:**
- In the **procedural example**, functions and data are separate.
- In the **OOP example**, data (`length`, `width`) and behavior (`calculateArea`) are encapsulated within the `Rectangle` class.


### **Classes and Objects in C++**

#### **1. Class and Object Overview**

- **Class**: 
  A class is a blueprint or template for creating objects. It defines data members (attributes) and member functions (methods) that an object can have.

- **Object**: 
  An object is an instance of a class. It holds the actual data and can use the methods defined in the class.

---

#### **2. Structure of a Class**

```cpp
class ClassName {
public:       // Access modifier
    // Data members
    // Member functions
};
```

#### **Example of a Class and Object**

```cpp
#include <iostream>
using namespace std;

// Defining a class
class Car {
public:
    string brand;  // Data member
    int speed;

    // Member function
    void displayInfo() {
        cout << "Brand: " << brand << ", Speed: " << speed << " km/h" << endl;
    }
};

int main() {
    Car myCar;            // Creating an object of class Car
    myCar.brand = "Tesla"; // Assigning values to data members
    myCar.speed = 200;

    myCar.displayInfo();   // Calling the member function

    return 0;
}
```

**Output:**
```
Brand: Tesla, Speed: 200 km/h
```

---

#### **3. Access Modifiers**

Access modifiers control the visibility of class members. There are three types:

1. **Public**:
   - Members are accessible from anywhere in the program.

2. **Private**:
   - Members are accessible only within the class.

3. **Protected**:
   - Members are accessible within the class and its derived (child) classes.

---

#### **Examples of Access Modifiers**

**Public Members Example:**
```cpp
#include <iostream>
using namespace std;

class Student {
public:
    string name;

    void display() {
        cout << "Student Name: " << name << endl;
    }
};

int main() {
    Student student1;
    student1.name = "Alice";  // Public member is accessible here
    student1.display();

    return 0;
}
```

**Private Members Example:**
```cpp
#include <iostream>
using namespace std;

class Student {
private:
    string name; // Private member

public:
    void setName(string studentName) {
        name = studentName; // Accessible within the class
    }

    void display() {
        cout << "Student Name: " << name << endl;
    }
};

int main() {
    Student student1;
    // student1.name = "Alice"; // Error: name is private
    student1.setName("Alice"); // Use setter to access private member
    student1.display();

    return 0;
}
```

**Protected Members Example:**
```cpp
#include <iostream>
using namespace std;

// Base class
class Animal {
protected:
    string species;

public:
    void setSpecies(string animalSpecies) {
        species = animalSpecies;
    }
};

// Derived class
class Dog : public Animal {
public:
    void display() {
        cout << "Species: " << species << endl; // Accessible in derived class
    }
};

int main() {
    Dog dog1;
    dog1.setSpecies("Canine");
    dog1.display();

    return 0;
}
```

**Output:**
```
Species: Canine
```

---

### **4. Key Points to Remember**
- Use **public** for members that need to be accessed directly from outside the class.
- Use **private** for members that should be hidden from the outside and accessed only through member functions.
- Use **protected** for members that should be accessible in derived classes but not directly from outside the class.

---
### **Constructors and Destructors in C++**

#### **1. Constructor**
A constructor is a special member function of a class that is automatically called when an object of the class is created. It is used to initialize the data members of the class.

**Key Characteristics:**
- It has the same name as the class.
- It does not have a return type (not even `void`).
- It can be overloaded (multiple constructors with different parameters).

---

#### **Types of Constructors**

1. **Default Constructor**: 
   - A constructor with no parameters.
   - Automatically invoked when an object is created without arguments.

2. **Parameterized Constructor**: 
   - A constructor that takes arguments.
   - Used to initialize class members with user-defined values.

3. **Copy Constructor**:
   - A constructor that creates a new object as a copy of an existing object.

---

#### **Examples of Constructors**

**Default Constructor:**
```cpp
#include <iostream>
using namespace std;

class Person {
public:
    string name;
    int age;

    // Default Constructor
    Person() {
        name = "Unknown";
        age = 0;
    }

    void display() {
        cout << "Name: " << name << ", Age: " << age << endl;
    }
};

int main() {
    Person p1;  // Default constructor is called
    p1.display();

    return 0;
}
```

**Output:**
```
Name: Unknown, Age: 0
```

---

**Parameterized Constructor:**
```cpp
#include <iostream>
using namespace std;

class Person {
public:
    string name;
    int age;

    // Parameterized Constructor
    Person(string personName, int personAge) {
        name = personName;
        age = personAge;
    }

    void display() {
        cout << "Name: " << name << ", Age: " << age << endl;
    }
};

int main() {
    Person p1("Alice", 25);  // Parameterized constructor is called
    p1.display();

    return 0;
}
```

**Output:**
```
Name: Alice, Age: 25
```

---

**Copy Constructor:**
```cpp
#include <iostream>
using namespace std;

class Person {
public:
    string name;
    int age;

    // Parameterized Constructor
    Person(string personName, int personAge) {
        name = personName;
        age = personAge;
    }

    // Copy Constructor
    Person(const Person &p) {
        name = p.name;
        age = p.age;
    }

    void display() {
        cout << "Name: " << name << ", Age: " << age << endl;
    }
};

int main() {
    Person p1("Bob", 30);  // Parameterized constructor is called
    Person p2 = p1;        // Copy constructor is called

    p1.display();
    p2.display();

    return 0;
}
```

**Output:**
```
Name: Bob, Age: 30
Name: Bob, Age: 30
```

---

#### **2. Destructor**
A destructor is a special member function of a class that is automatically called when an object goes out of scope or is explicitly deleted. It is used to release resources such as memory, file handles, or database connections.

**Key Characteristics:**
- It has the same name as the class, preceded by a tilde (`~`).
- It does not take arguments.
- It does not have a return type.

**Example of a Destructor:**
```cpp
#include <iostream>
using namespace std;

class Person {
public:
    string name;

    // Constructor
    Person(string personName) {
        name = personName;
        cout << name << " is created." << endl;
    }

    // Destructor
    ~Person() {
        cout << name << " is destroyed." << endl;
    }
};

int main() {
    Person p1("Charlie");  // Constructor is called
    Person p2("Diana");    // Constructor is called

    return 0;  // Destructor is automatically called for both objects
}
```

**Output:**
```
Charlie is created.
Diana is created.
Diana is destroyed.
Charlie is destroyed.
```

---

### **Summary**

| **Type**        | **Purpose**                                   | **Example**                                                                                       |
|------------------|-----------------------------------------------|---------------------------------------------------------------------------------------------------|
| Default Constructor | Initializes default values.                  | `Person() { name = "Unknown"; }`                                                                 |
| Parameterized Constructor | Initializes with specific values.            | `Person(string name, int age) { this->name = name; this->age = age; }`                           |
| Copy Constructor | Copies data from another object.               | `Person(const Person &p) { name = p.name; age = p.age; }`                                        |
| Destructor       | Releases resources when an object is destroyed. | `~Person() { cout << "Object destroyed"; }`                                                     |

### **Inheritance in C++**

Inheritance is a mechanism in object-oriented programming where one class (called the derived class) can acquire properties and behaviors (data members and member functions) of another class (called the base class). 

---

### **Types of Inheritance in C++**

#### **1. Single Inheritance**
In single inheritance, a class inherits from only one base class.

**Example:**
```cpp
#include <iostream>
using namespace std;

// Base class
class Animal {
public:
    void eat() {
        cout << "This animal eats food." << endl;
    }
};

// Derived class
class Dog : public Animal {
public:
    void bark() {
        cout << "The dog barks." << endl;
    }
};

int main() {
    Dog myDog;
    myDog.eat();  // Inherited from Animal
    myDog.bark(); // Specific to Dog
    return 0;
}
```

**Output:**
```
This animal eats food.
The dog barks.
```

---

#### **2. Multiple Inheritance**
A class inherits from more than one base class.

**Example:**
```cpp
#include <iostream>
using namespace std;

// Base class 1
class Person {
public:
    void displayPerson() {
        cout << "This is a person." << endl;
    }
};

// Base class 2
class Employee {
public:
    void displayEmployee() {
        cout << "This is an employee." << endl;
    }
};

// Derived class
class Manager : public Person, public Employee {
public:
    void displayManager() {
        cout << "This is a manager." << endl;
    }
};

int main() {
    Manager myManager;
    myManager.displayPerson();   // Inherited from Person
    myManager.displayEmployee(); // Inherited from Employee
    myManager.displayManager();  // Specific to Manager
    return 0;
}
```

**Output:**
```
This is a person.
This is an employee.
This is a manager.
```

---

#### **3. Multilevel Inheritance**
A class inherits from a derived class, forming a chain.

**Example:**
```cpp
#include <iostream>
using namespace std;

// Base class
class Animal {
public:
    void eat() {
        cout << "This animal eats food." << endl;
    }
};

// Derived class
class Mammal : public Animal {
public:
    void giveBirth() {
        cout << "This mammal gives birth." << endl;
    }
};

// Further derived class
class Human : public Mammal {
public:
    void speak() {
        cout << "Humans can speak." << endl;
    }
};

int main() {
    Human person;
    person.eat();       // Inherited from Animal
    person.giveBirth(); // Inherited from Mammal
    person.speak();     // Specific to Human
    return 0;
}
```

**Output:**
```
This animal eats food.
This mammal gives birth.
Humans can speak.
```

---

#### **4. Hierarchical Inheritance**
Multiple classes inherit from a single base class.

**Example:**
```cpp
#include <iostream>
using namespace std;

// Base class
class Animal {
public:
    void eat() {
        cout << "This animal eats food." << endl;
    }
};

// Derived class 1
class Dog : public Animal {
public:
    void bark() {
        cout << "The dog barks." << endl;
    }
};

// Derived class 2
class Cat : public Animal {
public:
    void meow() {
        cout << "The cat meows." << endl;
    }
};

int main() {
    Dog myDog;
    Cat myCat;

    myDog.eat();  // Inherited from Animal
    myDog.bark(); // Specific to Dog

    myCat.eat();  // Inherited from Animal
    myCat.meow(); // Specific to Cat

    return 0;
}
```

**Output:**
```
This animal eats food.
The dog barks.
This animal eats food.
The cat meows.
```

---

#### **5. Hybrid Inheritance**
A combination of two or more types of inheritance.

**Example:**
```cpp
#include <iostream>
using namespace std;

// Base class
class Person {
public:
    void displayPerson() {
        cout << "This is a person." << endl;
    }
};

// Derived class 1
class Employee : public Person {
public:
    void displayEmployee() {
        cout << "This is an employee." << endl;
    }
};

// Derived class 2
class Student : public Person {
public:
    void displayStudent() {
        cout << "This is a student." << endl;
    }
};

// Further derived class
class WorkingStudent : public Employee, public Student {
public:
    void displayWorkingStudent() {
        cout << "This is a working student." << endl;
    }
};

int main() {
    WorkingStudent ws;

    // Accessing base class and intermediate class methods
    ws.displayEmployee();
    ws.displayStudent();
    ws.displayWorkingStudent();

    return 0;
}
```

**Output:**
```
This is an employee.
This is a student.
This is a working student.
```

---

### **Key Points to Remember**
- Use `public`, `protected`, or `private` inheritance to control access to base class members in derived classes.
- Avoid ambiguity in multiple inheritance by explicitly specifying the base class when necessary.
- Use inheritance to promote code reuse, modularity, and maintainability.

### **Polymorphism in C++**

Polymorphism allows objects of different classes to be treated as objects of a common base class. It enables a single interface to represent different underlying data types and provides flexibility in code.

---

### **Types of Polymorphism in C++**

#### **1. Compile-Time Polymorphism**
This type of polymorphism is achieved during compilation.

##### **a. Function Overloading**
- Multiple functions with the same name but different parameter lists.
- Allows performing similar operations with different types or number of arguments.

**Example:**
```cpp
#include <iostream>
using namespace std;

class Calculator {
public:
    // Function to add two integers
    int add(int a, int b) {
        return a + b;
    }

    // Function to add three integers
    int add(int a, int b, int c) {
        return a + b + c;
    }

    // Function to add two floating-point numbers
    double add(double a, double b) {
        return a + b;
    }
};

int main() {
    Calculator calc;
    cout << "Addition of two integers: " << calc.add(5, 10) << endl;
    cout << "Addition of three integers: " << calc.add(5, 10, 15) << endl;
    cout << "Addition of two doubles: " << calc.add(2.5, 3.5) << endl;

    return 0;
}
```

**Output:**
```
Addition of two integers: 15
Addition of three integers: 30
Addition of two doubles: 6
```

---

##### **b. Operator Overloading**
- Custom behavior for standard operators when applied to objects of user-defined classes.
- Common operators: `+`, `-`, `*`, `==`, etc.

**Example:**
```cpp
#include <iostream>
using namespace std;

class Complex {
private:
    double real, imag;

public:
    Complex(double r = 0, double i = 0) : real(r), imag(i) {}

    // Overload '+' operator
    Complex operator+(const Complex &c) {
        return Complex(real + c.real, imag + c.imag);
    }

    void display() {
        cout << real << " + " << imag << "i" << endl;
    }
};

int main() {
    Complex c1(3.0, 4.0), c2(1.0, 2.0);
    Complex c3 = c1 + c2;  // Using overloaded '+' operator
    c3.display();

    return 0;
}
```

**Output:**
```
4 + 6i
```

---

#### **2. Runtime Polymorphism**
This type of polymorphism is achieved during program execution using inheritance and virtual functions.

##### **a. Virtual Functions**
- A function in the base class that is declared as `virtual`.
- Allows overriding in derived classes.
- Supports dynamic dispatch using a base class pointer or reference.

**Example:**
```cpp
#include <iostream>
using namespace std;

class Animal {
public:
    virtual void sound() {  // Virtual function
        cout << "Animal makes a sound." << endl;
    }
};

class Dog : public Animal {
public:
    void sound() override {  // Override the base class function
        cout << "Dog barks." << endl;
    }
};

class Cat : public Animal {
public:
    void sound() override {  // Override the base class function
        cout << "Cat meows." << endl;
    }
};

int main() {
    Animal *animal;   // Base class pointer
    Dog dog;
    Cat cat;

    animal = &dog;
    animal->sound();  // Calls Dog's sound()

    animal = &cat;
    animal->sound();  // Calls Cat's sound()

    return 0;
}
```

**Output:**
```
Dog barks.
Cat meows.
```

---

##### **b. Abstract Classes**
- A class with at least one pure virtual function.
- Cannot instantiate abstract classes directly.
- Used as a base class to define an interface for derived classes.

**Example:**
```cpp
#include <iostream>
using namespace std;

class Shape {
public:
    virtual void draw() = 0;  // Pure virtual function
};

class Circle : public Shape {
public:
    void draw() override {
        cout << "Drawing Circle." << endl;
    }
};

class Rectangle : public Shape {
public:
    void draw() override {
        cout << "Drawing Rectangle." << endl;
    }
};

int main() {
    Shape *shape;  // Base class pointer
    Circle circle;
    Rectangle rectangle;

    shape = &circle;
    shape->draw();  // Calls Circle's draw()

    shape = &rectangle;
    shape->draw();  // Calls Rectangle's draw()

    return 0;
}
```

**Output:**
```
Drawing Circle.
Drawing Rectangle.
```

---

### **Comparison of Compile-Time and Runtime Polymorphism**

| **Feature**              | **Compile-Time Polymorphism**            | **Runtime Polymorphism**          |
|--------------------------|------------------------------------------|------------------------------------|
| **Achieved through**      | Function overloading, Operator overloading | Virtual functions, Abstract classes |
| **Binding**               | Static (at compile-time)                | Dynamic (at runtime)              |
| **Performance**           | Faster                                  | Slightly slower due to dynamic dispatch |
| **Use case**              | When behavior is fixed                  | When behavior depends on the derived class |

### **Encapsulation in C++**

Encapsulation is the bundling of data (variables) and methods (functions) that operate on that data into a single unit, typically a class. This principle ensures that the internal representation of an object is hidden from the outside world, and access is controlled through specific interfaces.

---

### **Key Features of Encapsulation**
1. **Data Hiding**: The internal details of an object are hidden from the outside.
2. **Access Control**: Data members are typically private, and access is provided through public methods (getters and setters).
3. **Improved Maintainability**: Changes to the implementation do not affect external code using the class.

---

### **Example: Using Private Members with Public Getter and Setter Methods**

**Code Example:**
```cpp
#include <iostream>
using namespace std;

class Employee {
private:
    int id;          // Private data member
    string name;     // Private data member

public:
    // Setter for id
    void setId(int empId) {
        id = empId;
    }

    // Getter for id
    int getId() {
        return id;
    }

    // Setter for name
    void setName(string empName) {
        name = empName;
    }

    // Getter for name
    string getName() {
        return name;
    }

    // Method to display employee details
    void display() {
        cout << "Employee ID: " << id << endl;
        cout << "Employee Name: " << name << endl;
    }
};

int main() {
    Employee emp;

    // Setting values using setter methods
    emp.setId(101);
    emp.setName("John Doe");

    // Accessing values using getter methods
    cout << "ID: " << emp.getId() << endl;
    cout << "Name: " << emp.getName() << endl;

    // Display details
    emp.display();

    return 0;
}
```

---

**Output:**
```
ID: 101
Name: John Doe
Employee ID: 101
Employee Name: John Doe
```

---

### **Benefits of Encapsulation**
1. **Security**: Protects sensitive data by restricting access to internal details.
2. **Modularity**: Each object controls its own state, making the program modular and easier to debug.
3. **Control**: Provides control over the data by using getters and setters.
4. **Flexibility**: Internal implementation can be changed without altering external code.

---
### **Vectors in C++**
A **vector** in C++ is a dynamic array provided by the **Standard Template Library (STL)**. Unlike arrays, vectors can grow or shrink dynamically as elements are added or removed. They are implemented as **templates** in the `<vector>` header.

---

### **Key Features of Vectors**
1. **Dynamic Size**: Vectors automatically resize when elements are added or removed.
2. **Random Access**: Elements can be accessed directly using indices, just like arrays.
3. **Efficient Insertion/Deletion**: Insertion at the end of a vector is efficient, but insertion/deletion in the middle requires shifting elements.
4. **Type Safety**: Since vectors are templates, you can create vectors of any data type.
5. **Built-in Methods**: Vectors provide many useful functions, such as adding, removing, and searching for elements.

---

### **Basic Syntax**
```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    // Declare a vector of integers
    vector<int> v;

    // Add elements
    v.push_back(10);
    v.push_back(20);
    v.push_back(30);

    // Access elements
    cout << "Element at index 0: " << v[0] << endl;

    // Remove the last element
    v.pop_back();

    // Display size
    cout << "Size of vector: " << v.size() << endl;

    return 0;
}
```

---

### **Common Functions**
1. **Initialization**:
   ```cpp
   vector<int> v;                      // Empty vector
   vector<int> v(5, 10);               // Vector of size 5, initialized with 10
   vector<int> v2 = {1, 2, 3, 4, 5};   // Initialization with a list
   ```

2. **Adding Elements**:
   - `push_back(value)`: Appends an element to the end.
   - `emplace_back(value)`: Constructs an element at the end.

3. **Removing Elements**:
   - `pop_back()`: Removes the last element.
   - `erase(iterator)`: Removes an element at the specified position.
   - `clear()`: Removes all elements.

4. **Accessing Elements**:
   - `v[index]`: Access by index (no bounds checking).
   - `v.at(index)`: Access by index with bounds checking.
   - `front()`: Returns the first element.
   - `back()`: Returns the last element.

5. **Size and Capacity**:
   - `size()`: Number of elements in the vector.
   - `capacity()`: Space allocated for the vector (can be greater than `size()`).
   - `resize(new_size)`: Resizes the vector.

6. **Iterators**:
   - `begin()`, `end()`: Access the start and end of the vector.
   - `rbegin()`, `rend()`: Access in reverse order.

---

### **Examples**

#### **1. Basic Vector Operations**
```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> v = {10, 20, 30, 40};

    // Adding elements
    v.push_back(50);

    // Accessing elements
    for (int i = 0; i < v.size(); i++) {
        cout << v[i] << " ";
    }
    cout << endl;

    // Removing elements
    v.pop_back();
    v.erase(v.begin() + 1); // Remove element at index 1

    // Display remaining elements
    for (int x : v) {
        cout << x << " ";
    }
    cout << endl;

    return 0;
}
```

#### **2. Using Iterators**
```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<int> v = {1, 2, 3, 4, 5};

    // Using iterators to traverse the vector
    for (auto it = v.begin(); it != v.end(); ++it) {
        cout << *it << " ";
    }
    cout << endl;

    return 0;
}
```

#### **3. Working with 2D Vectors**
```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    vector<vector<int>> matrix = {
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 9}
    };

    // Display the 2D vector
    for (auto row : matrix) {
        for (auto col : row) {
            cout << col << " ";
        }
        cout << endl;
    }

    return 0;
}
```

#### **4. Sorting a Vector**
```cpp
#include <iostream>
#include <vector>
#include <algorithm> // For sort()
using namespace std;

int main() {
    vector<int> v = {40, 10, 30, 20};

    // Sort the vector
    sort(v.begin(), v.end());

    // Display sorted vector
    for (int x : v) {
        cout << x << " ";
    }
    cout << endl;

    return 0;
}
```

---

### **Advantages of Vectors**
- Dynamic resizing without manual memory management.
- Provides extensive member functions for easier manipulation.
- Supports iterators for flexible traversal.

---

### **Disadvantages of Vectors**
- Resizing can involve copying all elements to a new memory block.
- Random insertions and deletions (except at the end) are less efficient due to shifting elements.

---

### **When to Use Vectors**
- When you need a dynamic array that can resize automatically.
- When you require built-in methods for easy data management.
- For use cases where frequent addition/removal happens at the end of the array.