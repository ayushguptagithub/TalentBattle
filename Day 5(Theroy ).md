### Arrays in C++

An **array** is a collection of elements of the same data type stored in contiguous memory locations. Arrays in C++ allow you to store multiple values of the same type using a single variable name, enabling efficient storage and access.

#### **Declaration of Arrays**
To declare an array in C++, use the following syntax:
```cpp
data_type array_name[array_size];
```

- **`data_type`**: The type of elements the array will hold (e.g., `int`, `float`, `char`, etc.).
- **`array_name`**: The name of the array.
- **`array_size`**: The number of elements the array can hold.

#### **Example: Declaring and Initializing an Array**
```cpp
#include <iostream>
using namespace std;

int main() {
    int numbers[5] = {1, 2, 3, 4, 5}; // Declaration and initialization
    cout << "First element: " << numbers[0] << endl; // Accessing elements
    cout << "Last element: " << numbers[4] << endl; 
    return 0;
}
```

---

#### **Accessing Array Elements**
Array elements are accessed using indices. Indexing starts from `0` in C++.
```cpp
array_name[index];
```

#### **Example: Accessing and Modifying Elements**
```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[3] = {10, 20, 30};
    cout << "Original: " << arr[1] << endl; // Access element at index 1
    arr[1] = 50; // Modify the element
    cout << "Modified: " << arr[1] << endl;
    return 0;
}
```

---

#### **Array Traversal**
You can use loops to traverse through arrays.

**Example: Traversing an Array**
```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[5] = {1, 2, 3, 4, 5};

    cout << "Array elements:" << endl;
    for (int i = 0; i < 5; i++) {
        cout << arr[i] << " ";
    }
    return 0;
}
```

---

#### **Multidimensional Arrays**
C++ supports multidimensional arrays, such as 2D arrays, which are arrays of arrays.

**Syntax for 2D Arrays:**
```cpp
data_type array_name[rows][columns];
```

**Example: Declaring and Initializing a 2D Array**
```cpp
#include <iostream>
using namespace std;

int main() {
    int matrix[2][3] = {
        {1, 2, 3},
        {4, 5, 6}
    };

    cout << "2D Array elements:" << endl;
    for (int i = 0; i < 2; i++) {
        for (int j = 0; j < 3; j++) {
            cout << matrix[i][j] << " ";
        }
        cout << endl;
    }
    return 0;
}
```

---

#### **Dynamic Arrays**
Dynamic arrays allow for runtime size allocation using pointers or libraries like `std::vector`.

**Example: Using `new` for Dynamic Arrays**
```cpp
#include <iostream>
using namespace std;

int main() {
    int size;
    cout << "Enter size of array: ";
    cin >> size;

    int* arr = new int[size]; // Dynamic allocation
    for (int i = 0; i < size; i++) {
        arr[i] = i + 1; // Assign values
    }

    cout << "Dynamic Array elements:" << endl;
    for (int i = 0; i < size; i++) {
        cout << arr[i] << " ";
    }

    delete[] arr; // Free memory
    return 0;
}
```

---

#### **Common Operations on Arrays**
1. **Find the largest or smallest element:**
   ```cpp
   int largest = arr[0];
   for (int i = 1; i < size; i++) {
       if (arr[i] > largest) {
           largest = arr[i];
       }
   }
   ```

2. **Sum of elements:**
   ```cpp
   int sum = 0;
   for (int i = 0; i < size; i++) {
       sum += arr[i];
   }
   ```

3. **Reversing an array:**
   ```cpp
   for (int i = 0; i < size / 2; i++) {
       swap(arr[i], arr[size - i - 1]);
   }
   ```

---

### **Key Points About Arrays**
- **Fixed size:** Once declared, the size of the array cannot be changed.
- **Efficient access:** Direct access using indices provides fast retrieval and updates.
- **Contiguous memory:** All elements are stored sequentially in memory.
- **Limitations:** Arrays do not support resizing, and out-of-bound access can lead to undefined behavior.

### Functions in C++

A **function** is a block of code that performs a specific task and can be reused multiple times. Functions are an essential part of modular programming, making code more organized, readable, and reusable.

---

#### **Function Syntax**
```cpp
return_type function_name(parameters) {
    // Body of the function
    return value; // Optional (if return_type is not `void`)
}
```

- **`return_type`**: The data type of the value returned by the function (e.g., `int`, `float`, `void`).
- **`function_name`**: The name of the function.
- **`parameters`**: Inputs to the function (optional).
- **`return`**: The keyword to send back a value (optional for `void` functions).

---

### **Types of Functions**

#### 1. **Built-in Functions**
Functions provided by the C++ Standard Library (e.g., `cout`, `cin`, `sqrt`, etc.).

#### 2. **User-defined Functions**
Functions created by the programmer for specific tasks.

---

### **Example of a User-Defined Function**

```cpp
#include <iostream>
using namespace std;

// Function to add two numbers
int add(int a, int b) {
    return a + b; // Return the sum
}

int main() {
    int x = 10, y = 20;
    cout << "Sum: " << add(x, y) << endl; // Calling the function
    return 0;
}
```

---

### **Function Components**

1. **Function Declaration (Prototype)**:
   Specifies the function's name, return type, and parameters without the body.
   ```cpp
   return_type function_name(parameters);
   ```

2. **Function Definition**:
   Contains the function's body and actual implementation.
   ```cpp
   return_type function_name(parameters) {
       // Code to perform the task
   }
   ```

3. **Function Call**:
   Executes the function by providing actual arguments.
   ```cpp
   function_name(arguments);
   ```

---

### **Types of Function Parameters**

1. **Pass by Value**
   A copy of the argument is passed to the function. Changes made inside the function do not affect the original variable.

   **Example:**
   ```cpp
   void modify(int x) {
       x += 10;
   }

   int main() {
       int a = 5;
       modify(a);
       cout << "a: " << a << endl; // Output: 5
       return 0;
   }
   ```

2. **Pass by Reference**
   The actual address of the variable is passed, allowing the function to modify the original value.

   **Example:**
   ```cpp
   void modify(int &x) {
       x += 10;
   }

   int main() {
       int a = 5;
       modify(a);
       cout << "a: " << a << endl; // Output: 15
       return 0;
   }
   ```

3. **Default Arguments**
   Allows specifying default values for parameters if no argument is passed during the function call.

   **Example:**
   ```cpp
   int multiply(int a, int b = 2) {
       return a * b;
   }

   int main() {
       cout << multiply(5) << endl;    // Output: 10
       cout << multiply(5, 3) << endl; // Output: 15
       return 0;
   }
   ```

---

### **Function Overloading**
Function overloading allows multiple functions with the same name but different parameter lists.

**Example:**
```cpp
#include <iostream>
using namespace std;

int add(int a, int b) {
    return a + b;
}

double add(double a, double b) {
    return a + b;
}

int main() {
    cout << "Int addition: " << add(10, 20) << endl;       // Calls int version
    cout << "Double addition: " << add(1.5, 2.5) << endl; // Calls double version
    return 0;
}
```

---

### **Inline Functions**
Functions defined with the `inline` keyword have their code expanded at the call site, reducing the overhead of a function call.

**Example:**
```cpp
inline int square(int x) {
    return x * x;
}

int main() {
    cout << "Square: " << square(5) << endl; // Output: 25
    return 0;
}
```

---

### **Recursive Functions**
A recursive function calls itself until a base condition is met.

**Example: Factorial Using Recursion**
```cpp
#include <iostream>
using namespace std;

int factorial(int n) {
    if (n == 0 || n == 1) return 1; // Base case
    return n * factorial(n - 1);    // Recursive call
}

int main() {
    cout << "Factorial of 5: " << factorial(5) << endl; // Output: 120
    return 0;
}
```

---

### **Lambda Functions**
C++ supports **lambda expressions** for creating anonymous functions.

**Example:**
```cpp
#include <iostream>
using namespace std;

int main() {
    auto add = [](int a, int b) { return a + b; };
    cout << "Sum: " << add(3, 7) << endl; // Output: 10
    return 0;
}
```

---

### **Key Points About Functions**
- Functions improve code modularity and reusability.
- Pass by reference allows modifying the original variable.
- Function overloading enhances flexibility by supporting multiple parameter sets.
- Inline functions reduce call overhead for small, frequently used functions.
- Use recursion judiciously to avoid stack overflow errors.


### Strings in C++

Strings are sequences of characters used to store and manipulate text. In C++, strings can be handled in two primary ways:

1. **C-style Strings** (using character arrays).
2. **C++ Standard Library Strings** (using `std::string`).

---

### **C-style Strings**

C-style strings are arrays of characters terminated by a special character `'\0'` (null character).

#### **Declaring and Initializing C-style Strings**
```cpp
#include <iostream>
using namespace std;

int main() {
    char str1[] = "Hello"; // Automatically includes the null character
    char str2[6] = "World"; // Specify size (5 characters + 1 null character)
    char str3[] = {'C', '+', '+', '\0'}; // Explicit null character

    cout << str1 << " " << str2 << " " << str3 << endl; // Output: Hello World C++
    return 0;
}
```

#### **Common Operations with C-style Strings**
Functions for C-style strings are provided in the `<cstring>` library.

1. **Length of a String**: `strlen`
   ```cpp
   #include <iostream>
   #include <cstring>
   using namespace std;

   int main() {
       char str[] = "C++";
       cout << "Length: " << strlen(str) << endl; // Output: 3
       return 0;
   }
   ```

2. **Copy a String**: `strcpy`
   ```cpp
   char dest[10];
   strcpy(dest, "Hello");
   ```

3. **Concatenate Strings**: `strcat`
   ```cpp
   char str1[20] = "Hello, ";
   strcat(str1, "World!");
   ```

4. **Compare Strings**: `strcmp`
   ```cpp
   if (strcmp("abc", "abc") == 0) {
       cout << "Strings are equal!" << endl;
   }
   ```

---

### **C++ Strings (`std::string`)**

The C++ Standard Library provides the `std::string` class for easier and more versatile string manipulation. It eliminates the need to manually manage null characters.

#### **Declaring and Initializing `std::string`**
```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string str1 = "Hello";
    string str2("World");
    string str3(str1 + ", " + str2); // Concatenation

    cout << str3 << endl; // Output: Hello, World
    return 0;
}
```

---

### **Common Operations with `std::string`**

1. **Length of a String**: `size()` or `length()`
   ```cpp
   string str = "Hello";
   cout << "Length: " << str.length() << endl; // Output: 5
   ```

2. **Accessing Characters**: `[]` or `.at()`
   ```cpp
   string str = "Hello";
   cout << str[0] << endl;    // Output: H
   cout << str.at(1) << endl; // Output: e
   ```

3. **Appending Strings**: `+=` or `append()`
   ```cpp
   string str = "Hello";
   str += " World";
   str.append("!");
   cout << str << endl; // Output: Hello World!
   ```

4. **Substring**: `substr()`
   ```cpp
   string str = "Hello, World!";
   cout << str.substr(0, 5) << endl; // Output: Hello
   ```

5. **Find Substring**: `find()`
   ```cpp
   string str = "Hello, World!";
   cout << str.find("World") << endl; // Output: 7
   ```

6. **Replace Substring**: `replace()`
   ```cpp
   string str = "Hello, World!";
   str.replace(7, 5, "C++");
   cout << str << endl; // Output: Hello, C++!
   ```

7. **Erase Characters**: `erase()`
   ```cpp
   string str = "Hello, World!";
   str.erase(5, 7);
   cout << str << endl; // Output: Hello!
   ```

8. **Insert Substring**: `insert()`
   ```cpp
   string str = "Hello!";
   str.insert(5, ", World");
   cout << str << endl; // Output: Hello, World!
   ```

9. **Compare Strings**: `compare()`
   ```cpp
   string str1 = "abc";
   string str2 = "xyz";
   if (str1.compare(str2) < 0) {
       cout << "str1 is less than str2" << endl;
   }
   ```

---

### **Iterating Over Characters**

**Using a For Loop:**
```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string str = "C++ Strings";
    for (char c : str) {
        cout << c << " ";
    }
    return 0;
}
```

---

### **Input and Output**

1. **Taking Input**:
   ```cpp
   string str;
   getline(cin, str); // Reads entire line including spaces
   ```

2. **Output**:
   ```cpp
   cout << str << endl;
   ```

---

### **Example: Reverse a String**
```cpp
#include <iostream>
#include <string>
#include <algorithm>
using namespace std;

int main() {
    string str = "Hello";
    reverse(str.begin(), str.end());
    cout << str << endl; // Output: olleH
    return 0;
}
```

---

### **Example: Count Vowels in a String**
```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string str = "Hello, World!";
    int count = 0;

    for (char c : str) {
        c = tolower(c); // Convert to lowercase
        if (c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u') {
            count++;
        }
    }

    cout << "Number of vowels: " << count << endl; // Output: 3
    return 0;
}
```

---

### **Key Points**
1. **C-style Strings** are simple but require manual management of null characters.
2. **`std::string`** provides a modern, flexible approach to string manipulation in C++.
3. Use `<cstring>` for C-style string operations and `<string>` for `std::string`. 
4. `std::string` is recommended for most cases due to its safety and ease of use.


