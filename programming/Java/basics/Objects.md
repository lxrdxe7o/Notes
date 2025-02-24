### **Objects in Java**  

An **object** in Java is an instance of a class. It represents a real-world entity with **state (attributes)** and **behavior (methods)**. Objects are created from **classes**, which serve as blueprints.  

---

## **1. Creating an Object**  

### **Step 1: Define a Class**
A class is like a template from which objects are created.  

```java
class Car {
    // Attributes (state)
    String brand;
    int speed;

    // Constructor
    Car(String brand, int speed) {
        this.brand = brand;
        this.speed = speed;
    }

    // Method (behavior)
    void displayInfo() {
        System.out.println("Car Brand: " + brand + ", Speed: " + speed + " km/h");
    }
}
```

### **Step 2: Create Objects**
An object is created using the `new` keyword.

```java
public class Main {
    public static void main(String[] args) {
        // Creating objects of the Car class
        Car car1 = new Car("Toyota", 120);
        Car car2 = new Car("Honda", 150);

        // Calling method on objects
        car1.displayInfo();
        car2.displayInfo();
    }
}
```

---

## **2. Object Characteristics**
### **a) State (Attributes)**
- Defined by **fields (variables)**
- Stores information about the object  

Example: `brand` and `speed` are attributes in the `Car` class.

### **b) Behavior (Methods)**
- Defined by **methods**  
- Describes what an object can do  

Example: `displayInfo()` prints car details.

### **c) Identity (Unique Existence)**
- Each object has a unique memory address.
- Even if two objects have the same data, they are different instances.

---

## **3. Accessing Object Members**
```java
// Accessing attributes
System.out.println(car1.brand);  // Output: Toyota

// Calling methods
car1.displayInfo();  // Output: Car Brand: Toyota, Speed: 120 km/h
```

---

## **4. Modifying Object Attributes**
```java
car1.speed = 180;  // Changing speed
car1.displayInfo();  // Output: Car Brand: Toyota, Speed: 180 km/h
```

---

## **5. Objects and Memory**
- Objects are stored in **heap memory**.
- The reference variable (like `car1`) is stored in the **stack memory**.
- `null` can be assigned to an object reference to indicate no object.

---

## **6. Garbage Collection**
Java automatically deletes unused objects through **Garbage Collection**, so you don’t need to manually free memory.

```java
car1 = null; // Now eligible for garbage collection
```

---

### **Summary**
✔ Objects are **instances** of a class.  
✔ They have **state (fields)** and **behavior (methods)**.  
✔ Objects are stored in **heap memory** and managed by **Garbage Collector**.  
✔ Created using `new ClassName();`  

### **Complex Object System: Library Management System**  

This is a **Library Management System** as an example. This system will have **Books**, **Members**, and a **Library** that manages book borrowing.

---

## **1. Define the `Book` Class**
Each book has a **title, author, and availability status**.

```java
class Book {
    String title;
    String author;
    boolean isAvailable;

    // Constructor
    public Book(String title, String author) {
        this.title = title;
        this.author = author;
        this.isAvailable = true; // Default: Available
    }

    // Display book info
    public void displayBook() {
        System.out.println("Title: " + title + ", Author: " + author + ", Available: " + isAvailable);
    }
}
```

---

## **2. Define the `Member` Class**
A member has a **name** and can borrow books.

```java
class Member {
    String name;
    Book borrowedBook;

    // Constructor
    public Member(String name) {
        this.name = name;
        this.borrowedBook = null; // No book borrowed initially
    }

    // Borrow a book
    public void borrowBook(Book book) {
        if (book.isAvailable) {
            this.borrowedBook = book;
            book.isAvailable = false;
            System.out.println(name + " borrowed \"" + book.title + "\".");
        } else {
            System.out.println("Sorry, \"" + book.title + "\" is already borrowed.");
        }
    }

    // Return a book
    public void returnBook() {
        if (this.borrowedBook != null) {
            System.out.println(name + " returned \"" + borrowedBook.title + "\".");
            borrowedBook.isAvailable = true;
            borrowedBook = null;
        } else {
            System.out.println(name + " has no borrowed books.");
        }
    }

    // Display member info
    public void displayMember() {
        if (borrowedBook != null) {
            System.out.println(name + " has borrowed \"" + borrowedBook.title + "\".");
        } else {
            System.out.println(name + " has not borrowed any book.");
        }
    }
}
```

---

## **3. Define the `Library` Class**
The library stores books and allows book management.

```java
import java.util.ArrayList;
import java.util.List;

class Library {
    List<Book> books = new ArrayList<>();

    // Add a new book to the library
    public void addBook(Book book) {
        books.add(book);
        System.out.println("Added book: " + book.title);
    }

    // Display all books
    public void displayBooks() {
        System.out.println("Library Books:");
        for (Book book : books) {
            book.displayBook();
        }
    }
}
```

---

## **4. Testing the System**
```java
public class Main {
    public static void main(String[] args) {
        // Create library
        Library library = new Library();

        // Add books
        Book book1 = new Book("1984", "George Orwell");
        Book book2 = new Book("The Alchemist", "Paulo Coelho");
        library.addBook(book1);
        library.addBook(book2);

        // Create members
        Member member1 = new Member("Alice");
        Member member2 = new Member("Bob");

        // Display books before borrowing
        library.displayBooks();

        // Alice borrows a book
        member1.borrowBook(book1);
        member1.displayMember();
        
        // Bob tries to borrow the same book
        member2.borrowBook(book1); // Should show "already borrowed"

        // Alice returns the book
        member1.returnBook();
        
        // Bob borrows the book after Alice returns it
        member2.borrowBook(book1);
        member2.displayMember();

        // Display final library books
        library.displayBooks();
    }
}
```

---

## **Output**
```
Added book: 1984
Added book: The Alchemist
Library Books:
Title: 1984, Author: George Orwell, Available: true
Title: The Alchemist, Author: Paulo Coelho, Available: true
Alice borrowed "1984".
Alice has borrowed "1984".
Sorry, "1984" is already borrowed.
Alice returned "1984".
Bob borrowed "1984".
Bob has borrowed "1984".
Library Books:
Title: 1984, Author: George Orwell, Available: false
Title: The Alchemist, Author: Paulo Coelho, Available: true
```

---

## **Concepts Used**
✅ **Encapsulation** – Each class hides its data and exposes behavior through methods.  
✅ **Objects & Interactions** – `Member` interacts with `Book` and `Library`.  
✅ **List Storage** – The library uses `ArrayList<Book>` to manage books.  

