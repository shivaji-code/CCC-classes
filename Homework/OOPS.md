# C++ Student Class Example

## C++ Code

```cpp
#include <iostream>
using namespace std;

class Student {
public:
    void Re() {
        cout << "Students primary task is Reading" << endl;
    }
    
    void pl() {
        cout << "Students used to play for relaxation" << endl;
    }
    
    void No() {
        cout << "Students used to make noice while no teacher in the class room" << endl;
    }
    
    void di() {
        cout << "Students have more distractions than an adult" << endl;
    }
};

int main() {
    Student std;
    
    std.Re();
    std.pl();
    std.No();
    std.di();
    
    return 0;
}
```

## Output

```text
Students primary task is Reading
Students used to play for relaxation
Students used to make noice while no teacher in the class room.
Students have more distractions than an adult.
```
