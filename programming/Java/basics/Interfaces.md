### **Interfaces in Java**

An **interface** in Java is a blueprint of a class that defines a contract for classes to follow. It contains **abstract methods** (methods without a body) that must be implemented by any class that **implements** the interface. Interfaces help achieve **abstraction** and **multiple inheritance** in Java.

---

## **1. Defining an Interface**
An interface is defined using the `interface` keyword.

```java
// Defining an interface
interface Animal {
    void makeSound();  // Abstract method (no body)
}
```

---

## **2. Implementing an Interface**
A class uses the `implements` keyword to implement an interface.

```java
// Implementing the interface
class Dog implements Animal {
    public void makeSound() { // Must provide implementation
        System.out.println("Bark!");
    }
}
```

---

## **3. Multiple Interfaces**
A class can implement multiple interfaces, allowing multiple inheritance.

```java
interface Flyable {
    void fly();
}

interface Swimmable {
    void swim();
}

class Duck implements Flyable, Swimmable {
    public void fly() {
        System.out.println("Duck is flying");
    }
    
    public void swim() {
        System.out.println("Duck is swimming");
    }
}
```

---

## **4. Default & Static Methods in Interfaces (Java 8+)**
Java 8 introduced **default methods** and **static methods** in interfaces.

### **Default Method**
A method in an interface with a body. It can be overridden by implementing classes.

```java
interface Vehicle {
    default void start() {
        System.out.println("Vehicle is starting");
    }
}

class Car implements Vehicle {
    // Inherits the default method
}
```

### **Static Method**
A method that belongs to the interface itself.

```java
interface Utility {
    static void showMessage() {
        System.out.println("Static method in interface");
    }
}

// Calling the static method
Utility.showMessage();
```

---

## **5. Functional Interfaces (Java 8+)**
A **functional interface** is an interface with exactly **one abstract method**, used for **lambda expressions**.

```java
@FunctionalInterface
interface Calculator {
    int add(int a, int b);
}

// Lambda Expression
public class Main {
    public static void main(String[] args) {
        Calculator calc = (a, b) -> a + b;
        System.out.println(calc.add(5, 3));  // Output: 8
    }
}
```

---

## **6. Marker Interfaces**
An **empty interface** (no methods) used for tagging classes.

```java
interface Serializable {}  // Marker interface

class Data implements Serializable { }
```

---

## **7. Key Points**
- **Interfaces cannot have constructors.**
- **All methods are implicitly `public abstract` (unless default/static).**
- **All fields are implicitly `public static final` (constants).**
- **Classes can implement multiple interfaces but can extend only one class.**


### **Real-World Example: Payment System Using Interfaces**  

Let's say we're building a payment system where we support multiple payment methods like **Credit Card** and **PayPal**. We can use an interface to define a contract for payment processing.

---

### **Step 1: Define an Interface**
```java
// Payment interface defining a common method for all payment types
interface Payment {
    void processPayment(double amount);
}
```

---

### **Step 2: Implement Different Payment Methods**
```java
// Implementing Credit Card Payment
class CreditCardPayment implements Payment {
    public void processPayment(double amount) {
        System.out.println("Processing credit card payment of $" + amount);
    }
}

// Implementing PayPal Payment
class PayPalPayment implements Payment {
    public void processPayment(double amount) {
        System.out.println("Processing PayPal payment of $" + amount);
    }
}
```

---

### **Step 3: Create a Payment Processor**
We create a method that processes payments using any class that implements the `Payment` interface.

```java
// Payment Processor class
class PaymentProcessor {
    public void makePayment(Payment paymentMethod, double amount) {
        paymentMethod.processPayment(amount);
    }
}
```

---

### **Step 4: Test the System**
```java
public class Main {
    public static void main(String[] args) {
        PaymentProcessor processor = new PaymentProcessor();

        // Paying with Credit Card
        Payment creditCard = new CreditCardPayment();
        processor.makePayment(creditCard, 100.50);

        // Paying with PayPal
        Payment paypal = new PayPalPayment();
        processor.makePayment(paypal, 200.75);
    }
}
```

---

### **Output**
```
Processing credit card payment of $100.5
Processing PayPal payment of $200.75
```

---

### **Why Use Interfaces Here?**
1. **Loose Coupling** – The `PaymentProcessor` class doesn’t need to know the exact payment method.
2. **Scalability** – We can add new payment methods (e.g., Google Pay) without modifying existing code.
3. **Flexibility** – Any class implementing `Payment` can be processed.

