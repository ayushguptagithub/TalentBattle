
### 1. **Calculate Area of Shapes**

#### Rectangle
```c
#include <stdio.h>

int main() {
    int length, breadth, area;
    printf("Enter length and breadth of the rectangle: ");
    scanf("%d %d", &length, &breadth);
    area = length * breadth;
    printf("Area of Rectangle: %d\n", area);
    return 0;
}
```

#### Circle
```c
#include <stdio.h>

int main() {
    float radius, area, pi = 3.14159;
    printf("Enter radius of the circle: ");
    scanf("%f", &radius);
    area = pi * radius * radius;
    printf("Area of Circle: %.2f\n", area);
    return 0;
}
```

#### Triangle
```c
#include <stdio.h>

int main() {
    float base, height, area;
    printf("Enter base and height of the triangle: ");
    scanf("%f %f", &base, &height);
    area = 0.5 * base * height;
    printf("Area of Triangle: %.2f\n", area);
    return 0;
}
```

#### Square
```c
#include <stdio.h>

int main() {
    int side, area;
    printf("Enter side length of the square: ");
    scanf("%d", &side);
    area = side * side;
    printf("Area of Square: %d\n", area);
    return 0;
}
```

---

### 2. **Calculate Square and Square Root**
```c
#include <stdio.h>
#include <math.h>

int main() {
    int num, square;
    float squareRoot;
    printf("Enter a number: ");
    scanf("%d", &num);
    square = num * num;
    squareRoot = sqrt((float)num);
    printf("Square: %d\n", square);
    printf("Square Root: %.2f\n", squareRoot);
    return 0;
}
```

---

### 3. **Swap Two Numbers**

#### Using Temporary Variable
```c
#include <stdio.h>

int main() {
    int a, b, temp;
    printf("Enter two numbers: ");
    scanf("%d %d", &a, &b);
    temp = a;
    a = b;
    b = temp;
    printf("After Swapping: a = %d, b = %d\n", a, b);
    return 0;
}
```

#### Without Temporary Variable
```c
#include <stdio.h>

int main() {
    int a, b;
    printf("Enter two numbers: ");
    scanf("%d %d", &a, &b);
    a = a + b;
    b = a - b;
    a = a - b;
    printf("After Swapping: a = %d, b = %d\n", a, b);
    return 0;
}
```

---

### 4. **Print Numbers 1 to N**
```c
#include <stdio.h>

int main() {
    int N;
    printf("Enter N: ");
    scanf("%d", &N);
    for (int i = 1; i <= N; i++) {
        printf("%d ", i);
    }
    printf("\n");
    return 0;
}
```

---

### 5. **Check if a Number is Prime**
```c
#include <stdio.h>

int main() {
    int num, isPrime = 0;
    printf("Enter a number: ");
    scanf("%d", &num);
    
    for (int i = 1; i <= num; i++) {
        if (num % i == 0) {
            isPrime++;
        }
    }
    if (isPrime==2)
        printf("Prime\n");
    else
        printf("Not Prime\n");
    return 0;
}
```

---

### 6. **Fibonacci Series up to N Terms**
```c
#include <stdio.h>

int main() {
    int N, t1 = 0, t2 = 1, nextTerm;
    printf("Enter N: ");
    scanf("%d", &N);
    printf("Fibonacci Series: ");
    for (int i = 1; i <= N; i++) {
        printf("%d ", t1);
        nextTerm = t1 + t2;
        t1 = t2;
        t2 = nextTerm;
    }
    printf("\n");
    return 0;
}
```

---

### 7. **Factorial of a Number**
```c
#include <stdio.h>

int main() {
    int num, factorial = 1;
    printf("Enter a number: ");
    scanf("%d", &num);
    for (int i = 1; i <= num; i++) {
        factorial *= i;
    }
    printf("Factorial: %d\n", factorial);
    return 0;
}
```

---

### 8. **Find the Largest of Three Numbers**
```c
#include <stdio.h>

int main() {
    int a, b, c;
    printf("Enter three numbers: ");
    scanf("%d %d %d", &a, &b, &c);
    if (a > b && a > c)
        printf("Largest: %d\n", a);
    else if (b > c)
        printf("Largest: %d\n", b);
    else
        printf("Largest: %d\n", c);
    return 0;
}
```

---

### 9. **Check Even or Odd Using Switch-Case**
```c
#include <stdio.h>

int main() {
    int num;
    printf("Enter a number: ");
    scanf("%d", &num);
    switch (num % 2) {
        case 0:
            printf("Even\n");
            break;
        default:
            printf("Odd\n");
    }
    return 0;
}
```

---

### 10. **Sum of Digits**
```c
#include <stdio.h>

int main() {
    int num, sum = 0;
    printf("Enter a number: ");
    scanf("%d", &num);
    while (num != 0) {
        sum += num % 10;
        num /= 10;
    }
    printf("Sum of Digits: %d\n", sum);
    return 0;
}
```

---

### 11. **Reverse a Number**
```c
#include <stdio.h>

int main() {
    int num, reversed = 0;
    printf("Enter a number: ");
    scanf("%d", &num);
    while (num != 0) {
        reversed = reversed * 10 + num % 10;
        num /= 10;
    }
    printf("Reversed Number: %d\n", reversed);
    return 0;
}
```


Here’s a simplified version of the program using basic logic to calculate Armstrong numbers:

---

###  Armstrong Number 
```c
#include <stdio.h>

int main() {
    int num, originalNum, remainder, result = 0, n = 0, i;

    printf("Enter a number: ");
    scanf("%d", &num);

    // Copy the original number to calculate the digit count
    originalNum = num;

    // Count the number of digits
    while (originalNum > 0) {
        n++;
        originalNum /= 10;
    }

    // Reset original number for the second pass
    originalNum = num;

    // Calculate the sum of powers of digits
    while (originalNum > 0) {
        int power = 1; // Initialize power
        remainder = originalNum % 10;

        // Multiply the digit 'n' times
        for (i = 0; i < n; i++) {
            power *= remainder;
        }

        result += power;
        originalNum /= 10;
    }

    // Check if the number is Armstrong
    if (result == num)
        printf("%d is an Armstrong number.\n", num);
    else
        printf("%d is not an Armstrong number.\n", num);

    return 0;
}
```


### Leap Year Check Program in C
```c
#include <stdio.h>

int main() {
    int year;

    printf("Enter a year: ");
    scanf("%d", &year);

    // Check if the year is a leap year
    if ((year % 4 == 0 && year % 100 != 0) || (year % 400 == 0)) {
        printf("%d is a Leap Year.\n", year);
    } else {
        printf("%d is not a Leap Year.\n", year);
    }

    return 0;
}
```

### Program to Print the Table of a Number Entered By User
```c
#include <stdio.h>

int main() {
    int num;

    printf("Enter a number: ");
    scanf("%d", &num);

    for (int i = 1; i <= 10; i++) {
        printf("%d x %d = %d\n", num, i, num * i);
    }

    return 0;
}
```


### 1. **Right-Angled Triangle Pattern**

**Pattern:**
```
*
* *
* * *
* * * *
* * * * *
```

**Code:**
```c
#include <stdio.h>

int main() {
    int n;

    printf("Enter the number of rows: ");
    scanf("%d", &n);

    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= i; j++) {
            printf("* ");
        }
        printf("\n");
    }

    return 0;
}
```

---

### 2. **Inverted Right-Angled Triangle Pattern**

**Pattern:**
```
* * * * *
* * * *
* * *
* *
*
```

**Code:**
```c
#include <stdio.h>

int main() {
    int n;

    printf("Enter the number of rows: ");
    scanf("%d", &n);

    for (int i = n; i >= 1; i--) {
        for (int j = 1; j <= i; j++) {
            printf("* ");
        }
        printf("\n");
    }

    return 0;
}
```

---
### 3. **Space Pattern**

**Pattern:**
```
     *
    **
   ***
  ****
 *****
```

**Code:**
```c    

#include <stdio.h>

int main()
{
     for (int i = 5; i >= 1; i--) {
        // Print stars
        for (int j = 1; j <= i; j++) {
            printf(" ");
        }

       
        for (int k = 1; k <= (6 - i); k++) { 
            printf("*");
        }
        
        printf("\n");
    }
    
    
    return 0;
}
```

---

### 3. **Pyramid Pattern**

**Pattern:**
```
    *
   * *
  * * *
 * * * *
* * * * *
```

**Code:**
```c

#include <stdio.h>

int main()
{
     for (int i = 5; i >= 1; i--) {
        // Print stars
        for (int j = 1; j <= i; j++) {
            printf(" ");
        }

       
        for (int k = 1; k <= (6 - i); k++) { 
            printf("* ");
        }
        
        printf("\n");
    }
    
    
    return 0;
}
```

---

### 4. **Number Triangle Pattern**

**Pattern:**
```
1
1 2
1 2 3
1 2 3 4
1 2 3 4 5
```

**Code:**
```c
#include <stdio.h>

int main() {
    int n;

    printf("Enter the number of rows: ");
    scanf("%d", &n);

    for (int i = 1; i <= n; i++) {
        for (int j = 1; j <= i; j++) {
            printf("%d ", j);
        }
        printf("\n");
    }

    return 0;
}
```
