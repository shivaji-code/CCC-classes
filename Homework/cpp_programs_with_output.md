# C++ Practice Programs (with sample I/O)


---

### 17 July 2026
**Q: Rectangle rope length & carpet area**
```cpp
#include <iostream>
using namespace std;

int main() {
    int length, breadth;

    cin >> length >> breadth;

    int ropeLength = 2 * (length + breadth);
    int carpetArea = length * breadth;

    cout << "The required length is " << ropeLength << " m" << endl;
    cout << "The required area of carpet is " << carpetArea << " sqm";

    return 0;
}
```
**Sample Input:**
```
5 3
```
**Sample Output:**
```
The required length is 16 m
The required area of carpet is 15 sqm
```

---

### 17 July 2026
**Q: Book printing profit calculation**
```cpp
#include <iostream>
using namespace std;

int main() {
    int copies, sellingPrice, productionCost;

    cin >> copies >> sellingPrice >> productionCost;

    int profit = (copies * sellingPrice) - (copies * productionCost) - 100;

    cout << profit;

    return 0;
}
```
**Sample Input:**
```
1000 50 30
```
**Sample Output:**
```
19900
```

---

### 17 July 2026
**Q: Sum of first & last digit (4-digit number)**
```cpp
#include <iostream>
using namespace std;

int main() {
    int num;
    cin >> num;

    int firstDigit = num / 1000;
    int lastDigit = num % 10;

    cout << firstDigit + lastDigit;

    return 0;
}
```
**Sample Input:**
```
4285
```
**Sample Output:**
```
9
```

---

### 18 July 2026
**Q: Check leap year**
```cpp
#include <iostream>
using namespace std;

int main() {
    int year;
    cin >> year;

    if ((year % 400 == 0) || (year % 4 == 0 && year % 100 != 0))
        cout << year << " is a leap year.";
    else
        cout << year << " is not a leap year.";

    return 0;
}
```
**Sample Input:**
```
2024
```
**Sample Output:**
```
2024 is a leap year.
```

---

### 18 July 2026
**Q: Check vowel / consonant / not an alphabet**
```cpp
#include <iostream>
using namespace std;

int main() {
    char ch;
    cin >> ch;

    if ((ch >= 'A' && ch <= 'Z') || (ch >= 'a' && ch <= 'z')) {
        if (ch == 'A' || ch == 'E' || ch == 'I' || ch == 'O' || ch == 'U' ||
            ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u') {
            cout << "Vowel";
        } else {
            cout << "Consonant";
        }
    } else {
        cout << "Not an alphabet";
    }

    return 0;
}
```
**Sample Input:**
```
A
```
**Sample Output:**
```
Vowel
```

---

### 18 July 2026
**Q: Find cheapest shopping site (Flipkart/Snapdeal/Amazon)**
```cpp
#include <iostream>

using namespace std;

int main() {
    double fp, fd, fs;
    double sp, sd, ss;
    double ap, ad, as;
    
    // Read input data
    cin >> fp >> fd >> fs;
    cin >> sp >> sd >> ss;
    cin >> ap >> ad >> as;
    
    // Calculate final prices
    double flipkart = fp - (fp * fd / 100.0) + fs;
    double snapdeal = sp - (sp * sd / 100.0) + ss;
    double amazon = ap - (ap * ad / 100.0) + as;
    
    // Print ONLY the numbers (as required by the system)
    cout << flipkart << endl;
    cout << snapdeal << endl;
    cout << amazon << endl;
    
    // Print ONLY the website name
    if (flipkart <= snapdeal && flipkart <= amazon) {
        cout << "Flipkart" << endl;
    }
    else if (snapdeal <= flipkart && snapdeal <= amazon) {
        cout << "Snapdeal" << endl;
    }
    else {
        cout << "Amazon" << endl;
    }
    
    return 0;
}
```
**Sample Input:**
```
1000 10 50
2000 20 40
1500 15 60
```
**Sample Output:**
```
950
1640
1335
Flipkart
```

---

### 20 July 2026
**Q: Check scholarship eligibility**
```cpp
#include <iostream>
using namespace std;

int main() {
    int age, year, income, arrears;
    float score, attendance;

    cin >> age;
    cin >> year;
    cin >> income;
    cin >> arrears;
    cin >> score;
    cin >> attendance;

    // Basic eligibility
    if (year < 2021 || age < 18 || age >= 21 || income >= 250000) {
        cout << "Not Eligible";
        return 0;
    }

    // Students with 2 or fewer arrears
    if (arrears <= 2) {
        if (score >= 60 && attendance >= 80) {
            if (income <= 200000)
                cout << "Eligible";
            else
                cout << "Partially Eligible";
        } else {
            cout << "Not Eligible";
        }
    }
    // Students with more than 2 arrears
    else {
        if (score >= 80 && attendance >= 90) {
            if (income <= 200000)
                cout << "Eligible";
            else
                cout << "Partially Eligible";
        } else {
            cout << "Not Eligible";
        }
    }

    return 0;
}
```
**Sample Input:**
```
19 2022 180000 1 75 85
```
**Sample Output:**
```
Eligible
```

---

### 20 July 2026
**Q: Find number of days in a month**
```cpp
#include <iostream>
using namespace std;

int main() {
    int year, month;
    cin >> year;
    cin >> month;

    if (year < 1900 || year > 9999) {
        cout << 0;
        return 0;
    }

    switch (month) {
        case 1: case 3: case 5: case 7:
        case 8: case 10: case 12:
            cout << "31 Days";
            break;

        case 4: case 6: case 9: case 11:
            cout << "30 Days";
            break;

        case 2:
            if ((year % 400 == 0) || (year % 4 == 0 && year % 100 != 0))
                cout << "29 Days";
            else
                cout << "28 Days";
            break;

        default:
            cout << 0;
    }

    return 0;
}
```
**Sample Input:**
```
2024 2
```
**Sample Output:**
```
29 Days
```

---

### 20 July 2026
**Q: Room rent with peak-season surcharge**
```cpp
#include <iostream>
#include <iomanip>
using namespace std;

int main() {
    int month, rent, days;
    cin >> month >> rent >> days;

    if (month < 1 || month > 12) {
        cout << "Invalid Input";
    } else {
        double total;

        if ((month >= 4 && month <= 6) || (month >= 11 && month <= 12))
            total = rent * days * 1.20;
        else
            total = rent * days;

        cout << fixed << setprecision(2) << total;
    }

    return 0;
}
```
**Sample Input:**
```
5 1000 10
```
**Sample Output:**
```
12000.00
```

---

### 21 July 2026
**Q: Reverse digits of a number**
```cpp
#include<iostream>
using namespace std;
int main(){
    int n, rem = 0, sum = 0;
    cin >> n;
    while(n > 0){
        rem = n % 10;
        sum = (sum * 10) + rem;
        n = n / 10;
    }
    cout << sum;
}
```
**Sample Input:**
```
12345
```
**Sample Output:**
```
54321
```

---

### 21 July 2026
**Q: Print evens then odds in a range**
```cpp
#include<iostream>
using namespace std;
int main(){
    int a,b;
    cin >> a >> b;
    for(int i = a; i <= b; i++){
        if(i % 2 == 0){
            cout << i << " ";
        }
    }
    cout << endl;
    for(int i = a; i <= b; i++){
        if(i % 2 != 0){
            cout << i << " ";
        }
    }
}
```
**Sample Input:**
```
1 10
```
**Sample Output:**
```
2 4 6 8 10 
1 3 5 7 9 
```

---

### 21 July 2026
**Q: 2-digit numbers where digit-sum + digit-product = number**
```cpp
#include <iostream>

using namespace std;

int main() {
    int m, n;
    if (!(cin >> m >> n)) return 0;

    for (int i = m; i <= n; i++) {
        if (i >= 10 && i <= 99) {
            int d1 = i / 10;
            int d2 = i % 10;
            if ((d1 + d2) + (d1 * d2) == i
            ) {
                cout << i << endl;
            }
        }
    }

    return 0;
}
```
**Sample Input:**
```
10 99
```
**Sample Output:**
```
19
29
39
49
59
69
79
89
99
```

---

### 22 July 2026
**Q: Find nth Fibonacci number**
```cpp
#include <iostream>
using namespace std;

int main()
{
    int n;
    cin >> n;

    int a = 0, b = 1, c;

    if (n == 1)
        cout << 0;
    else if (n == 2)
        cout << 1;
    else
    {
        for (int i = 3; i <= n; i++)
        {
            c = a + b;
            a = b;
            b = c;
        }
        cout << b;
    }

    return 0;
}
```
**Sample Input:**
```
10
```
**Sample Output:**
```
34
```

---

### 22 July 2026
**Q: Print hollow square star pattern**
```cpp
#include <iostream>
using namespace std;

int main()
{
    int n;
    cin >> n;

    for (int i = 1; i <= n; i++)
    {
        for (int j = 1; j <= n; j++)
        {
            if (i == 1 || i == n || j == 1 || j == n)
                cout << "*";
            else
                cout << " ";
        }
        cout << endl;
    }

    return 0;
}
```
**Sample Input:**
```
5
```
**Sample Output:**
```
*****
*   *
*   *
*   *
*****
```

---

### 22 July 2026
**Q: Check if a number is a palindrome**
```cpp
#include <iostream>
using namespace std;

int main()
{
    int n, rev = 0, rem, temp;

    cin >> n;
    temp = n;

    while (n > 0)
    {
        rem = n % 10;
        rev = rev * 10 + rem;
        n = n / 10;
    }

    if (temp == rev)
        cout << "Palindrome";
    else
        cout << "Not Palindrome";

    return 0;
}
```
**Sample Input:**
```
121
```
**Sample Output:**
```
Palindrome
```

---

### 23 July 2026
**Q: Simulate the Collatz sequence**
```cpp
#include <iostream>
using namespace std;

int main()
{
    int n, count = 0;
    cin >> n;

    while (n != 1)
    {
        cout << n << endl;

        if (n % 2 == 0)
            n = n / 2;
        else
            n = 3 * n + 1;

        count++;
    }

    cout << 1 << endl;
    cout << count;

    return 0;
}
```
**Sample Input:**
```
6
```
**Sample Output:**
```
6
3
10
5
16
8
4
2
1
8
```

---

### 23 July 2026
**Q: Find digital root of a number**
```cpp
#include <iostream>
using namespace std;

int main()
{
    int n, sum;

    cin >> n;

    while (n >= 10)
    {
        sum = 0;
        while (n > 0)
        {
            sum = sum + (n % 10);
            n = n / 10;
        }
        n = sum;
    }

    cout << n;

    return 0;
}
```
**Sample Input:**
```
9875
```
**Sample Output:**
```
2
```

---

### 23 July 2026
**Q: Print inverted right-angled triangle pattern**
```cpp
#include <iostream>
using namespace std;

int main()
{
    int n;
    cin >> n;

    for (int i = n; i >= 1; i--)
    {
        for (int j = 1; j <= i; j++)
        {
            cout << "*";
        }
        cout << endl;
    }

    return 0;
}
```
**Sample Input:**
```
5
```
**Sample Output:**
```
*****
****
***
**
*
```

---

### 24 July 2026
**Q: Check if two arrays are compatible**
```cpp
#include <iostream>
using namespace std;

int main() {
    int n1, n2;
    cin >> n1;

    int a[100];
    for (int i = 0; i < n1; i++)
        cin >> a[i];

    cin >> n2;

    int b[100];
    for (int i = 0; i < n2; i++)
        cin >> b[i];

    if (n1 != n2) {
        cout << "Incompatible";
        return 0;
    }

    for (int i = 0; i < n1; i++) {
        if (a[i] < b[i]) {
            cout << "Incompatible";
            return 0;
        }
    }

    cout << "Compatible";
    return 0;
}
```
**Sample Input:**
```
3
5 6 7
3
4 5 6
```
**Sample Output:**
```
Compatible
```

---

### 24 July 2026
**Q: Count distinct elements in an array**
```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;

    int a[100];
    for (int i = 0; i < n; i++)
        cin >> a[i];

    int count = 0;

    for (int i = 0; i < n; i++) {
        bool found = false;

        for (int j = 0; j < i; j++) {
            if (a[i] == a[j]) {
                found = true;
                break;
            }
        }

        if (!found)
            count++;
    }

    cout << "There are " << count << " distinct element in the array.";

    return 0;
}
```
**Sample Input:**
```
6
1 2 2 3 4 4
```
**Sample Output:**
```
There are 4 distinct element in the array.
```

---

### 24 July 2026
**Q: Check if two arrays are the same (size + sum)**
```cpp
#include <iostream>
using namespace std;

int main() {
    int n1, n2;
    cin >> n1 >> n2;

    int a[100], b[100];
    int sum1 = 0, sum2 = 0;

    for (int i = 0; i < n1; i++) {
        cin >> a[i];
        sum1 += a[i];
    }

    for (int i = 0; i < n2; i++) {
        cin >> b[i];
        sum2 += b[i];
    }

    if (n1 == n2 && sum1 == sum2)
        cout << "Same";
    else
        cout << "Not Same";

    return 0;
}
```
**Sample Input:**
```
3 3
1 2 3
3 2 1
```
**Sample Output:**
```
Same
```

---

### 27 July 2026
**Q: Insert an element at a given position in an array**
```cpp
#include <iostream>
using namespace std;

int main() {
    int n, a[100], pos, element;

    cin >> n;

    for (int i = 0; i < n; i++) {
        cin >> a[i];
    }

    cin >> pos;
    cin >> element;

    if (pos < 1 || pos > n + 1) {
        cout << "Invalid Input";
        return 0;
    }

    for (int i = n; i >= pos; i--) {
        a[i] = a[i - 1];
    }

    a[pos - 1] = element;

    cout << "Array after insertion is" << endl;

    for (int i = 0; i <= n; i++) {
        cout << a[i] << endl;
    }

    return 0;
}
```
**Sample Input:**
```
5
1 2 3 4 5
3
99
```
**Sample Output:**
```
Array after insertion is
1
2
99
3
4
5
```

---

### 27 July 2026
**Q: Sort an array using bubble sort**
```cpp
#include <iostream>
using namespace std;

int main() {
    int n, a[100];

    cin >> n;

    for (int i = 0; i < n; i++) {
        cin >> a[i];
    }

    // Bubble Sort
    for (int i = 0; i < n - 1; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            if (a[j] > a[j + 1]) {
                int temp = a[j];
                a[j] = a[j + 1];
                a[j + 1] = temp;
            }
        }
    }

    cout << "The Sorted array is:" << endl;

    for (int i = 0; i < n; i++) {
        cout << a[i] << endl;
    }

    return 0;
}
```
**Sample Input:**
```
5
5 3 8 1 2
```
**Sample Output:**
```
The Sorted array is:
1
2
3
5
8
```

---

### 27 July 2026
**Q: Sum of even & odd elements in an array**
```cpp
#include <iostream>
using namespace std;

int main() {
    int n, a[15];
    int evensum = 0, oddsum = 0;

    cin >> n;

    for (int i = 0; i < n; i++) {
        cin >> a[i];

        if (a[i] % 2 == 0)
            evensum += a[i];
        else
            oddsum += a[i];
    }

    cout << "The sum of the even numbers in the array is " << evensum << endl;
    cout << "The sum of the odd numbers in the array is " << oddsum << endl;

    return 0;
}
```
**Sample Input:**
```
5
1 2 3 4 5
```
**Sample Output:**
```
The sum of the even numbers in the array is 6
The sum of the odd numbers in the array is 9
```

---

### 28 July 2026
**Q: Check if a matrix is upper triangular**
```cpp
#include <iostream>
using namespace std;

int main()
{
    int n;
    cin >> n;

    int a[100][100];

    // Input matrix
    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < n; j++)
        {
            cin >> a[i][j];
        }
    }

    bool upper = true;

    // Check elements below diagonal
    for (int i = 1; i < n; i++)
    {
        for (int j = 0; j < i; j++)
        {
            if (a[i][j] != 0)
            {
                upper = false;
            }
        }
    }

    if (upper)
        cout << "Upper triangular matrix";
    else
        cout << "Not an Upper triangular matrix";

    return 0;
}
```
**Sample Input:**
```
3
1 2 3
0 4 5
0 0 6
```
**Sample Output:**
```
Upper triangular matrix
```

---

### 28 July 2026
**Q: Find row/column with maximum sum in a matrix**
```cpp
#include <iostream>
using namespace std;

int main()
{
    int r, c;
    cin >> r >> c;

    int a[100][100];

    // Input matrix
    for (int i = 0; i < r; i++)
    {
        for (int j = 0; j < c; j++)
        {
            cin >> a[i][j];
        }
    }

    // Row sums
    cout << "The Sum of rows is ";
    int maxRow = 0, maxRowSum = -1;

    for (int i = 0; i < r; i++)
    {
        int sum = 0;
        for (int j = 0; j < c; j++)
        {
            sum += a[i][j];
        }

        cout << sum << " ";

        if (sum > maxRowSum)
        {
            maxRowSum = sum;
            maxRow = i;
        }
    }

    cout << endl;
    cout << "Row " << maxRow + 1 << " has a maximum sum" << endl;

    // Column sums
    cout << "The Sum of columns is ";
    int maxCol = 0, maxColSum = -1;

    for (int j = 0; j < c; j++)
    {
        int sum = 0;
        for (int i = 0; i < r; i++)
        {
            sum += a[i][j];
        }

        cout << sum << " ";

        if (sum > maxColSum)
        {
            maxColSum = sum;
            maxCol = j;
        }
    }

    cout << endl;
    cout << "Column " << maxCol + 1 << " has the maximum sum";

    return 0;
}
```
**Sample Input:**
```
2 3
1 2 3
4 5 6
```
**Sample Output:**
```
The Sum of rows is 6 15 
Row 2 has a maximum sum
The Sum of columns is 5 7 9 
Column 3 has the maximum sum
```

---

### 28 July 2026
**Q: Print transpose of a square matrix**
```cpp
#include <iostream>
using namespace std;

int main()
{
    int n;
    cin >> n;

    int a[100][100];

    // Input matrix
    for(int i = 0; i < n; i++)
    {
        for(int j = 0; j < n; j++)
        {
            cin >> a[i][j];
        }
    }

    cout << "Transpose matrix is:" << endl;

    // Print transpose
    for(int i = 0; i < n; i++)
    {
        for(int j = 0; j < n; j++)
        {
            cout << a[j][i] << " ";
        }
        cout << endl;
    }

    return 0;
}
```
**Sample Input:**
```
3
1 2 3
4 5 6
7 8 9
```
**Sample Output:**
```
Transpose matrix is:
1 4 7 
2 5 8 
3 6 9 
```

---

### 29 July 2026
**Q: Find first non-repeating character in a string**
```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string str;
    getline(cin, str);

    int freq[256] = {0};

    // Count frequency of each character
    for (char ch : str) {
        freq[(unsigned char)ch]++;
    }

    // Find first non-repeating character
    for (char ch : str) {
        if (freq[(unsigned char)ch] == 1) {
            cout << ch;
            return 0;
        }
    }

    cout << "All characters are repetitive.";

    return 0;
}
```
**Sample Input:**
```
swiss
```
**Sample Output:**
```
w
```

---

### 29 July 2026
**Q: Count vowels in a string**
```cpp
#include <iostream>
#include <string>
using namespace std;

int main() {
    string str;
    getline(cin, str);

    int count = 0;

    for (int i = 0; i < str.length(); i++) {
        char ch = tolower(str[i]);

        if (ch == 'a' || ch == 'e' || ch == 'i' || ch == 'o' || ch == 'u') {
            count++;
        }
    }

    cout << "Number of vowels: " << count;

    return 0;
}
```
**Sample Input:**
```
Hello World
```
**Sample Output:**
```
Number of vowels: 3
```

---

### 29 July 2026
**Q: Reverse the words in a sentence**
```cpp
#include <iostream>
#include <sstream>
#include <vector>
using namespace std;

int main() {
    string str, word;
    getline(cin, str);

    stringstream ss(str);
    vector<string> words;

    while (ss >> word) {
        words.push_back(word);
    }

    for (int i = words.size() - 1; i >= 0; i--) {
        cout << words[i];
        if (i != 0)
            cout << " ";
    }

    return 0;
}
```
**Sample Input:**
```
The quick brown fox
```
**Sample Output:**
```
fox brown quick The
```

---

### 30 July 2026
**Q: Print frequency of each distinct array element**
```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;

    int a[100];

    for (int i = 0; i < n; i++) {
        cin >> a[i];
    }

    for (int i = 0; i < n; i++) {
        bool visited = false;

        // Check if already counted
        for (int j = 0; j < i; j++) {
            if (a[i] == a[j]) {
                visited = true;
                break;
            }
        }

        if (!visited) {
            int count = 1;

            // Count occurrences
            for (int j = i + 1; j < n; j++) {
                if (a[i] == a[j]) {
                    count++;
                }
            }

            cout << a[i] << " " << count << endl;
        }
    }

    return 0;
}
```
**Sample Input:**
```
6
1 2 2 3 3 3
```
**Sample Output:**
```
1 1
2 2
3 3
```

---

### 30 July 2026
**Q: Segregate even numbers before odd numbers in array**
```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;

    int a[100];

    for (int i = 0; i < n; i++) {
        cin >> a[i];
    }

    cout << "Array after Segregation" << endl;

    // Print even numbers first
    for (int i = 0; i < n; i++) {
        if (a[i] % 2 == 0)
            cout << a[i] << " ";
    }

    // Print odd numbers next
    for (int i = 0; i < n; i++) {
        if (a[i] % 2 != 0)
            cout << a[i] << " ";
    }

    return 0;
}
```
**Sample Input:**
```
6
1 2 3 4 5 6
```
**Sample Output:**
```
Array after Segregation
2 4 6 1 3 5 
```

---

### 30 July 2026
**Q: Remove duplicates from an array**
```cpp
#include <iostream>
using namespace std;

int main() {
    int n;
    cin >> n;

    int a[100];

    for (int i = 0; i < n; i++) {
        cin >> a[i];
    }

    for (int i = 0; i < n; i++) {
        bool duplicate = false;

        for (int j = 0; j < i; j++) {
            if (a[i] == a[j]) {
                duplicate = true;
                break;
            }
        }

        if (!duplicate) {
            cout << a[i] << " ";
        }
    }

    return 0;
}
```
**Sample Input:**
```
6
1 2 2 3 3 4
```
**Sample Output:**
```
1 2 3 4 
```