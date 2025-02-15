### **Variables in Java (Extensive Explanation)**

In Java, **variables** are used to store data values. A variable is essentially a **named memory location** that holds a value which can be manipulated during the execution of a program.

---

## **1. Variable Declaration and Initialization**
### **Syntax:**
```java
dataType variableName; // Declaration
variableName = value;  // Initialization
```
Or, **declare and initialize in one step**:
```java
dataType variableName = value;
```

### **Example:**
```java
int age = 25;
double price = 99.99;
char grade = 'A';
String name = "John";
```

---

## **2. Types of Variables in Java**
Java variables are categorized into **three main types**:

### **A. Local Variables**
- Declared inside a method, constructor, or block.
- Accessible **only within the method/block**.
- Must be **initialized** before use.
  
**Example:**
```java
public class Example {
    public void show() {
        int x = 10; // Local variable
        System.out.println(x);
    }
}
```
**Key Points:**
- No default value (must be explicitly initialized).
- Scope is limited to the method/block.

---

### **B. Instance Variables (Non-Static Variables)**
- Declared **inside a class**, but **outside any method**.
- Belong to an **instance (object)** of the class.
- Have **default values** if not initialized (e.g., `0` for int, `null` for objects).

**Example:**
```java
class Car {
    String model; // Instance variable (default: null)
    int year;     // Instance variable (default: 0)

    public void display() {
        System.out.println("Model: " + model);
        System.out.println("Year: " + year);
    }
}
```
**Key Points:**
- Allocated when an object is created and destroyed when the object is garbage-collected.
- Each object gets its **own copy** of instance variables.

---

### **C. Static Variables (Class Variables)**
- Declared using the **static** keyword.
- Belong to the **class itself**, not any specific object.
- **Shared among all instances** of the class.

**Example:**
```java
class Employee {
    static String company = "TechCorp"; // Static variable

    public void show() {
        System.out.println("Company: " + company);
    }
}
```
**Key Points:**
- Memory is allocated **only once**, at class loading time.
- Can be accessed using **class name** (`Employee.company`).

---

## **3. Variable Scope in Java**
Scope determines **where a variable can be accessed**.

| Variable Type   | Scope |
|----------------|-------|
| **Local**       | Inside the method/block only |
| **Instance**    | Inside the class (for each object) |
| **Static**      | Throughout the class (shared by all objects) |

---

## **4. Variable Default Values**
If a variable is **not initialized**, it gets a **default value** based on its type:

| Data Type  | Default Value |
|------------|--------------|
| byte, short, int, long | `0` |
| float, double | `0.0` |
| boolean | `false` |
| char | `'\u0000'` (null character) |
| Object (e.g., String) | `null` |

**Example:**
```java
class Test {
    int num;  // Default: 0
    boolean flag;  // Default: false

    void display() {
        System.out.println("num: " + num);
        System.out.println("flag: " + flag);
    }
}
```

---

## **5. Final Variables (Constants)**
- Declared using the `final` keyword.
- **Cannot be changed** after assignment.

**Example:**
```java
class Config {
    final int MAX_USERS = 100; // Constant
}
```
**Key Points:**
- Must be initialized when declared or in a constructor.
- Conventionally written in **uppercase** (e.g., `MAX_USERS`).

---

## **6. Difference Between Instance, Local, and Static Variables**
| Feature | Local Variable | Instance Variable | Static Variable |
|---------|---------------|-------------------|----------------|
| Declared In | Method/block | Class (outside methods) | Class (using `static`) |
| Scope | Within method/block | Whole object | Whole class |
| Default Value | None (must initialize) | Yes | Yes |
| Memory Allocation | On method execution | On object creation | At class loading |
| Access Using | Directly inside method | `objectName.variable` | `ClassName.variable` |

---

## **7. Type Inference (var - Java 10+)**
Introduced in Java 10, `var` allows Java to **infer the type** automatically.

```java
var name = "Alice"; // Compiler infers type as String
var age = 30;       // Compiler infers type as int
```
**Key Points:**
- `var` **cannot** be used for class variables.
- Must be initialized at declaration.

---

## **8. Summary**
- Java variables store data and come in **local, instance, and static** types.
- **Local variables** exist within methods and must be initialized.
- **Instance variables** belong to objects and have default values.
- **Static variables** belong to the class and are shared by all instances.
- Use `final` for **constants**.
- Java 10 introduced `var` for **type inference**.

Would you like a hands-on example or a deeper dive into any specific topic? 🚀
