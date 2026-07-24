# C++ Programs (User-Defined Functions)

A collection of simple C++ programs using user-defined functions.

---

## 1. Armstrong Number

Checks whether a given number is an Armstrong number using a user-defined function.

```cpp
#include <iostream>
using namespace std;

bool isArmstrong(int num) {
    int temp = num, sum = 0;
    while (temp != 0) {
        int digit = temp % 10;
        sum = sum + digit * digit * digit;
        temp = temp / 10;
    }
    if (sum == num) {
        return true;
    }
    return false;
}

int main() {
    int number;
    cout << "Enter a number: ";
    cin >> number;

    if (isArmstrong(number)) {
        cout << number << " is an Armstrong number." << endl;
    } else {
        cout << number << " is not an Armstrong number." << endl;
    }

    return 0;
}
```

**Output:**
```
Enter a number: 153
153 is an Armstrong number.
```

```
Enter a number: 123
123 is not an Armstrong number.
```

---

## 2. Length of a String

Finds the length of a string using a user-defined function.

```cpp
#include <iostream>
using namespace std;

int stringLength(string str) {
    int count = 0;
    for (int i = 0; str[i] != '\0'; i++) {
        count++;
    }
    return count;
}

int main() {
    string str;
    cout << "Enter a string: ";
    cin >> str;

    cout << "Length of the string is: " << stringLength(str) << endl;

    return 0;
}
```

**Output:**
```
Enter a string: hello
Length of the string is: 5
```

---

## 3. Length of a Number

Finds the number of digits in a number using a user-defined function.

```cpp
#include <iostream>
using namespace std;

int numberLength(int num) {
    int count = 0;
    while (num != 0) {
        count++;
        num = num / 10;
    }
    return count;
}

int main() {
    int number;
    cout << "Enter a number: ";
    cin >> number;

    cout << "Length of the number is: " << numberLength(number) << endl;

    return 0;
}
```

**Output:**
```
Enter a number: 12345
Length of the number is: 5
```

---


## 4. Simple Calculator (Using Switch Case)

A simple calculator that performs +, -, *, /, and % based on the operator entered.

```cpp
#include <iostream>
using namespace std;

int main() {
    int a, b;
    char op;
    cin >> a >> op >> b;

    switch (op) {
        case '+':
            cout << a + b;
            break;
        case '-':
            cout << a - b;
            break;
        case '*':
            cout << a * b;
            break;
        case '/':
            if (b != 0) {
                cout << a / b;
            } else {
                cout << "infinity";
            }
            break;
        case '%':
            cout << a % b;
            break;
        default:
            cout << "Invalid input";
    }

    return 0;
}
```

**Output:**
```
10 + 5
15
```

```
10 / 0
infinity
```

---

## 5. Print Character Array in Border Pattern

Prints a character array such that letters appear only on the first row, last row, and the diagonal (border-style pattern), with spaces elsewhere.

```cpp
#include <iostream>
using namespace std;

int main() {
    char arr[] = {'Z', 'O', 'H', 'O'};
    int n = sizeof(arr) / sizeof(arr[0]);

    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            if (i == 0 || i == n - 1 || i + j == n - 1) {
                cout << arr[j] << " ";
            } else {
                cout << "  ";
            }
        }
        cout << endl;
    }

    return 0;
}
```

**Output:**
```
Z O H O
    H
  O
Z O H O
```
