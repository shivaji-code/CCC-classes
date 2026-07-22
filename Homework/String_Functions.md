# C++ String Functions

This document explains some commonly used **C++ string functions** with simple definitions, syntax, example programs, and outputs.

> **Note:** All programs use:
> ```cpp
> #include <bits/stdc++.h>
> using namespace std;
> ```
> `#include <bits/stdc++.h>` is a GCC header file that includes almost all standard C++ library headers.

---

# 1. swap()

## Definition
The `swap()` function exchanges the contents of two strings.

## Syntax
```cpp
string1.swap(string2);
```

## Example
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    string s1 = "Apple";
    string s2 = "Mango";

    cout << "Before Swap:" << endl;
    cout << "s1 = " << s1 << endl;
    cout << "s2 = " << s2 << endl;

    s1.swap(s2);

    cout << "\nAfter Swap:" << endl;
    cout << "s1 = " << s1 << endl;
    cout << "s2 = " << s2 << endl;

    return 0;
}
```

## Output
```
Before Swap:
s1 = Apple
s2 = Mango

After Swap:
s1 = Mango
s2 = Apple
```

---

# 2. find()

## Definition
The `find()` function searches for the **first occurrence** of a character or word in a string.

## Syntax
```cpp
string.find("text");
```

## Example
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    string s = "Hello World";

    cout << s.find("World");

    return 0;
}
```

## Output
```
6
```

## Explanation
The word `"World"` starts at index **6**.

---

# 3. rfind()

## Definition
The `rfind()` function searches for the **last occurrence** of a character or word in a string.

## Syntax
```cpp
string.rfind("text");
```

## Example
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    string s = "Apple Mango Apple";

    cout << s.rfind("Apple");

    return 0;
}
```

## Output
```
12
```

## Explanation
The last `"Apple"` starts at index **12**.

---

# 4. resize()

## Definition
The `resize()` function changes the size (length) of a string.

- If the new size is smaller, extra characters are removed.
- If the new size is larger, new characters are added.

## Syntax
```cpp
string.resize(size);
```

## Example
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    string s = "Programming";

    s.resize(7);

    cout << s;

    return 0;
}
```

## Output
```
Program
```

## Explanation
Only the first **7** characters remain.

---

# 5. empty()

## Definition
The `empty()` function checks whether a string is empty or not.

- Returns `true` if the string is empty.
- Returns `false` if the string is not empty.

## Syntax
```cpp
string.empty();
```

## Example
```cpp
#include <bits/stdc++.h>
using namespace std;

int main() {
    string s = "";

    if (s.empty()) {
        cout << "String is empty";
    }
    else {
        cout << "String is not empty";
    }

    return 0;
}
```

## Output
```
String is empty
```

---

# Quick Revision Table

| Function | Purpose | Syntax Example |
|----------|---------|----------------|
| `swap()` | Swaps two strings | `s1.swap(s2);` |
| `find()` | Finds the first occurrence | `s.find("abc");` |
| `rfind()` | Finds the last occurrence | `s.rfind("abc");` |
| `resize()` | Changes the string length | `s.resize(5);` |
| `empty()` | Checks whether the string is empty | `s.empty();` |

---

# Summary

- `swap()` → Exchanges two strings.
- `find()` → Finds the first occurrence of a character or word.
- `rfind()` → Finds the last occurrence of a character or word.
- `resize()` → Changes the length of the string.
- `empty()` → Checks whether the string is empty.

---

**Author:** Shivaji Alagari  
**Repository:** CCC-classes
