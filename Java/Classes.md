# **Classes in Java **

A **class** in Java is a blueprint for creating objects. It defines the **attributes** (variables) and **behaviors** (methods) of objects. A class is a fundamental concept in **Object-Oriented Programming (OOP)**.

---

## **1. Defining a Class**
### **Syntax:**
```java
class ClassName {
    // Variables (attributes)
    dataType variableName;

    // Methods (behaviors)
    returnType methodName() {
        // Method body
    }
}
```

### **Example:**
```java
class Car {
    // Attributes
    String brand;
    int speed;

    // Method
    void drive() {
        System.out.println(brand + " is driving at " + speed + " km/h.");
    }
}
```
- `Car` is a **class**.
- `brand` and `speed` are **instance variables**.
- `drive()` is a **method**.

---

## **2. Creating Objects (Instantiation)**
To use a class, you must create **objects** using the `new` keyword.

```java
public class Main {
    public static void main(String[] args) {
        Car myCar = new Car(); // Creating an object
        myCar.brand = "Toyota"; // Assigning values
        myCar.speed = 120;
        myCar.drive(); // Calling method
    }
}
```
### **Output:**
```
Toyota is driving at 120 km/h.
```

---

## **3. Class Components**
A class contains **variables, methods, constructors, and blocks**.

### **A. Variables in a Class**
- **Instance Variables** → Belong to an object.
- **Static Variables** → Belong to the class (shared by all objects).

```java
class Example {
    int x = 10; // Instance variable
    static int y = 20; // Static variable
}
```

---

### **B. Methods in a Class**
Methods define the **behavior** of objects.

```java
class MathOperations {
    int add(int a, int b) {
        return a + b;
    }
}
```

---

### **C. Constructors in a Class**
A **constructor** initializes objects. It has the **same name as the class** and **no return type**.

```java
class Person {
    String name;

    // Constructor
    Person(String personName) {
        name = personName;
    }

    void display() {
        System.out.println("Name: " + name);
    }
}
```

**Creating an object with a constructor:**
```java
Person p1 = new Person("Alice");
p1.display();
```

### **Output:**
```
Name: Alice
```

---

## **4. Types of Classes in Java**
| Class Type | Description | Example |
|------------|------------|---------|
| **Concrete Class** | A regular class with complete methods | `class Car {}` |
| **Abstract Class** | Cannot be instantiated; contains abstract methods | `abstract class Animal {}` |
| **Final Class** | Cannot be extended | `final class Constants {}` |
| **Static Class** | Contains only static methods and variables | `class MathUtils {}` |

### **Example of Abstract Class**
```java
abstract class Animal {
    abstract void makeSound(); // Abstract method
}

class Dog extends Animal {
    void makeSound() {
        System.out.println("Bark");
    }
}
```

---

## **5. Class Inheritance**
A class can **inherit** from another class using `extends`.

```java
class Animal {
    void eat() {
        System.out.println("Eating...");
    }
}

class Dog extends Animal {
    void bark() {
        System.out.println("Barking...");
    }
}

public class Main {
    public static void main(String[] args) {
        Dog d = new Dog();
        d.eat(); // Inherited method
        d.bark();
    }
}
```

### **Output:**
```
Eating...
Barking...
```

---

## **6. Summary**
- A **class** is a blueprint for creating objects.
- **Instance variables** store object-specific data.
- **Methods** define behavior.
- **Constructors** initialize objects.
- **Inheritance** allows code reuse.
- **Abstract and final classes** modify class behavior.

Would you like more examples or details on a specific topic? 🚀
