

### **51. Calculate Sum of Natural Numbers using Recursion**
```cpp
#include <iostream>
using namespace std;

int sumOfNaturalNumbers(int n) {
    if (n == 0) return 0; // Base case
    return n + sumOfNaturalNumbers(n - 1); // Recursive case
}

int main() {
    int n;
    cout << "Enter a positive number: ";
    cin >> n;
    cout << "Sum of first " << n << " natural numbers: " << sumOfNaturalNumbers(n) << endl;
    return 0;
}
```

---

### **52. Calculate Factorial Using Recursion**
```cpp
#include <iostream>
using namespace std;

int factorial(int n) {
    if (n == 0 || n == 1) return 1; // Base case
    return n * factorial(n - 1); // Recursive case
}

int main() {
    int n;
    cout << "Enter a number: ";
    cin >> n;
    cout << "Factorial of " << n << ": " << factorial(n) << endl;
    return 0;
}
```

---

### **53. Calculate H.C.F using Recursion**
```cpp
#include <iostream>
using namespace std;

int hcf(int a, int b) {
    if (b == 0) return a; // Base case
    return hcf(b, a % b); // Recursive case
}

int main() {
    int num1, num2;
    cout << "Enter two numbers: ";
    cin >> num1 >> num2;
    cout << "H.C.F of " << num1 << " and " << num2 << " is: " << hcf(num1, num2) << endl;
    return 0;
}
```

---

### **54. Convert Binary Number to Decimal**
```cpp
#include <iostream>
#include <cmath>
using namespace std;

int binaryToDecimal(int binary) {
    int decimal = 0, base = 1, lastDigit;
    while (binary > 0) {
        lastDigit = binary % 10;
        decimal += lastDigit * base;
        binary /= 10;
        base *= 2;
    }
    return decimal;
}

int main() {
    int binary;
    cout << "Enter a binary number: ";
    cin >> binary;
    cout << "Decimal equivalent: " << binaryToDecimal(binary) << endl;
    return 0;
}
```

---

### **55. Convert Octal Number to Decimal**
```cpp
#include <iostream>
#include <cmath>
using namespace std;

int octalToDecimal(int octal) {
    int decimal = 0, base = 1, lastDigit;
    while (octal > 0) {
        lastDigit = octal % 10;
        decimal += lastDigit * base;
        octal /= 10;
        base *= 8;
    }
    return decimal;
}

int main() {
    int octal;
    cout << "Enter an octal number: ";
    cin >> octal;
    cout << "Decimal equivalent: " << octalToDecimal(octal) << endl;
    return 0;
}
```


### **56. Convert Decimal Number to Octal**
```cpp
#include <iostream>
using namespace std;

void decimalToOctal(int decimal) {
    int octal[50], i = 0;
    while (decimal != 0) {
        octal[i++] = decimal % 8;
        decimal /= 8;
    }
    cout << "Octal equivalent: ";
    for (int j = i - 1; j >= 0; j--) {
        cout << octal[j];
    }
    cout << endl;
}

int main() {
    int decimal;
    cout << "Enter a decimal number: ";
    cin >> decimal;
    decimalToOctal(decimal);
    return 0;
}
```

---

### **57. Program to Convert Binary to Octal**
```cpp
#include <iostream>
#include <cmath>
using namespace std;

// Convert binary to decimal
int binaryToDecimal(int binary) {
    int decimal = 0, base = 1, lastDigit;
    while (binary > 0) {
        lastDigit = binary % 10;
        decimal += lastDigit * base;
        binary /= 10;
        base *= 2;
    }
    return decimal;
}

// Convert decimal to octal
void decimalToOctal(int decimal) {
    int octal[50], i = 0;
    while (decimal != 0) {
        octal[i++] = decimal % 8;
        decimal /= 8;
    }
    cout << "Octal equivalent: ";
    for (int j = i - 1; j >= 0; j--) {
        cout << octal[j];
    }
    cout << endl;
}

int main() {
    int binary;
    cout << "Enter a binary number: ";
    cin >> binary;
    int decimal = binaryToDecimal(binary);
    decimalToOctal(decimal);
    return 0;
}
```

---

### **58. Program to Convert Octal to Binary**
```cpp
#include <iostream>
using namespace std;

// Convert octal to decimal
int octalToDecimal(int octal) {
    int decimal = 0, base = 1, lastDigit;
    while (octal > 0) {
        lastDigit = octal % 10;
        decimal += lastDigit * base;
        octal /= 10;
        base *= 8;
    }
    return decimal;
}

// Convert decimal to binary
void decimalToBinary(int decimal) {
    int binary[50], i = 0;
    while (decimal != 0) {
        binary[i++] = decimal % 2;
        decimal /= 2;
    }
    cout << "Binary equivalent: ";
    for (int j = i - 1; j >= 0; j--) {
        cout << binary[j];
    }
    cout << endl;
}

int main() {
    int octal;
    cout << "Enter an octal number: ";
    cin >> octal;
    int decimal = octalToDecimal(octal);
    decimalToBinary(decimal);
    return 0;
}
```

---

### **59. Reverse a Sentence Using Recursion**
```cpp
#include <iostream>
#include <string>
using namespace std;

void reverseSentence(string str) {
    if (str.length() == 0) return; // Base case
    cout << str.back();            // Print the last character
    reverseSentence(str.substr(0, str.length() - 1)); // Recursive call
}

int main() {
    string sentence;
    cout << "Enter a sentence: ";
    getline(cin, sentence);
    cout << "Reversed sentence: ";
    reverseSentence(sentence);
    cout << endl;
    return 0;
}
```

---

### **60. Program to Compute Power Using Recursion**
```cpp
#include <iostream>
using namespace std;

int power(int base, int exp) {
    if (exp == 0) return 1; // Base case
    return base * power(base, exp - 1); // Recursive case
}

int main() {
    int base, exp;
    cout << "Enter base and exponent: ";
    cin >> base >> exp;
    cout << base << " raised to the power " << exp << " is: " << power(base, exp) << endl;
    return 0;
}
```


### **61. Calculate Average of Numbers Using Arrays**
```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter the number of elements: ";
    cin >> n;
    double arr[n], sum = 0;

    cout << "Enter " << n << " numbers: ";
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
        sum += arr[i];
    }

    cout << "Average: " << sum / n << endl;
    return 0;
}
```

---

### **62. Display Largest Element of an Array**
```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter the number of elements: ";
    cin >> n;
    int arr[n];

    cout << "Enter " << n << " numbers: ";
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }

    int max = arr[0];
    for (int i = 1; i < n; i++) {
        if (arr[i] > max) max = arr[i];
    }

    cout << "Largest element: " << max << endl;
    return 0;
}
```

---

### **63. Calculate Standard Deviation**
```cpp
#include <iostream>
#include <cmath>
using namespace std;

int main() {
    int n;
    cout << "Enter the number of elements: ";
    cin >> n;
    double arr[n], sum = 0, mean, variance = 0;

    cout << "Enter " << n << " numbers: ";
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
        sum += arr[i];
    }

    mean = sum / n;
    for (int i = 0; i < n; i++) {
        variance += pow(arr[i] - mean, 2);
    }

    variance /= n;
    cout << "Standard Deviation: " << sqrt(variance) << endl;
    return 0;
}
```

---

### **64. Add Two Matrices Using Multidimensional Arrays**
```cpp
#include <iostream>
using namespace std;

int main() {
    int rows, cols;
    cout << "Enter rows and columns: ";
    cin >> rows >> cols;

    int a[rows][cols], b[rows][cols], sum[rows][cols];
    cout << "Enter elements of first matrix:\n";
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            cin >> a[i][j];
        }
    }

    cout << "Enter elements of second matrix:\n";
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            cin >> b[i][j];
        }
    }

    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            sum[i][j] = a[i][j] + b[i][j];
        }
    }

    cout << "Sum of matrices:\n";
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            cout << sum[i][j] << " ";
        }
        cout << endl;
    }

    return 0;
}
```

---

### **65. Multiply Two Matrices Without Using Functions**
```cpp
#include <iostream>
using namespace std;

int main() {
    int r1, c1, r2, c2;
    cout << "Enter rows and columns of first matrix: ";
    cin >> r1 >> c1;
    cout << "Enter rows and columns of second matrix: ";
    cin >> r2 >> c2;

    if (c1 != r2) {
        cout << "Matrix multiplication not possible.\n";
        return 0;
    }

    int a[r1][c1], b[r2][c2], product[r1][c2] = {0};

    cout << "Enter elements of first matrix:\n";
    for (int i = 0; i < r1; i++) {
        for (int j = 0; j < c1; j++) {
            cin >> a[i][j];
        }
    }

    cout << "Enter elements of second matrix:\n";
    for (int i = 0; i < r2; i++) {
        for (int j = 0; j < c2; j++) {
            cin >> b[i][j];
        }
    }

    for (int i = 0; i < r1; i++) {
        for (int j = 0; j < c2; j++) {
            for (int k = 0; k < c1; k++) {
                product[i][j] += a[i][k] * b[k][j];
            }
        }
    }

    cout << "Product of matrices:\n";
    for (int i = 0; i < r1; i++) {
        for (int j = 0; j < c2; j++) {
            cout << product[i][j] << " ";
        }
        cout << endl;
    }

    return 0;
}
```


Here are the solutions for **66 to 75**:

---

### **66. Find Transpose of a Matrix**
```cpp
#include <iostream>
using namespace std;

int main() {
    int rows, cols;
    cout << "Enter rows and columns: ";
    cin >> rows >> cols;

    int matrix[rows][cols], transpose[cols][rows];
    cout << "Enter elements of the matrix:\n";
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            cin >> matrix[i][j];
        }
    }

    // Transpose
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            transpose[j][i] = matrix[i][j];
        }
    }

    cout << "Transpose of the matrix:\n";
    for (int i = 0; i < cols; i++) {
        for (int j = 0; j < rows; j++) {
            cout << transpose[i][j] << " ";
        }
        cout << endl;
    }

    return 0;
}
```

---

### **67. Access Array Elements Using Pointers**
```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cout << "Enter the number of elements: ";
    cin >> n;
    int arr[n];

    cout << "Enter " << n << " numbers: ";
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }

    cout << "Accessing elements using pointers:\n";
    for (int i = 0; i < n; i++) {
        cout << *(arr + i) << " ";
    }
    cout << endl;

    return 0;
}
```

---

### **68. Program to Swap Elements Using Call by Reference**
```cpp
#include <iostream>
using namespace std;

void swap(int &x, int &y) {
    int temp = x;
    x = y;
    y = temp;
}

int main() {
    int a, b;
    cout << "Enter two numbers: ";
    cin >> a >> b;

    cout << "Before swapping: a = " << a << ", b = " << b << endl;
    swap(a, b);
    cout << "After swapping: a = " << a << ", b = " << b << endl;

    return 0;
}
```

---

### **69. Find Frequency of Characters of a String Object**
```cpp
#include <iostream>
#include <map>
using namespace std;

int main() {
    string str;
    cout << "Enter a string: ";
    cin >> str;

    map<char, int> frequency;
    for (char c : str) {
        frequency[c]++;
    }

    cout << "Frequency of characters:\n";
    for (auto &pair : frequency) {
        cout << pair.first << ": " << pair.second << endl;
    }

    return 0;
}
```

---

### **70. Remove All Characters Except Alphabets**
```cpp
#include <iostream>
#include <cctype>
using namespace std;

int main() {
    string str, result = "";
    cout << "Enter a string: ";
    cin >> str;

    for (char c : str) {
        if (isalpha(c)) {
            result += c;
        }
    }

    cout << "String after removing non-alphabets: " << result << endl;
    return 0;
}
```

---

### **71. Concatenate String Objects**
```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string str1, str2;
    cout << "Enter first string: ";
    cin >> str1;
    cout << "Enter second string: ";
    cin >> str2;

    string result = str1 + str2;
    cout << "Concatenated string: " << result << endl;
    return 0;
}
```

---

### **72. Copy String Object**
```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string str1, str2;
    cout << "Enter a string: ";
    cin >> str1;

    str2 = str1;
    cout << "Copied string: " << str2 << endl;
    return 0;
}
```

---

### **73. Sort Words in Dictionary Order**
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    int n;
    cout << "Enter the number of words: ";
    cin >> n;
    vector<string> words(n);

    cout << "Enter the words:\n";
    for (int i = 0; i < n; i++) {
        cin >> words[i];
    }

    sort(words.begin(), words.end());

    cout << "Words in dictionary order:\n";
    for (string word : words) {
        cout << word << endl;
    }

    return 0;
}
```

---

### **74. Add Two Complex Numbers**
```cpp
#include <iostream>
using namespace std;

struct Complex {
    float real;
    float imag;
};

Complex add(Complex a, Complex b) {
    Complex result;
    result.real = a.real + b.real;
    result.imag = a.imag + b.imag;
    return result;
}

int main() {
    Complex c1, c2, sum;
    cout << "Enter real and imaginary part of first complex number: ";
    cin >> c1.real >> c1.imag;

    cout << "Enter real and imaginary part of second complex number: ";
    cin >> c2.real >> c2.imag;

    sum = add(c1, c2);

    cout << "Sum: " << sum.real << " + " << sum.imag << "i\n";
    return 0;
}
```

---

### **75. Store Information in Structure and Display It**
```cpp
#include <iostream>
using namespace std;

struct Student {
    string name;
    int age;
    float marks;
};

int main() {
    Student student;

    cout << "Enter student's name: ";
    cin >> student.name;
    cout << "Enter student's age: ";
    cin >> student.age;
    cout << "Enter student's marks: ";
    cin >> student.marks;

    cout << "\nStudent Information:\n";
    cout << "Name: " << student.name << endl;
    cout << "Age: " << student.age << endl;
    cout << "Marks: " << student.marks << endl;

    return 0;
}
```

---

All 75 programs are now complete, Congratulations!😊