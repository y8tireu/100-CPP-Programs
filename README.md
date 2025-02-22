# 100 C++ Programs

---

## Program 1: Hello World
```cpp
#include <iostream>
int main() {
    std::cout << "Hello, World!" << std::endl;
    return 0;
}
```

---

## Program 2: Sum of Two Numbers
```cpp
#include <iostream>
int main() {
    int a = 5, b = 7;
    std::cout << "Sum: " << (a + b) << std::endl;
    return 0;
}
```

---

## Program 3: Factorial (Recursive)
```cpp
#include <iostream>
int factorial(int n) {
    return (n == 0) ? 1 : n * factorial(n - 1);
}
int main() {
    int num = 5;
    std::cout << "Factorial of " << num << " is " << factorial(num) << std::endl;
    return 0;
}
```

---

## Program 4: Fibonacci Series
```cpp
#include <iostream>
void fibonacci(int n) {
    int a = 0, b = 1;
    for (int i = 0; i < n; ++i) {
        std::cout << a << " ";
        int temp = a + b;
        a = b;
        b = temp;
    }
}
int main() {
    fibonacci(10);
    std::cout << std::endl;
    return 0;
}
```

---

## Program 5: Prime Number Checker
```cpp
#include <iostream>
#include <cmath>
bool isPrime(int n) {
    if(n < 2) return false;
    for (int i = 2; i <= std::sqrt(n); ++i)
        if(n % i == 0)
            return false;
    return true;
}
int main() {
    int num = 29;
    std::cout << num << " is prime? " << (isPrime(num) ? "Yes" : "No") << std::endl;
    return 0;
}
```

---

## Program 6: Reverse a String
```cpp
#include <iostream>
#include <string>
#include <algorithm>
int main() {
    std::string s = "C++ Programming";
    std::reverse(s.begin(), s.end());
    std::cout << "Reversed: " << s << std::endl;
    return 0;
}
```

---

## Program 7: Palindrome Checker
```cpp
#include <iostream>
#include <string>
#include <algorithm>
bool isPalindrome(const std::string &s) {
    std::string rev = s;
    std::reverse(rev.begin(), rev.end());
    return s == rev;
}
int main() {
    std::string word = "radar";
    std::cout << word << " is palindrome? " << (isPalindrome(word) ? "Yes" : "No") << std::endl;
    return 0;
}
```

---

## Program 8: Find Largest in an Array
```cpp
#include <iostream>
#include <algorithm>
int main() {
    int arr[] = {3, 67, 2, 89, 34};
    int n = sizeof(arr) / sizeof(arr[0]);
    int maxVal = *std::max_element(arr, arr + n);
    std::cout << "Largest number: " << maxVal << std::endl;
    return 0;
}
```

---

## Program 9: Find Smallest in an Array
```cpp
#include <iostream>
#include <algorithm>
int main() {
    int arr[] = {3, 67, 2, 89, 34};
    int n = sizeof(arr) / sizeof(arr[0]);
    int minVal = *std::min_element(arr, arr + n);
    std::cout << "Smallest number: " << minVal << std::endl;
    return 0;
}
```

---

## Program 10: Even or Odd
```cpp
#include <iostream>
int main() {
    int num = 42;
    std::cout << num << " is " << ((num % 2 == 0) ? "Even" : "Odd") << std::endl;
    return 0;
}
```

---

## Program 11: Vector Squaring Using Transform
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
int main() {
    std::vector<int> nums = {0, 1, 2, 3, 4};
    std::vector<int> squares(nums.size());
    std::transform(nums.begin(), nums.end(), squares.begin(), [](int x){ return x * x; });
    std::cout << "Squares: ";
    for (auto s : squares) std::cout << s << " ";
    std::cout << std::endl;
    return 0;
}
```

---

## Program 12: Bubble Sort
```cpp
#include <iostream>
#include <vector>
void bubbleSort(std::vector<int> &arr) {
    for (size_t i = 0; i < arr.size(); ++i)
        for (size_t j = 0; j < arr.size()-i-1; ++j)
            if(arr[j] > arr[j+1])
                std::swap(arr[j], arr[j+1]);
}
int main() {
    std::vector<int> arr = {64, 34, 25, 12, 22, 11, 90};
    bubbleSort(arr);
    std::cout << "Sorted: ";
    for(auto v : arr) std::cout << v << " ";
    std::cout << std::endl;
    return 0;
}
```

---

## Program 13: Merge Sort
```cpp
#include <iostream>
#include <vector>
void merge(std::vector<int>& arr, int l, int m, int r) {
    int n1 = m - l + 1, n2 = r - m;
    std::vector<int> L(arr.begin() + l, arr.begin() + m + 1);
    std::vector<int> R(arr.begin() + m + 1, arr.begin() + r + 1);
    int i = 0, j = 0, k = l;
    while(i < n1 && j < n2)
        arr[k++] = (L[i] <= R[j]) ? L[i++] : R[j++];
    while(i < n1)
        arr[k++] = L[i++];
    while(j < n2)
        arr[k++] = R[j++];
}
void mergeSort(std::vector<int>& arr, int l, int r) {
    if(l < r) {
        int m = l + (r - l) / 2;
        mergeSort(arr, l, m);
        mergeSort(arr, m+1, r);
        merge(arr, l, m, r);
    }
}
int main() {
    std::vector<int> arr = {38, 27, 43, 3, 9, 82, 10};
    mergeSort(arr, 0, arr.size()-1);
    std::cout << "Merge Sorted: ";
    for (auto v : arr) std::cout << v << " ";
    std::cout << std::endl;
    return 0;
}
```

---

## Program 14: Binary Search
```cpp
#include <iostream>
#include <vector>
int binarySearch(const std::vector<int>& arr, int target) {
    int low = 0, high = arr.size() - 1;
    while(low <= high) {
        int mid = low + (high - low) / 2;
        if(arr[mid] == target)
            return mid;
        else if(arr[mid] < target)
            low = mid + 1;
        else
            high = mid - 1;
    }
    return -1;
}
int main() {
    std::vector<int> arr = {1, 3, 5, 7, 9, 11};
    std::cout << "Index of 7: " << binarySearch(arr, 7) << std::endl;
    return 0;
}
```

---

## Program 15: Tower of Hanoi
```cpp
#include <iostream>
void towerOfHanoi(int n, char source, char auxiliary, char target) {
    if(n == 1) {
        std::cout << "Move disk 1 from " << source << " to " << target << std::endl;
        return;
    }
    towerOfHanoi(n - 1, source, target, auxiliary);
    std::cout << "Move disk " << n << " from " << source << " to " << target << std::endl;
    towerOfHanoi(n - 1, auxiliary, source, target);
}
int main() {
    towerOfHanoi(3, 'A', 'B', 'C');
    return 0;
}
```

---

## Program 16: Sum of Digits
```cpp
#include <iostream>
#include <string>
int main() {
    int num = 12345;
    int sum = 0;
    std::string s = std::to_string(num);
    for(char c : s)
        sum += c - '0';
    std::cout << "Sum of digits: " << sum << std::endl;
    return 0;
}
```

---

## Program 17: Count Vowels in a String
```cpp
#include <iostream>
#include <string>
#include <cctype>
int main() {
    std::string s = "Hello World";
    int count = 0;
    for(char c : s) {
        c = std::tolower(c);
        if(c=='a' || c=='e' || c=='i' || c=='o' || c=='u')
            ++count;
    }
    std::cout << "Vowels count: " << count << std::endl;
    return 0;
}
```

---

## Program 18: Generate a Random Number
```cpp
#include <iostream>
#include <cstdlib>
#include <ctime>
int main() {
    std::srand(static_cast<unsigned int>(std::time(0)));
    int num = std::rand() % 100 + 1;
    std::cout << "Random number (1-100): " << num << std::endl;
    return 0;
}
```

---

## Program 19: Calculate GCD
```cpp
#include <iostream>
#include <numeric>
int main() {
    int a = 48, b = 180;
    int gcd = std::gcd(a, b);
    std::cout << "GCD: " << gcd << std::endl;
    return 0;
}
```

---

## Program 20: Calculate LCM
```cpp
#include <iostream>
#include <numeric>
int main() {
    int a = 12, b = 15;
    int lcm = (a * b) / std::gcd(a, b);
    std::cout << "LCM: " << lcm << std::endl;
    return 0;
}
```

---

## Program 21: Armstrong Number Checker
```cpp
#include <iostream>
#include <cmath>
#include <string>
int main() {
    int num = 153;
    std::string s = std::to_string(num);
    int power = s.size(), sum = 0;
    for(char c : s)
        sum += std::pow(c - '0', power);
    std::cout << num << " is Armstrong? " << (sum == num ? "Yes" : "No") << std::endl;
    return 0;
}
```

---

## Program 22: Perfect Number Checker
```cpp
#include <iostream>
int main() {
    int num = 28, sum = 0;
    for (int i = 1; i < num; ++i)
        if(num % i == 0)
            sum += i;
    std::cout << num << " is perfect? " << (sum == num ? "Yes" : "No") << std::endl;
    return 0;
}
```

---

## Program 23: Simple Calculator
```cpp
#include <iostream>
int main() {
    double a, b;
    char op;
    std::cout << "Enter expression (e.g., 10 + 5): ";
    std::cin >> a >> op >> b;
    switch(op) {
        case '+': std::cout << a + b; break;
        case '-': std::cout << a - b; break;
        case '*': std::cout << a * b; break;
        case '/': 
            if(b != 0)
                std::cout << a / b;
            else
                std::cout << "Division by zero error";
            break;
        default: std::cout << "Invalid operator";
    }
    std::cout << std::endl;
    return 0;
}
```

---

## Program 24: Celsius to Fahrenheit Converter
```cpp
#include <iostream>
double cToF(double celsius) {
    return (celsius * 9.0/5.0) + 32;
}
int main() {
    double c = 25;
    std::cout << c << "°C = " << cToF(c) << "°F" << std::endl;
    return 0;
}
```

---

## Program 25: Simple Currency Converter (USD to EUR)
```cpp
#include <iostream>
double usdToEur(double usd, double rate = 0.85) {
    return usd * rate;
}
int main() {
    std::cout << "$100 = " << usdToEur(100) << " EUR" << std::endl;
    return 0;
}
```

---

## Program 26: Factorization (List Factors)
```cpp
#include <iostream>
#include <vector>
int main() {
    int num = 28;
    std::vector<int> factors;
    for(int i = 1; i <= num; ++i)
        if(num % i == 0)
            factors.push_back(i);
    std::cout << "Factors of " << num << ": ";
    for(auto f : factors)
        std::cout << f << " ";
    std::cout << std::endl;
    return 0;
}
```

---

## Program 27: Leap Year Checker
```cpp
#include <iostream>
bool isLeapYear(int year) {
    return (year % 4 == 0 && year % 100 != 0) || (year % 400 == 0);
}
int main() {
    int year = 2024;
    std::cout << year << " is leap year? " << (isLeapYear(year) ? "Yes" : "No") << std::endl;
    return 0;
}
```

---

## Program 28: Area of a Circle
```cpp
#include <iostream>
#include <cmath>
int main() {
    double radius = 5;
    double area = M_PI * radius * radius;
    std::cout << "Area of circle with radius " << radius << " is " << area << std::endl;
    return 0;
}
```

---

## Program 29: Area of a Triangle (Heron’s Formula)
```cpp
#include <iostream>
#include <cmath>
int main() {
    double a = 3, b = 4, c = 5;
    double s = (a + b + c) / 2;
    double area = std::sqrt(s * (s - a) * (s - b) * (s - c));
    std::cout << "Area of triangle: " << area << std::endl;
    return 0;
}
```

---

## Program 30: Even or Odd Using Lambda
```cpp
#include <iostream>
#include <functional>
int main() {
    auto evenOrOdd = [](int x) { return (x % 2 == 0) ? "Even" : "Odd"; };
    std::cout << "17 is " << evenOrOdd(17) << std::endl;
    return 0;
}
```

---

## Program 31: Square Numbers in a Vector Using Transform
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
int main() {
    std::vector<int> nums = {1,2,3,4,5};
    std::vector<int> squares(nums.size());
    std::transform(nums.begin(), nums.end(), squares.begin(), [](int x){ return x*x; });
    std::cout << "Squares: ";
    for(auto s : squares) std::cout << s << " ";
    std::cout << std::endl;
    return 0;
}
```

---

## Program 32: Filter Even Numbers Using Copy_if
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
int main() {
    std::vector<int> nums = {1,2,3,4,5,6};
    std::vector<int> evens;
    std::copy_if(nums.begin(), nums.end(), std::back_inserter(evens), [](int x){ return x % 2 == 0; });
    std::cout << "Even numbers: ";
    for(auto e : evens) std::cout << e << " ";
    std::cout << std::endl;
    return 0;
}
```

---

## Program 33: Multiply Elements Using Accumulate
```cpp
#include <iostream>
#include <vector>
#include <numeric>
int main() {
    std::vector<int> nums = {1,2,3,4};
    int product = std::accumulate(nums.begin(), nums.end(), 1, std::multiplies<int>());
    std::cout << "Product: " << product << std::endl;
    return 0;
}
```

---

## Program 34: Create Map from Two Arrays
```cpp
#include <iostream>
#include <map>
#include <vector>
int main() {
    std::vector<char> keys = {'a', 'b', 'c'};
    std::vector<int> values = {1, 2, 3};
    std::map<char, int> m;
    for(size_t i = 0; i < keys.size(); ++i)
        m[keys[i]] = values[i];
    std::cout << "Map contents:" << std::endl;
    for(auto &p : m)
        std::cout << p.first << " : " << p.second << std::endl;
    return 0;
}
```

---

## Program 35: Sort Vector of Pairs by Second Value
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
int main() {
    std::vector<std::pair<std::string, int>> vec = {{"apple", 3}, {"banana", 1}, {"cherry", 2}};
    std::sort(vec.begin(), vec.end(), [](auto &a, auto &b) {
        return a.second < b.second;
    });
    std::cout << "Sorted by value:" << std::endl;
    for(auto &p : vec)
        std::cout << p.first << " : " << p.second << std::endl;
    return 0;
}
```

---

## Program 36: Count Words in a File
```cpp
#include <iostream>
#include <fstream>
#include <sstream>
#include <string>
int main() {
    std::ifstream file("example.txt");
    if(!file) {
        std::cerr << "File not found!" << std::endl;
        return 1;
    }
    std::stringstream buffer;
    buffer << file.rdbuf();
    std::string content = buffer.str();
    std::istringstream iss(content);
    std::string word;
    int count = 0;
    while(iss >> word)
        ++count;
    std::cout << "Word count: " << count << std::endl;
    return 0;
}
```

---

## Program 37: Read File and Display Content
```cpp
#include <iostream>
#include <fstream>
#include <string>
int main() {
    std::ifstream file("example.txt");
    if(!file) {
        std::cerr << "Unable to open file!" << std::endl;
        return 1;
    }
    std::string line;
    while(std::getline(file, line))
        std::cout << line << std::endl;
    return 0;
}
```

---

## Program 38: Write to a File
```cpp
#include <iostream>
#include <fstream>
int main() {
    std::ofstream file("output.txt");
    if(file)
        file << "Hello, file!" << std::endl;
    else
        std::cerr << "Error writing to file" << std::endl;
    return 0;
}
```

---

## Program 39: Append to a File
```cpp
#include <iostream>
#include <fstream>
int main() {
    std::ofstream file("output.txt", std::ios::app);
    if(file)
        file << "Appending new line" << std::endl;
    else
        std::cerr << "Error appending to file" << std::endl;
    return 0;
}
```

---

## Program 40: Delete a File
```cpp
#include <iostream>
#include <cstdio>
int main() {
    const char* filename = "output.txt";
    if(std::remove(filename) == 0)
        std::cout << filename << " deleted" << std::endl;
    else
        std::cerr << "File deletion failed" << std::endl;
    return 0;
}
```

---

## Program 41: Create a Directory (C++17)
```cpp
#include <iostream>
#include <filesystem>
namespace fs = std::filesystem;
int main() {
    fs::path dir("new_folder");
    if(!fs::exists(dir)) {
        fs::create_directory(dir);
        std::cout << "Directory created" << std::endl;
    } else {
        std::cout << "Directory already exists" << std::endl;
    }
    return 0;
}
```

---

## Program 42: List Files in a Directory (C++17)
```cpp
#include <iostream>
#include <filesystem>
namespace fs = std::filesystem;
int main() {
    for(const auto & entry : fs::directory_iterator("."))
        std::cout << entry.path() << std::endl;
    return 0;
}
```

---

## Program 43: Rename a File
```cpp
#include <iostream>
#include <filesystem>
namespace fs = std::filesystem;
int main() {
    fs::path oldName = "old.txt";
    fs::path newName = "new.txt";
    if(fs::exists(oldName)) {
        fs::rename(oldName, newName);
        std::cout << "File renamed" << std::endl;
    } else {
        std::cout << "File not found" << std::endl;
    }
    return 0;
}
```

---

## Program 44: Exception Handling Example
```cpp
#include <iostream>
int main() {
    try {
        int result = 10 / 0;
        std::cout << result << std::endl;
    } catch(...) {
        std::cerr << "Division by zero error" << std::endl;
    }
    return 0;
}
```

---

## Program 45: Custom Exception
```cpp
#include <iostream>
#include <exception>
class MyError : public std::exception {
public:
    const char* what() const noexcept override {
        return "Negative value error!";
    }
};
int checkValue(int x) {
    if(x < 0) throw MyError();
    return x;
}
int main() {
    try {
        std::cout << checkValue(-5) << std::endl;
    } catch(const MyError &e) {
        std::cerr << "Error: " << e.what() << std::endl;
    }
    return 0;
}
```

---

## Program 46: Simple Class and Object
```cpp
#include <iostream>
class Person {
public:
    Person(const std::string &name) : name(name) {}
    void greet() const {
        std::cout << "Hello, my name is " << name << std::endl;
    }
private:
    std::string name;
};
int main() {
    Person p("Alice");
    p.greet();
    return 0;
}
```

---

## Program 47: Inheritance Example
```cpp
#include <iostream>
class Animal {
public:
    virtual void speak() const { std::cout << "Animal sound" << std::endl; }
};
class Dog : public Animal {
public:
    void speak() const override { std::cout << "Woof!" << std::endl; }
};
int main() {
    Dog d;
    d.speak();
    return 0;
}
```

---

## Program 48: Polymorphism Example
```cpp
#include <iostream>
class Base {
public:
    virtual void sound() const = 0;
};
class Bird : public Base {
public:
    void sound() const override { std::cout << "Tweet" << std::endl; }
};
class Cat : public Base {
public:
    void sound() const override { std::cout << "Meow" << std::endl; }
};
void makeSound(const Base &animal) {
    animal.sound();
}
int main() {
    Bird b;
    Cat c;
    makeSound(b);
    makeSound(c);
    return 0;
}
```

---

## Program 49: Encapsulation Example
```cpp
#include <iostream>
class BankAccount {
public:
    BankAccount(int balance) : balance(balance) {}
    void deposit(int amount) { balance += amount; }
    int getBalance() const { return balance; }
private:
    int balance;
};
int main() {
    BankAccount account(100);
    account.deposit(50);
    std::cout << "Balance: " << account.getBalance() << std::endl;
    return 0;
}
```

---

## Program 50: Abstraction Using Pure Virtual Functions
```cpp
#include <iostream>
class Shape {
public:
    virtual double area() const = 0;
};
class Square : public Shape {
public:
    Square(double side) : side(side) {}
    double area() const override { return side * side; }
private:
    double side;
};
int main() {
    Square s(4);
    std::cout << "Area of square: " << s.area() << std::endl;
    return 0;
}
```

---

## Program 51: Binary to Decimal Conversion
```cpp
#include <iostream>
#include <string>
#include <cmath>
int main() {
    std::string binary = "1010";
    int decimal = 0;
    for(size_t i = 0; i < binary.size(); ++i)
        decimal = decimal * 2 + (binary[i] - '0');
    std::cout << "Decimal of " << binary << " is " << decimal << std::endl;
    return 0;
}
```

---

## Program 52: Decimal to Binary Conversion
```cpp
#include <iostream>
#include <string>
#include <algorithm>
std::string decimalToBinary(int n) {
    std::string binary;
    if(n == 0) return "0";
    while(n) {
        binary.push_back((n % 2) + '0');
        n /= 2;
    }
    std::reverse(binary.begin(), binary.end());
    return binary;
}
int main() {
    std::cout << "Binary of 10: " << decimalToBinary(10) << std::endl;
    return 0;
}
```

---

## Program 53: Matrix Addition
```cpp
#include <iostream>
#include <vector>
int main() {
    std::vector<std::vector<int>> A = {{1,2}, {3,4}};
    std::vector<std::vector<int>> B = {{5,6}, {7,8}};
    std::vector<std::vector<int>> sum(2, std::vector<int>(2,0));
    for(int i = 0; i < 2; ++i)
        for(int j = 0; j < 2; ++j)
            sum[i][j] = A[i][j] + B[i][j];
    std::cout << "Matrix Sum:" << std::endl;
    for(auto &row : sum) {
        for(auto val : row)
            std::cout << val << " ";
        std::cout << std::endl;
    }
    return 0;
}
```

---

## Program 54: Matrix Multiplication
```cpp
#include <iostream>
#include <vector>
int main() {
    std::vector<std::vector<int>> A = {{1,2}, {3,4}};
    std::vector<std::vector<int>> B = {{2,0}, {1,2}};
    std::vector<std::vector<int>> prod(2, std::vector<int>(2,0));
    for(int i = 0; i < 2; ++i)
        for(int j = 0; j < 2; ++j)
            for(int k = 0; k < 2; ++k)
                prod[i][j] += A[i][k] * B[k][j];
    std::cout << "Matrix Product:" << std::endl;
    for(auto &row : prod) {
        for(auto val : row)
            std::cout << val << " ";
        std::cout << std::endl;
    }
    return 0;
}
```

---

## Program 55: Transpose of a Matrix
```cpp
#include <iostream>
#include <vector>
int main() {
    std::vector<std::vector<int>> matrix = {{1,2,3}, {4,5,6}};
    std::vector<std::vector<int>> transpose(3, std::vector<int>(2,0));
    for(size_t i = 0; i < matrix.size(); ++i)
        for(size_t j = 0; j < matrix[0].size(); ++j)
            transpose[j][i] = matrix[i][j];
    std::cout << "Transpose:" << std::endl;
    for(auto &row : transpose) {
        for(auto val : row)
            std::cout << val << " ";
        std::cout << std::endl;
    }
    return 0;
}
```

---

## Program 56: Check if Matrix is Symmetric
```cpp
#include <iostream>
#include <vector>
bool isSymmetric(const std::vector<std::vector<int>> &matrix) {
    int n = matrix.size();
    for(int i = 0; i < n; ++i)
        for(int j = 0; j < n; ++j)
            if(matrix[i][j] != matrix[j][i])
                return false;
    return true;
}
int main() {
    std::vector<std::vector<int>> matrix = {
        {1, 2, 3},
        {2, 4, 5},
        {3, 5, 6}
    };
    std::cout << "Symmetric? " << (isSymmetric(matrix) ? "Yes" : "No") << std::endl;
    return 0;
}
```

---

## Program 57: Multiplication Table
```cpp
#include <iostream>
int main() {
    int n = 5;
    for(int i = 1; i <= n; ++i) {
        for(int j = 1; j <= n; ++j)
            std::cout << i * j << "\t";
        std::cout << std::endl;
    }
    return 0;
}
```

---

## Program 58: Count Frequency of Elements in a Vector
```cpp
#include <iostream>
#include <vector>
#include <map>
int main() {
    std::vector<int> nums = {1,2,2,3,3,3};
    std::map<int, int> freq;
    for(auto n : nums)
        ++freq[n];
    std::cout << "Frequencies:" << std::endl;
    for(auto &p : freq)
        std::cout << p.first << " : " << p.second << std::endl;
    return 0;
}
```

---

## Program 59: Parse JSON using nlohmann/json  
*(Requires installation of [nlohmann/json](https://github.com/nlohmann/json))*  
```cpp
#include <iostream>
#include <nlohmann/json.hpp>
using json = nlohmann::json;
int main() {
    std::string json_str = R"({"name": "Alice", "age": 30})";
    auto data = json::parse(json_str);
    std::cout << "Name: " << data["name"] << ", Age: " << data["age"] << std::endl;
    return 0;
}
```

---

## Program 60: Regular Expression Example
```cpp
#include <iostream>
#include <regex>
#include <string>
int main() {
    std::string text = "The rain in Spain";
    std::regex re("\\bS\\w+");
    std::smatch match;
    if(std::regex_search(text, match, re))
        std::cout << "Match: " << match.str() << std::endl;
    else
        std::cout << "No match found." << std::endl;
    return 0;
}
```

---

## Program 61: Sorting with Lambda
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
int main() {
    std::vector<int> nums = {5, 2, 9, 1, 5, 6};
    std::sort(nums.begin(), nums.end(), [](int a, int b) { return a < b; });
    std::cout << "Sorted: ";
    for(auto n : nums) std::cout << n << " ";
    std::cout << std::endl;
    return 0;
}
```

---

## Program 62: Create a Thread
```cpp
#include <iostream>
#include <thread>
void printNumbers() {
    for (int i = 0; i < 5; ++i)
        std::cout << i << " ";
}
int main() {
    std::thread t(printNumbers);
    t.join();
    std::cout << std::endl;
    return 0;
}
```

---

## Program 63: Multithreading Example
```cpp
#include <iostream>
#include <thread>
#include <vector>
void worker(int id) {
    std::cout << "Worker " << id << " started." << std::endl;
}
int main() {
    std::vector<std::thread> threads;
    for(int i = 0; i < 3; ++i)
        threads.push_back(std::thread(worker, i));
    for(auto &t : threads)
        t.join();
    return 0;
}
```

---

## Program 64: Mutex Example
```cpp
#include <iostream>
#include <thread>
#include <mutex>
int counter = 0;
std::mutex mtx;
void increment() {
    for(int i = 0; i < 1000; ++i) {
        std::lock_guard<std::mutex> lock(mtx);
        ++counter;
    }
}
int main() {
    std::thread t1(increment), t2(increment);
    t1.join(); t2.join();
    std::cout << "Counter: " << counter << std::endl;
    return 0;
}
```

---

## Program 65: STL Sort Example
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
int main() {
    std::vector<int> nums = {9, 3, 7, 1, 5};
    std::sort(nums.begin(), nums.end());
    std::cout << "Sorted: ";
    for(auto n : nums) std::cout << n << " ";
    std::cout << std::endl;
    return 0;
}
```

---

## Program 66: STL Binary Search
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
int main() {
    std::vector<int> nums = {1, 3, 5, 7, 9, 11};
    bool found = std::binary_search(nums.begin(), nums.end(), 7);
    std::cout << "7 found? " << (found ? "Yes" : "No") << std::endl;
    return 0;
}
```

---

## Program 67: Permutations using next_permutation
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
int main() {
    std::vector<int> nums = {1, 2, 3};
    std::cout << "Permutations:" << std::endl;
    do {
        for(auto n : nums)
            std::cout << n << " ";
        std::cout << std::endl;
    } while(std::next_permutation(nums.begin(), nums.end()));
    return 0;
}
```

---

## Program 68: Quick Sort Implementation
```cpp
#include <iostream>
#include <vector>
int partition(std::vector<int>& arr, int low, int high) {
    int pivot = arr[high], i = low - 1;
    for(int j = low; j < high; ++j)
        if(arr[j] < pivot)
            std::swap(arr[++i], arr[j]);
    std::swap(arr[i+1], arr[high]);
    return i+1;
}
void quickSort(std::vector<int>& arr, int low, int high) {
    if(low < high) {
        int pi = partition(arr, low, high);
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}
int main() {
    std::vector<int> arr = {10, 7, 8, 9, 1, 5};
    quickSort(arr, 0, arr.size() - 1);
    std::cout << "Quick Sorted: ";
    for(auto n : arr)
        std::cout << n << " ";
    std::cout << std::endl;
    return 0;
}
```

---

## Program 69: Merge Sort (Alternate Implementation)
```cpp
#include <iostream>
#include <vector>
void merge(std::vector<int>& arr, int l, int m, int r) {
    int n1 = m - l + 1, n2 = r - m;
    std::vector<int> L(arr.begin() + l, arr.begin() + m + 1);
    std::vector<int> R(arr.begin() + m + 1, arr.begin() + r + 1);
    int i = 0, j = 0, k = l;
    while(i < n1 && j < n2)
        arr[k++] = (L[i] < R[j]) ? L[i++] : R[j++];
    while(i < n1) arr[k++] = L[i++];
    while(j < n2) arr[k++] = R[j++];
}
void mergeSort(std::vector<int>& arr, int l, int r) {
    if(l < r) {
        int m = l + (r - l) / 2;
        mergeSort(arr, l, m);
        mergeSort(arr, m+1, r);
        merge(arr, l, m, r);
    }
}
int main() {
    std::vector<int> arr = {38, 27, 43, 3, 9, 82, 10};
    mergeSort(arr, 0, arr.size()-1);
    std::cout << "Merge Sorted: ";
    for(auto n : arr)
        std::cout << n << " ";
    std::cout << std::endl;
    return 0;
}
```

---

## Program 70: Factorial (Iterative)
```cpp
#include <iostream>
int main() {
    int n = 5;
    int fact = 1;
    for(int i = 1; i <= n; ++i)
        fact *= i;
    std::cout << "Factorial of " << n << " is " << fact << std::endl;
    return 0;
}
```

---

## Program 71: Recursion with std::function
```cpp
#include <iostream>
#include <functional>
int main() {
    std::function<int(int)> fact = [&fact](int n) {
        return (n == 0) ? 1 : n * fact(n - 1);
    };
    std::cout << "Factorial of 5 is " << fact(5) << std::endl;
    return 0;
}
```

---

## Program 72: Using std::bind
```cpp
#include <iostream>
#include <functional>
int add(int a, int b) { return a + b; }
int main() {
    auto add_five = std::bind(add, 5, std::placeholders::_1);
    std::cout << "5 + 10 = " << add_five(10) << std::endl;
    return 0;
}
```

---

## Program 73: Function Pointer Example
```cpp
#include <iostream>
int add(int a, int b) { return a + b; }
int main() {
    int (*funcPtr)(int, int) = add;
    std::cout << "3 + 4 = " << funcPtr(3, 4) << std::endl;
    return 0;
}
```

---

## Program 74: Lambda Function Demo
```cpp
#include <iostream>
int main() {
    auto square = [](int x) { return x * x; };
    std::cout << "Square of 6: " << square(6) << std::endl;
    return 0;
}
```

---

## Program 75: Lambda Capturing Variables
```cpp
#include <iostream>
int main() {
    int factor = 3;
    auto multiply = [factor](int x) { return x * factor; };
    std::cout << "5 * 3 = " << multiply(5) << std::endl;
    return 0;
}
```

---

## Program 76: Using auto Keyword
```cpp
#include <iostream>
#include <vector>
int main() {
    auto nums = std::vector<int>{1,2,3,4,5};
    for(auto n : nums)
        std::cout << n << " ";
    std::cout << std::endl;
    return 0;
}
```

---

## Program 77: Using Enum
```cpp
#include <iostream>
enum Color { RED, GREEN, BLUE };
int main() {
    Color c = GREEN;
    std::cout << "Color value: " << c << std::endl;
    return 0;
}
```

---

## Program 78: Using Struct
```cpp
#include <iostream>
struct Point {
    int x, y;
};
int main() {
    Point p = {10, 20};
    std::cout << "Point: (" << p.x << ", " << p.y << ")" << std::endl;
    return 0;
}
```

---

## Program 79: Using Union
```cpp
#include <iostream>
union Data {
    int i;
    float f;
};
int main() {
    Data d;
    d.i = 42;
    std::cout << "Union integer: " << d.i << std::endl;
    d.f = 3.14f;
    std::cout << "Union float: " << d.f << std::endl;
    return 0;
}
```

---

## Program 80: Bit Manipulation Example
```cpp
#include <iostream>
int main() {
    int x = 5; // 0101
    int y = x << 1; // 1010
    std::cout << "x << 1: " << y << std::endl;
    return 0;
}
```

---

## Program 81: Using Bitset
```cpp
#include <iostream>
#include <bitset>
int main() {
    std::bitset<8> bits(42);
    std::cout << "Bitset: " << bits << std::endl;
    return 0;
}
```

---

## Program 82: String to Integer Conversion
```cpp
#include <iostream>
#include <string>
int main() {
    std::string s = "12345";
    int num = std::stoi(s);
    std::cout << "Integer: " << num << std::endl;
    return 0;
}
```

---

## Program 83: Integer to String Conversion
```cpp
#include <iostream>
#include <string>
int main() {
    int num = 6789;
    std::string s = std::to_string(num);
    std::cout << "String: " << s << std::endl;
    return 0;
}
```

---

## Program 84: Using STL find Algorithm
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
int main() {
    std::vector<int> nums = {1,2,3,4,5};
    auto it = std::find(nums.begin(), nums.end(), 3);
    if(it != nums.end())
        std::cout << "Found 3 at position " << std::distance(nums.begin(), it) << std::endl;
    else
        std::cout << "3 not found" << std::endl;
    return 0;
}
```

---

## Program 85: Using STL count Algorithm
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
int main() {
    std::vector<int> nums = {1,2,2,3,3,3};
    int count = std::count(nums.begin(), nums.end(), 3);
    std::cout << "3 appears " << count << " times" << std::endl;
    return 0;
}
```

---

## Program 86: Using STL transform Algorithm
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
int main() {
    std::vector<int> nums = {1,2,3,4,5};
    std::vector<int> cubes(nums.size());
    std::transform(nums.begin(), nums.end(), cubes.begin(), [](int x){ return x*x*x; });
    std::cout << "Cubes: ";
    for(auto n : cubes) std::cout << n << " ";
    std::cout << std::endl;
    return 0;
}
```

---

## Program 87: Range-based For Loop with Vector
```cpp
#include <iostream>
#include <vector>
int main() {
    std::vector<int> nums = {10, 20, 30, 40, 50};
    for(auto n : nums)
        std::cout << n << " ";
    std::cout << std::endl;
    return 0;
}
```

---

## Program 88: Iterating over a Map
```cpp
#include <iostream>
#include <map>
int main() {
    std::map<std::string, int> scores = {{"Alice", 90}, {"Bob", 85}};
    for(const auto &pair : scores)
        std::cout << pair.first << " : " << pair.second << std::endl;
    return 0;
}
```

---

## Program 89: Iterating over a Set
```cpp
#include <iostream>
#include <set>
int main() {
    std::set<int> s = {3, 1, 4, 1, 5};
    for(auto n : s)
        std::cout << n << " ";
    std::cout << std::endl;
    return 0;
}
```

---

## Program 90: Sum of First n Numbers (Recursion)
```cpp
#include <iostream>
int sum(int n) {
    return (n == 0) ? 0 : n + sum(n - 1);
}
int main() {
    std::cout << "Sum of first 5 numbers: " << sum(5) << std::endl;
    return 0;
}
```

---

## Program 91: Template Function (Generic Swap)
```cpp
#include <iostream>
template<typename T>
void mySwap(T &a, T &b) {
    T temp = a;
    a = b;
    b = temp;
}
int main() {
    int x = 10, y = 20;
    mySwap(x, y);
    std::cout << "x: " << x << ", y: " << y << std::endl;
    return 0;
}
```

---

## Program 92: Class Template Example
```cpp
#include <iostream>
template<typename T>
class Container {
public:
    Container(T value) : value(value) {}
    T getValue() const { return value; }
private:
    T value;
};
int main() {
    Container<int> c(42);
    std::cout << "Container holds: " << c.getValue() << std::endl;
    return 0;
}
```

---

## Program 93: Unique Pointer Demonstration
```cpp
#include <iostream>
#include <memory>
int main() {
    std::unique_ptr<int> ptr = std::make_unique<int>(42);
    std::cout << "Unique pointer value: " << *ptr << std::endl;
    return 0;
}
```

---

## Program 94: Shared Pointer Demonstration
```cpp
#include <iostream>
#include <memory>
int main() {
    std::shared_ptr<int> sptr = std::make_shared<int>(100);
    std::cout << "Shared pointer value: " << *sptr << std::endl;
    return 0;
}
```

---

## Program 95: Move Semantics Demonstration
```cpp
#include <iostream>
#include <vector>
int main() {
    std::vector<int> original = {1,2,3,4,5};
    std::vector<int> moved = std::move(original);
    std::cout << "Moved vector: ";
    for(auto n : moved) std::cout << n << " ";
    std::cout << std::endl;
    std::cout << "Original vector size: " << original.size() << std::endl;
    return 0;
}
```

---

## Program 96: Lambda for Filtering a Vector
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
int main() {
    std::vector<int> nums = {1,2,3,4,5,6,7,8,9};
    std::vector<int> evens;
    std::copy_if(nums.begin(), nums.end(), std::back_inserter(evens), [](int x){ return x % 2 == 0; });
    std::cout << "Even numbers: ";
    for(auto n : evens) std::cout << n << " ";
    std::cout << std::endl;
    return 0;
}
```

---

## Program 97: Using Chrono to Measure Time
```cpp
#include <iostream>
#include <chrono>
#include <thread>
int main() {
    auto start = std::chrono::high_resolution_clock::now();
    std::this_thread::sleep_for(std::chrono::milliseconds(500));
    auto end = std::chrono::high_resolution_clock::now();
    std::chrono::duration<double> diff = end - start;
    std::cout << "Elapsed time: " << diff.count() << " seconds" << std::endl;
    return 0;
}
```

---

## Program 98: Regex Email Validation
```cpp
#include <iostream>
#include <regex>
#include <string>
int main() {
    std::string email = "example@test.com";
    std::regex pattern(R"(^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$)");
    bool valid = std::regex_match(email, pattern);
    std::cout << "Email " << email << " is " << (valid ? "valid" : "invalid") << std::endl;
    return 0;
}
```

---

## Program 99: std::optional Demonstration (C++17)
```cpp
#include <iostream>
#include <optional>
std::optional<int> findEven(int n) {
    if(n % 2 == 0)
        return n;
    return std::nullopt;
}
int main() {
    auto result = findEven(7);
    if(result)
        std::cout << "Even number: " << *result << std::endl;
    else
        std::cout << "Not an even number" << std::endl;
    return 0;
}
```

---

## Program 100: Iterate Directory Using std::filesystem (C++17)
```cpp
#include <iostream>
#include <filesystem>
namespace fs = std::filesystem;
int main() {
    for(const auto& entry : fs::directory_iterator("."))
        std::cout << entry.path() << std::endl;
    return 0;
}
```
