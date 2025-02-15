In Java, **strings** are sequences of characters, and they are represented by the `String` class, which is part of the `java.lang` package.

## **1. Creating Strings**
Java provides multiple ways to create strings:

```java
// Using string literals (preferred for efficiency)
String str1 = "Hello, World!";

// Using the 'new' keyword (creates a new object in heap memory)
String str2 = new String("Hello, World!");
```
**Note**: Strings created with literals are stored in the **String pool**, while `new String()` creates a new object in heap memory.

---

## **2. String Methods**
The `String` class provides many built-in methods for manipulation.

```java
String str = "Java Programming";

// Length of the string
int len = str.length();  // 16

// Convert to uppercase/lowercase
String upper = str.toUpperCase();  // "JAVA PROGRAMMING"
String lower = str.toLowerCase();  // "java programming"

// Get a character at a specific index
char ch = str.charAt(5);  // 'P'

// Check if a string contains a substring
boolean contains = str.contains("Prog");  // true

// Get a substring
String sub = str.substring(5, 16);  // "Programming"

// Replace characters or substrings
String replaced = str.replace("Java", "Python");  // "Python Programming"

// Check if a string is empty
boolean isEmpty = str.isEmpty();  // false

// Trim spaces from start and end
String trimmed = "  Hello  ".trim();  // "Hello"

// Split a string into an array
String[] words = str.split(" ");  // ["Java", "Programming"]
```

---

## **3. String Comparison**
### **Using `==` (Reference Comparison)**
```java
String a = "Hello";
String b = "Hello";
String c = new String("Hello");

System.out.println(a == b); // true (same reference in the String pool)
System.out.println(a == c); // false (different objects in heap memory)
```

### **Using `.equals()` (Content Comparison)**
```java
System.out.println(a.equals(c)); // true (compares actual content)
```

### **Using `.compareTo()` (Lexicographical Comparison)**
```java
String x = "apple";
String y = "banana";
System.out.println(x.compareTo(y)); // Negative (-1) since "apple" < "banana"
```

---

## **4. String Immutability**
Strings in Java are **immutable**, meaning their values **cannot be changed** after creation.

```java
String s = "Hello";
s.concat(" World"); // Creates a new string but doesn't modify 's'
System.out.println(s); // Output: "Hello" (original remains unchanged)
```
To modify strings efficiently, use `StringBuilder` or `StringBuffer`.

---

## **5. StringBuilder (Mutable)**
If you need to modify strings frequently, use `StringBuilder` (faster, not thread-safe) or `StringBuffer` (thread-safe).

```java
StringBuilder sb = new StringBuilder("Hello");
sb.append(" World");
System.out.println(sb.toString()); // "Hello World"
```

---

## **6. String Formatting**
```java
String name = "Alice";
int age = 25;
String formatted = String.format("My name is %s and I am %d years old.", name, age);
System.out.println(formatted); // "My name is Alice and I am 25 years old."
```

---

## **7. String Interning**
Java optimizes memory by storing **string literals** in a **string pool**.
```java
String s1 = "Java";
String s2 = new String("Java").intern(); // Moves to the string pool
System.out.println(s1 == s2); // true
```

---

### **Conclusion**
- Strings in Java are **immutable**.
- Use **string literals** for efficiency.
- Use `.equals()` for **content comparison**.
- Use **StringBuilder** for frequent modifications.

Would you like any specific examples? 🚀
