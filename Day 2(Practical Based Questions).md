

### 1. **Find the Largest Element in an Array**

```c
#include <stdio.h>

int main() {
    int arr[] = {5, 7, 2, 9, 11};
    int n = sizeof(arr) / sizeof(arr[0]);
    int largest = arr[0];

    for (int i = 1; i < n; i++) {
        if (arr[i] > largest) {
            largest = arr[i];
        }
    }

    printf("Largest element is: %d\n", largest);
    return 0;
}
```

**Output:**
```
Largest element is: 11
```

---

### 2. **Reverse the Elements of an Array**

```c
#include <stdio.h>

int main() {
    int arr[] = {1, 2, 3, 4, 5};
    int n = sizeof(arr) / sizeof(arr[0]);

    // Reverse the array
    for (int i = 0; i < n / 2; i++) {
        int temp = arr[i];
        arr[i] = arr[n - i - 1];
        arr[n - i - 1] = temp;
    }

    // Print the reversed array
    printf("Reversed array: ");
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");

    return 0;
}
```

**Output:**
```
Reversed array: 5 4 3 2 1
```

---

### 3. **Count Occurrences of Each Element in an Array**

```c
#include <stdio.h>

int main() {
    int arr[] = {1, 2, 2, 3, 3, 3};
    int n = sizeof(arr) / sizeof(arr[0]);

    // Count occurrences of each element
    for (int i = 0; i < n; i++) {
        int count = 1;
        if (arr[i] != -1) {
            for (int j = i + 1; j < n; j++) {
                if (arr[i] == arr[j]) {
                    count++;
                    arr[j] = -1; // Mark the element as counted
                }
            }
            printf("%d: %d\n", arr[i], count);
        }
    }

    return 0;
}
```

**Output:**
```
1: 1
2: 2
3: 3
```

---

### 4. **Find the Sum of Diagonal Elements of a 2D Matrix**

```c
#include <stdio.h>

int main() {
    int matrix[3][3] = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
    int sum = 0;

    // Loop through the matrix and sum the diagonal elements
    for (int i = 0; i < 3; i++) {
        sum += matrix[i][i];  // Primary diagonal elements
    }

    printf("Sum of diagonal elements is: %d\n", sum);
    return 0;
}
```

**Output:**
```
Sum of diagonal elements is: 15
```




### Strings in C

A **string** in C is a sequence of characters, terminated by a null character (`'\0'`). Strings in C are not a built-in data type like in some other languages. Instead, they are represented as arrays of characters. A string can be defined as:

```c
char str[] = "Hello, World!";
```

Or equivalently, as:

```c
char str[50] = "Hello, World!";
```

In C, strings are essentially arrays of characters, and their manipulation requires special handling since they end with the null character `'\0'`.

### Basic String Operations in C

1. **Length of a String:**
   You can find the length of a string using the `strlen()` function from the `<string.h>` library or manually by iterating through each character until the null character is encountered.

2. **Copying a String:**
   You can use the `strcpy()` function or manually copy each character.

3. **Concatenating Strings:**
   The `strcat()` function can be used to concatenate strings.

4. **Comparing Strings:**
   The `strcmp()` function is used to compare two strings lexicographically.

5. **Reverse a String:**
   Reversing a string can be done manually by swapping characters from both ends until you reach the middle.

---

### Example Code for Various String Operations

#### 1. **Find the Length of a String**

```c
#include <stdio.h>
#include <string.h>  // For strlen()

int main() {
    char str[] = "Hello, World!";
    
    int length = strlen(str);  // Using strlen to find the length of the string
    printf("Length of the string: %d\n", length);
    
    return 0;
}
```

**Output:**
```
Length of the string: 13
```

---

#### 2. **Copy One String to Another**

```c
#include <stdio.h>
#include <string.h>  // For strcpy()

int main() {
    char str1[] = "Hello";
    char str2[50];

    // Copying str1 to str2
    strcpy(str2, str1);

    printf("String 1: %s\n", str1);
    printf("String 2: %s\n", str2);

    return 0;
}
```

**Output:**
```
String 1: Hello
String 2: Hello
```

---

#### 3. **Concatenate Two Strings**

```c
#include <stdio.h>
#include <string.h>  // For strcat()

int main() {
    char str1[50] = "Hello";
    char str2[] = " World!";

    // Concatenate str2 to str1
    strcat(str1, str2);

    printf("Concatenated String: %s\n", str1);
    
    return 0;
}
```

**Output:**
```
Concatenated String: Hello World!
```

---

#### 4. **Compare Two Strings**

```c
#include <stdio.h>
#include <string.h>  // For strcmp()

int main() {
    char str1[] = "Hello";
    char str2[] = "Hello";
    char str3[] = "World";

    // Comparing two strings
    int result1 = strcmp(str1, str2);  // Should return 0 as they are equal
    int result2 = strcmp(str1, str3);  // Should return a negative value since "Hello" < "World"

    printf("Comparing str1 and str2: %d\n", result1);
    printf("Comparing str1 and str3: %d\n", result2);

    return 0;
}
```

**Output:**
```
Comparing str1 and str2: 0
Comparing str1 and str3: -1
```

- The `strcmp()` function returns `0` if the strings are equal, a negative value if the first string is less than the second, and a positive value if the first string is greater than the second.

---

#### 5. **Reverse a String**

```c
#include <stdio.h>
#include <string.h>  // For strlen()

void reverseString(char str[]) {
    int length = strlen(str);
    int start = 0;
    int end = length - 1;

    while (start < end) {
        // Swap characters at start and end positions
        char temp = str[start];
        str[start] = str[end];
        str[end] = temp;

        // Move start forward and end backward
        start++;
        end--;
    }
}

int main() {
    char str[] = "Hello, World!";
    
    reverseString(str);  // Reversing the string
    
    printf("Reversed string: %s\n", str);
    
    return 0;
}
```

**Output:**
```
Reversed string: !dlroW ,olleH
```

---

#### 6. **Count Occurrences of a Character in a String**

```c
#include <stdio.h>

int countOccurrences(char str[], char ch) {
    int count = 0;

    for (int i = 0; str[i] != '\0'; i++) {
        if (str[i] == ch) {
            count++;
        }
    }
    
    return count;
}

int main() {
    char str[] = "hello, world!";
    char ch = 'o';

    int count = countOccurrences(str, ch);
    printf("The character '%c' appears %d times in the string.\n", ch, count);

    return 0;
}
```

**Output:**
```
The character 'o' appears 2 times in the string.
```

---

#### 7. **Convert a String to Uppercase**

```c
#include <stdio.h>
#include <ctype.h>  // For toupper()

void toUppercase(char str[]) {
    for (int i = 0; str[i] != '\0'; i++) {
        str[i] = toupper(str[i]);  // Convert each character to uppercase
    }
}

int main() {
    char str[] = "Hello, World!";
    
    toUppercase(str);  // Convert string to uppercase
    
    printf("Uppercase string: %s\n", str);
    
    return 0;
}
```

**Output:**
```
Uppercase string: HELLO, WORLD!
```

---

### String Handling Functions:

1. **`strlen(str)`**: Returns the length of a string (excluding the null character `\0`).
2. **`strcpy(destination, source)`**: Copies the string from `source` to `destination`.
3. **`strcat(destination, source)`**: Concatenates the `source` string to the end of the `destination` string.
4. **`strcmp(str1, str2)`**: Compares two strings lexicographically.
5. **`strrev(str)`**: Reverses a string (note: `strrev()` is not part of the C standard library, but some compilers like Turbo C provide it).
6. **`toupper(c)`**: Converts a character to uppercase.
7. **`tolower(c)`**: Converts a character to lowercase.


