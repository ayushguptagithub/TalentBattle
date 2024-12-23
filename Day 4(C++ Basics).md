### **Introduction to C++**
C++ is a high-level programming language developed by Bjarne Stroustrup in 1983. It is widely used for system programming, application development, and competitive programming due to its efficiency and flexibility.

C++ supports multiple programming paradigms, including:
1. **Procedural programming** (like C)
2. **Object-oriented programming** (OOP)
3. **Generic programming**

---

### **Basic Structure of a C++ Program**
Here's a simple "Hello, World!" program in C++:

```cpp
#include <iostream> // Header file for input-output stream

using namespace std; // Allows using standard namespace

int main() {
    cout << "Hello, World!" << endl; // Output statement
    return 0; // Indicates successful program termination
}
```

### Explanation:
- `#include <iostream>`: Includes the input-output library.
- `using namespace std;`: Enables access to standard library objects (like `cout` and `endl`) without prefixing them with `std::`.
- `int main()`: The entry point of the program.
- `cout`: Used to output text to the console.
- `return 0;`: Ends the program.

---

### **Key Features of C++**
1. **Variables and Data Types**  
   Example:
   ```cpp
   #include <iostream>
   using namespace std;

   int main() {
       int age = 25; // Integer variable
       float height = 5.9; // Floating-point variable
       char grade = 'A'; // Character variable
       bool isStudent = true; // Boolean variable

       cout << "Age: " << age << endl;
       cout << "Height: " << height << endl;
       cout << "Grade: " << grade << endl;
       cout << "Is Student: " << isStudent << endl;

       return 0;
   }
   ```

### **Conditional Statements in C++**

Conditional statements allow a program to make decisions based on certain conditions. These statements help in controlling the flow of execution in a program.

---

### **Types of Conditional Statements**
1. **if Statement**  
2. **if-else Statement**  
3. **else-if Ladder**  
4. **Nested if Statement**  
5. **switch Statement**

---

### **1. if Statement**  
Executes a block of code if the condition evaluates to `true`.  

**Syntax**:
```cpp
if (condition) {
    // Code to execute if condition is true
}
```

**Example**:
```cpp
#include <iostream>
using namespace std;

int main() {
    int age = 18;

    if (age >= 18) {
        cout << "You are eligible to vote." << endl;
    }

    return 0;
}
```

---

### **2. if-else Statement**  
Executes one block of code if the condition is `true`, otherwise executes another block of code.

**Syntax**:
```cpp
if (condition) {
    // Code to execute if condition is true
} else {
    // Code to execute if condition is false
}
```

**Example**:
```cpp
#include <iostream>
using namespace std;

int main() {
    int number = 10;

    if (number % 2 == 0) {
        cout << "The number is even." << endl;
    } else {
        cout << "The number is odd." << endl;
    }

    return 0;
}
```

---

### **3. else-if Ladder**  
Used to test multiple conditions sequentially.

**Syntax**:
```cpp
if (condition1) {
    // Code for condition1
} else if (condition2) {
    // Code for condition2
} else {
    // Code if all conditions are false
}
```

**Example**:
```cpp
#include <iostream>
using namespace std;

int main() {
    int marks = 75;

    if (marks >= 90) {
        cout << "Grade: A" << endl;
    } else if (marks >= 75) {
        cout << "Grade: B" << endl;
    } else if (marks >= 50) {
        cout << "Grade: C" << endl;
    } else {
        cout << "Grade: F" << endl;
    }

    return 0;
}
```

---

### **4. Nested if Statement**  
An `if` statement inside another `if` statement.

**Syntax**:
```cpp
if (condition1) {
    if (condition2) {
        // Code if both condition1 and condition2 are true
    }
}
```

**Example**:
```cpp
#include <iostream>
using namespace std;

int main() {
    int age = 20;
    bool hasVoterID = true;

    if (age >= 18) {
        if (hasVoterID) {
            cout << "You are eligible to vote." << endl;
        } else {
            cout << "You need a voter ID to vote." << endl;
        }
    } else {
        cout << "You are not eligible to vote." << endl;
    }

    return 0;
}
```

---

### **5. switch Statement**  
Used to test a variable against multiple values.

**Syntax**:
```cpp
switch (expression) {
    case value1:
        // Code for case 1
        break;
    case value2:
        // Code for case 2
        break;
    // Add more cases as needed
    default:
        // Code if no cases match
}
```

**Example**:
```cpp
#include <iostream>
using namespace std;

int main() {
    int day = 3;

    switch (day) {
        case 1:
            cout << "Monday" << endl;
            break;
        case 2:
            cout << "Tuesday" << endl;
            break;
        case 3:
            cout << "Wednesday" << endl;
            break;
        case 4:
            cout << "Thursday" << endl;
            break;
        case 5:
            cout << "Friday" << endl;
            break;
        default:
            cout << "Weekend" << endl;
    }

    return 0;
}
```

---

### **Conclusion**
Conditional statements in C++ allow dynamic decision-making in programs. Each type of statement has specific use cases, and choosing the right one depends on the scenario.


### **Loops in C++**

Loops are used in programming to execute a block of code repeatedly based on a condition. C++ provides three main types of loops:  

---

### **Types of Loops in C++**
1. **for Loop**  
2. **while Loop**  
3. **do-while Loop**

---

### **1. for Loop**  
The `for` loop is used when the number of iterations is known beforehand.  

**Syntax**:
```cpp
for (initialization; condition; increment/decrement) {
    // Code to be executed
}
```

**Example**:
```cpp
#include <iostream>
using namespace std;

int main() {
    for (int i = 1; i <= 5; i++) {
        cout << "Iteration: " << i << endl;
    }
    return 0;
}
```

**Explanation**:
- `int i = 1;`: Initialization (loop starts with `i = 1`).
- `i <= 5;`: Condition (loop runs while `i` is less than or equal to 5).
- `i++`: Increment (value of `i` increases by 1 after each iteration).

---

### **2. while Loop**  
The `while` loop is used when the number of iterations is not fixed and depends on a condition.

**Syntax**:
```cpp
while (condition) {
    // Code to be executed
}
```

**Example**:
```cpp
#include <iostream>
using namespace std;

int main() {
    int count = 1;

    while (count <= 5) {
        cout << "Count: " << count << endl;
        count++;
    }
    return 0;
}
```

**Explanation**:
- The loop continues until the condition (`count <= 5`) is false.
- `count++` increments the value of `count` in each iteration.

---

### **3. do-while Loop**  
The `do-while` loop executes the code block at least once before checking the condition.

**Syntax**:
```cpp
do {
    // Code to be executed
} while (condition);
```

**Example**:
```cpp
#include <iostream>
using namespace std;

int main() {
    int number = 1;

    do {
        cout << "Number: " << number << endl;
        number++;
    } while (number <= 5);

    return 0;
}
```

**Explanation**:
- The block inside `do` is executed once before the condition (`number <= 5`) is checked.

---

### **4. Nested Loops**  
A loop inside another loop.

**Example**:
```cpp
#include <iostream>
using namespace std;

int main() {
    for (int i = 1; i <= 3; i++) {
        for (int j = 1; j <= 2; j++) {
            cout << "i: " << i << ", j: " << j << endl;
        }
    }
    return 0;
}
```

**Output**:
```
i: 1, j: 1
i: 1, j: 2
i: 2, j: 1
i: 2, j: 2
i: 3, j: 1
i: 3, j: 2
```

---

### **5. Infinite Loops**  
Loops that run indefinitely if the condition is always `true`.  

**Example (Avoid running this without a break condition)**:
```cpp
#include <iostream>
using namespace std;

int main() {
    while (true) {
        cout << "This is an infinite loop!" << endl;
    }
    return 0;
}
```

**Solution**: Use `break` to exit the loop.

---

### **6. Breaking Out of a Loop**
The `break` statement terminates the loop immediately.

**Example**:
```cpp
#include <iostream>
using namespace std;

int main() {
    for (int i = 1; i <= 10; i++) {
        if (i == 5) {
            break; // Exit the loop when i is 5
        }
        cout << "i: " << i << endl;
    }
    return 0;
}
```

---

### **7. Skipping an Iteration**
The `continue` statement skips the current iteration and moves to the next.

**Example**:
```cpp
#include <iostream>
using namespace std;

int main() {
    for (int i = 1; i <= 5; i++) {
        if (i == 3) {
            continue; // Skip the iteration when i is 3
        }
        cout << "i: " << i << endl;
    }
    return 0;
}
```

---

### **Conclusion**
Loops are essential for repetitive tasks in programming. Choosing the right loop depends on whether you know the number of iterations (`for`), need to check a condition (`while`), or require the code to execute at least once (`do-while`).