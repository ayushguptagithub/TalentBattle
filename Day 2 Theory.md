### Arrays in C: A Complete Overview

An **array** in C is a collection of elements of the same data type stored in contiguous memory locations. Arrays are used when you want to store multiple values in a single variable, rather than declaring individual variables for each value.

#### Characteristics of Arrays:
1. **Fixed Size:** Once the size of an array is defined, it cannot be changed.
2. **Indexed:** Elements in an array are accessed using an index (starting from 0).
3. **Contiguous Memory Allocation:** All elements are stored in adjacent memory locations.
4. **Same Data Type:** All elements in an array must be of the same data type (int, float, char, etc.).

### Types of Arrays:
1. **1D Array (Single Dimensional Array):**
   - Stores a list of elements.
2. **2D Array (Two Dimensional Array):**
   - Can be visualized as a table or matrix with rows and columns.
3. **Multidimensional Arrays:** 
   - Arrays with more than two dimensions (3D, 4D, etc.).

---

### 1. **Single Dimensional Array (1D Array)**

A 1D array stores a list of elements of the same type.

#### Syntax:
```c
data_type array_name[size];
```

Where:
- `data_type`: The type of data the array will store (e.g., `int`, `float`).
- `array_name`: The name of the array.
- `size`: The number of elements the array can hold.

#### Example Code for 1D Array:

```c
#include <stdio.h>

int main() {
    int arr[5]; // Declare an array of size 5

    // Input values
    printf("Enter 5 integers: ");
    for (int i = 0; i < 5; i++) {
        scanf("%d", &arr[i]);
    }

    // Output values
    printf("You entered: ");
    for (int i = 0; i < 5; i++) {
        printf("%d ", arr[i]);
    }

    return 0;
}
```

**Output:**
```
Enter 5 integers: 1 2 3 4 5
You entered: 1 2 3 4 5
```

### 2. **Two Dimensional Array (2D Array)**

A 2D array is a matrix-like structure. It can be visualized as a table with rows and columns.

#### Syntax:
```c
data_type array_name[rows][columns];
```

Where:
- `rows`: Number of rows in the array.
- `columns`: Number of columns in the array.

#### Example Code for 2D Array:

```c
#include <stdio.h>

int main() {
    int arr[3][3]; // Declare a 3x3 matrix

    // Input values
    printf("Enter 9 integers for a 3x3 matrix:\n");
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            scanf("%d", &arr[i][j]);
        }
    }

    // Output values (matrix)
    printf("The entered 3x3 matrix is:\n");
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            printf("%d ", arr[i][j]);
        }
        printf("\n");
    }

    return 0;
}
```

**Output:**
```
Enter 9 integers for a 3x3 matrix:
1 2 3 4 5 6 7 8 9
The entered 3x3 matrix is:
1 2 3 
4 5 6 
7 8 9
```




---

### Important Array Operations in C:

1. **Accessing Array Elements:**
   - You can access elements in an array using their index: `array_name[index]`.

2. **Initializing Arrays:**
   - You can initialize an array at the time of declaration:
     ```c
     int arr[] = {1, 2, 3, 4, 5};
     ```

3. **Passing Arrays to Functions:**
   - Arrays can be passed to functions by specifying the array name (without the size):
     ```c
     void printArray(int arr[], int size) {
         for (int i = 0; i < size; i++) {
             printf("%d ", arr[i]);
         }
     }
     ```

4. **Array Size:**
   - The size of an array is fixed and can be determined using `sizeof`:
     ```c
     int arr[5];
     printf("Size of array: %zu\n", sizeof(arr)/sizeof(arr[0]));  // Size in terms of number of elements
     ```

---

### Example Program: Array Sum and Average

```c
#include <stdio.h>

int main() {
    int arr[5] = {1, 2, 3, 4, 5};
    int sum = 0;
    float average;

    // Calculate the sum
    for (int i = 0; i < 5; i++) {
        sum += arr[i];
    }

    // Calculate the average
    average = sum / 5.0;

    printf("Sum: %d\n", sum);
    printf("Average: %.2f\n", average);

    return 0;
}
```

**Output:**
```
Sum: 15
Average: 3.00
```

---

### Functions in C: A Complete Overview

A **function** in C is a block of code that performs a specific task. Functions allow for better organization, code reuse, and modularity. You can break down complex tasks into smaller, manageable pieces by using functions.

### Function Components:
1. **Function Declaration (Prototype):** This tells the compiler about the function's name, return type, and parameters before the function is used.
2. **Function Definition:** This contains the actual code that runs when the function is called.
3. **Function Call:** This is where you invoke the function to execute its code.

### Function Syntax:

```c
return_type function_name(parameter1, parameter2, ...) {
    // Function body
    // Code that performs the task
}
```

Where:
- `return_type` specifies the type of value the function will return. If it doesn't return anything, it will be `void`.
- `function_name` is the name of the function.
- `parameter1, parameter2, ...` are the input values to the function (optional).

### Types of Functions:
1. **Standard Library Functions**: Functions provided by C standard library (e.g., `printf`, `scanf`).
2. **User-Defined Functions**: Functions written by the programmer to perform specific tasks.

---

### **Function Declaration (Prototype)**

A function prototype is a declaration of the function before its definition. It is used to inform the compiler about the function’s name, return type, and parameters so it can check the function calls.

#### Syntax:
```c
return_type function_name(parameter1, parameter2, ...);
```

Example:

```c
int add(int, int); // Function prototype
```

---

### **Function Definition**

This is where the actual code for the function resides.

#### Syntax:
```c
return_type function_name(parameter1, parameter2, ...) {
    // Function body
}
```

Example:

```c
int add(int a, int b) {
    return a + b;
}
```

---

### **Function Call**

To execute the function, you need to call it in the main program or any other function.

#### Syntax:
```c
function_name(parameter1, parameter2, ...);
```

Example:

```c
int sum = add(5, 3); // Calling the 'add' function
```

---

### **Function Example in C**

#### 1. **Simple Function to Add Two Numbers**

```c
#include <stdio.h>

// Function declaration
int add(int a, int b);

int main() {
    int num1, num2, result;

    // Taking input
    printf("Enter two numbers: ");
    scanf("%d %d", &num1, &num2);

    // Function call
    result = add(num1, num2);

    // Output the result
    printf("The sum of %d and %d is: %d\n", num1, num2, result);

    return 0;
}

// Function definition
int add(int a, int b) {
    return a + b;
}
```

**Output:**
```
Enter two numbers: 5 7
The sum of 5 and 7 is: 12
```

---

#### 2. **Function with No Return Value (`void` function)**

A function that does not return any value uses `void` as the return type.

```c
#include <stdio.h>

// Function declaration
void greet(void);

int main() {
    // Function call
    greet();

    return 0;
}

// Function definition
void greet() {
    printf("Hello, welcome to C programming!\n");
}
```

**Output:**
```
Hello, welcome to C programming!
```

---

#### 3. **Function Returning a Value**

The following example demonstrates a function that calculates the factorial of a number.

```c
#include <stdio.h>

// Function prototype
int factorial(int n);

int main() {
    int num, result;

    // Input
    printf("Enter a number: ");
    scanf("%d", &num);

    // Function call
    result = factorial(num);

    // Output
    printf("Factorial of %d is %d\n", num, result);

    return 0;
}

// Function definition
int factorial(int n) {
    if (n == 0 || n == 1) {
        return 1;
    }
    return n * factorial(n - 1); // Recursive function call
}
```

**Output:**
```
Enter a number: 5
Factorial of 5 is 120
```

---

#### 4. **Function with Multiple Parameters**

You can pass multiple parameters to a function.

```c
#include <stdio.h>

// Function prototype
int multiply(int a, int b, int c);

int main() {
    int result;

    // Function call with multiple arguments
    result = multiply(2, 3, 4);

    // Output
    printf("The result is: %d\n", result);

    return 0;
}

// Function definition
int multiply(int a, int b, int c) {
    return a * b * c; // Multiply three numbers
}
```

**Output:**
```
The result is: 24
```

---

### **Return Type `void`**

A `void` function doesn't return a value. Instead, it performs actions like printing or modifying values directly.

#### Example of `void` function:

```c
#include <stdio.h>

// Function prototype
void printMessage(void);

int main() {
    // Function call
    printMessage();

    return 0;
}

// Function definition
void printMessage() {
    printf("This is a message from a void function!\n");
}
```

**Output:**
```
This is a message from a void function!
```

---

### **Pass by Value vs Pass by Reference**

1. **Pass by Value:**
   - The actual value of the argument is passed to the function. Any changes made to the parameter inside the function do not affect the original variable.
   - Example (pass-by-value is the default in C):
     ```c
     void modify(int x) {
         x = 10;  // Changes are local to the function
     }
     ```

2. **Pass by Reference (using pointers):**
   - Instead of passing the actual value, the address (reference) of the argument is passed. This allows the function to modify the actual argument.
   - Example (pass-by-reference):
     ```c
     void modify(int *x) {
         *x = 10;  // Changes the actual value of the passed argument
     }
     ```

---

### **Recursive Function Example:**

A **recursive function** is one that calls itself to solve smaller subproblems. For example, the factorial function is often written recursively.

```c
#include <stdio.h>

// Function prototype
int factorial(int n);

int main() {
    int result = factorial(5);
    printf("Factorial of 5 is: %d\n", result);

    return 0;
}

// Function definition
int factorial(int n) {
    if (n <= 1) {
        return 1;  // Base case
    } else {
        return n * factorial(n - 1);  // Recursive case
    }
}
```

**Output:**
```
Factorial of 5 is: 120
```

---

### Conclusion:

- Functions allow you to break your program into modular blocks of code that can be reused and tested independently.
- Functions can return values, accept parameters, or even perform actions with no return type (`void`).
- Understanding how to use functions effectively in C is key to writing clean, maintainable code.



