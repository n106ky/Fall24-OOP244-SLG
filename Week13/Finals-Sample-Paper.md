## Dynamic Memory Allocation and the Rule of Three - `Tag` Class Implementation

### 📝 Objective
The task is to implement a class named **`Tag`**, ensuring it adheres to the **Rule of Three** while managing dynamic memory allocation. The class should also anticipate inheritance and provide a method for formatted display. Follow the points below for the implementation details.

---

### 🔧 Implementation Details

1. **Dynamic Memory Allocation**  
   - Implement a helper method named `cloneStr` for dynamic memory allocation within the class.  
   - Use this method for managing the **`m_tagData`** member to allocate and clone string data dynamically.

2. **Inheritance Ready**  
   - Code the solution to anticipate inheritance, as **`Tag`** will serve as a base class for future subclasses.

3. **Construct the Display Method**  
   - Create a method named **`present`** that takes an `ostream` reference as an argument.  
   - The **`present`** method should:
     - Insert the **`m_tagData`** into the output stream if **`m_tagData`** is not empty.
     - Be designed for potential overriding in subclasses.

4. **Insertion Operator Overloading**  
   - Overload the **`<<` operator** for **`Tag`** objects to replicate the functionality of the **`present`** method.

5. **Unified File Implementation**  
   - Assume all components of the class and testing code are implemented in a **single file**.

6. **Main Function Testing**  
   - Test your implementation using the provided main function (below).  
   - Ensure the output matches the **expected results** for both the console and file.

---

### 📂 Provided Code and Expected Output

```cpp
#include <cstring>
#include <iostream>
#include <fstream>
using namespace std;

class Tag {
    char* m_tagData;
protected:
    char* cloneStr(const char* tag) {
        char* newTagData{};
        if (tag) {
            newTagData = new char[strlen(tag) + 1];
            strcpy(newTagData, tag);
        }
        return newTagData;
    }
public:
    Tag(const char* tag) : m_tagData(cloneStr(tag)) {}
    // ... Additional code goes here ...
};

// ... Additional code goes here ...

int main() {
    ofstream file("tag.txt");
    Tag t1 = "Alice";
    Tag t2 = t1, t3 = "to be replaced";
    Tag t4;
    t3 = t1;
    cout << ">" << t1 << ":" << t4 << "<" << endl;
    file << t1 << endl;
    return 0;
}
```

---

### ✅ Expected Output

#### **Console Output**
```
>Alice:<
```

#### **File Output (`tag.txt`)**
```
Alice
```

---

### 💡 Key Notes
- Ensure proper **dynamic memory management** to avoid memory leaks.  
- Follow the **Rule of Three**, implementing the destructor, copy constructor, and copy assignment operator.  
- Design the **`present`** method to be easily overridden in subclasses.