[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/7TXVPuTD)

### ***Hw - 1 Omer Ediz AYDIN - Getir Java Spring Boot Bootcamp***

## Why we need to use OOP? Some major OOP Languages.

OOP is a programming paradigm that allows developer to organize software design around objects, which represents a real-world entity with attributes and behaviors. It helps for promoting, modularity and also reusability in code. Moreover, using OOP approach gives us ability to maintainability and abstraction as well as encapsulation, inheritance and polymoprhism.

### Major OOP Languages:
	Java, C++, Smaltalk, C#, Ruby etc. There are many more.

## Interface vs Abstract class?

In OOP, interfaces and abstract classes are both used to define the structure of classes. However, they serve different purposes. In this regard, I would like to continue with a table that describes differences


***Feature***					  ****Interface***				***Abstract Class***								                  
Method 
Implementation			No implementation (except default methods in Java 8+)	Can have both abstract and concrete methods
Inheritance			Multiple interfaces can be implemented			Can inherit only one abstract class
Constructors		  	Cannot have constructors				Can have constructors
Fields				Can only have constants (static final)			Can have instance fields
Access Modifiers		Methods are implicitly public				Methods can have various access modifiers (public, private, etc.)
When to Use			To define a contract for what a class can do		To define shared functionality and allow some flexibility in subclass implementation

## Why we need equals and hashcode? When to override?
equals(): is to used to check if two objects are considered equal in terms of their state(attribute).
hashcode(): provides a way of converting an object into a hash value(integer). It might be used in hash-based collections like HashMap or HashSet.

### When to override equals() and hashCode()?
You want to compare objects based on their content or state, rather than their memory address since you need logical equality for your objects.

The objects you are working with will be used in hash-based collections like HashMap, HashSet, or Hashtable.
The hashCode() should be consistent with equals() — that is, if two objects are considered equal according to the equals() method, they must have the same hash code.


## Diamond problem in Java? How to fix it?

Diamond problem in Java means that an issue arises when multiple inheritance is used in object-oriented programming. However, Java does not support multiple inheritance directly with classes to avoid this problem. Java does allow multiple inheritance through interfaces, but this can still lead to a similar problem when a class implements multiple interfaces that have default methods with the same signature. Diamond problem arises when a class inherits from two interfaces, both of which provide a default implementation for the same method. This leads to ambiguity because the compiler doesn't know which default method to use.

### How to fix it?

***Solution - 1 :*** Java provides a way to resolve the diamond problem using method overriding. If a class implements multiple interfaces that provide conflicting default methods, it can override the method to resolve the ambiguity.

***Solution - 2 :*** Explicitly calling methods from interfaces.

	Let's assume A and B are both interfaces that have signiture of display();

	class C implements A, B {
    @Override
    public void display() {
        A.super.display();  // Calls the display() method from A
        B.super.display();  // Calls the display() method from B
    }
}


### Why we need Garbagge Collector. How does it run?

It's main function is to manage memory by automatically identifying and freeing up memory that is no longer in use by the program, helping prevent memory leaks and ensuring efficient use of system resources. As a quick reminder, legacy programming languages don't have garbagge collector, so you, as a developer, are supposed to free up all memory usage. Let's think about C programming language. You need to manage memory efficiently so that you don't run into memory leak or excessive memory usage.

I want to take an overview to explain how it works since it requires too much texting etc. to explain it.

It works mainly in two steps:

 ***- Marking:*** The Garbagge Collector identifies which objects in memory are still in use by following references from active parts of the program (like variables or function calls).

 ***- Sweeping:*** It then frees the memory used by objects that are no longer referenced (those that are not reachable).

This process helps prevent memory leaks and allows the program to run without manually managing memory allocation and deallocation.

## Java 'static' keyword usage?

The static keyword in Java is used to define class-level methods and variables. When something is declared as static, it belongs to the class itself, rather than to any specific instance of the class. This means that static variables and methods can be accessed without creating an instance of the class.

 **- Static variables:** Shared across all instances of the class.
 **- Static methods:** Can be called without creating an instance of the class.
 **- Static blocks:** Used for static initialization.
 **- Static inner classes:** Can be instantiated without an instance of the outer class.
 **- Static members** (variables and methods) are useful when you want to maintain data or behavior that is common across all instances of a class.

## Immutability means ? Where, How and Why to use it ?

It's a concept where an object’s state cannot be modified after it is created. Once an immutable object is created, it cannot be changed.  No fields or properties of the object can be altered. Instead, if any change is needed, a new object with the updated state is created, while the original object remains unchanged.

There are so many places to use this one but the thing that I want to emphase that I mainly use it when I need to deep copy of an Entity. When we use Spring Data JPA, there can be error about entities' reference, by doing so, you can prevent this error and save your new entity with new reference to your db. (There are other methods in Entity Manager but I am speaking more abstraction level where you cannot have access to entity manager in case you use only spring data jpa interfaces out-of-box)

Composition and Aggregation means and differences ?

***Composition :*** Composition is a stronger form of association where one object owns or controls the lifecycle of another object.

***Aggregation :*** Aggregation is a weaker form of association where one object is related to another, but there is no ownership. The whole object can exist independently of the part object.

***Feature***		  ***Composition***									***Aggregation***																		                          
Ownership	  The parent object owns the child object.					The parent object does not own the child object.
Lifespan	  The child object's lifecycle is controlled by the parent object.		The child object can outlive the parent object.
UML		  Filled diamond on the parent side.						Empty diamond on the parent side.
Example		  A House contains Rooms.							A Library contains Books.						
Dependency	Strong dependency — part cannot exist without the whole.			Weaker dependency — part can exist independently.

## Cohesion and Coupling means and differences ?

Those are fundamental concepts in software design that relates to how components or modules interact with each other within a system.
***Cohesion :***  it's a measure of how strongly the elements inside a module belong together. 
***Coupling :***  it indicates how tightly one module is connected to another. Ideally, we want low coupling, where modules interact minimally with each other.

***Aspect***	***Cohesion***								***Coupling***																                         
Definition	Measures the internal consistency within a module or class.		Measures the dependence between different modules or classes.
Goal		High cohesion is desired.						Low coupling is desired.							            Impact		High cohesion makes a module easier to maintain and understand.		Low coupling reduces the impact of changes and promotes reusability.
Design 		Focuses on creating well-defined and focused modules.			Focuses on minimizing dependencies between modules.

## Heap and Stack means and differences?

Two types of memory regions used for different purposes.

The stack is a region of memory that stores temporary data, typically used for function calls and local variables. The stack operates in a Last In, First Out (LIFO) manner.
- Automatically Managed (push/pop)
- Smaller
- Faster
- Temporary
- Stackover Flow

The heap is a region of memory used for dynamic memory allocation. It's where objects and data that have a flexible lifetime are stored. ,
- Manually managed or via Garbagge Collector
- Larger
- Slower
- Data persist
- Memory leaks (if not freed properly by GC)

### Exception means ? Type of Exceptions ?

Exceptions are used to handle errors or unexpected conditions that may occur during the execution of a program. Instead of the program crashing or behaving unpredictably, exceptions provide a structured way to deal with these issues.

***Exception Types:***
	**Checked Exceptions:**
		IOException, SQLException
	**Unchecked Exceptions:**
		NullPointerException, ArrayIndexOutOfBoundsException, ArithmeticException
	**Errors:**
		OutOfMemoryError, StackOverflowError

Example of how to handle an exception

        try {
            // Try to get a number from the user
            System.out.print("Enter a number: ");
            int num = Integer.parseInt(scanner.nextLine());
            System.out.println("You entered: " + num);
        } 
        // Catch block to handle specific exceptions
        catch (NumberFormatException e) {
            System.out.println("That's not a valid number! Please enter a valid integer.");
        }

We can also create or custom exceptions so that i can return in response.

    class WordContainsException extends Exception
    {   
      // Parameterless Constructor
      public WordContainsException() {}

      // Constructor that accepts a message
      public WordContainsException(String message)
      {
         super(message);
      }
    }

    try
    {
         if(word.contains(" "))
         {
              throw new WordContainsException();
         }
    }
    catch(WordContainsException ex)
    {
          // Process message however you would like
    }

***For curious minds:*** 
https://stackoverflow.com/questions/8423700/how-to-create-a-custom-exception-type-in-java
https://stackoverflow.com/questions/52437023/best-way-to-add-the-custom-exception-for-the-spring-boot-code

### How to summarize ‘clean code’ as short as possible ?

I would like to ***cite*** it from ***refactoring.guru*** which says **"Clean code is that code that is easy to read, understand and maintain. Clean code also makes software development predictable and increases the quality of a resulting product."**

### What is the method of hiding in Java ?

Method hiding in Java occurs when a static method in a subclass has the same signature as a static method in its superclass. The method in the subclass does not override the method in the superclass but instead hides it, and the method resolution happens at compile time based on the reference type.

### What is the difference between abstraction and polymorphism in Java ?

**Abstraction:**
    - Hiding implementation details and showing only the essential features.
    - To reduce complexity by hiding unnecessary details. 
    - Abstract classes and interfaces.  

**Polymorphism:**
    - The ability of an object to take many forms.
    - To allow methods to behave differently based on the object type.
    - Method overloading (compile-time) and method overriding (runtime).

Abstraction is about defining "what" needs to be done, but leaving out the details of "how."
Polymorphism is about defining a method to behave in multiple ways based on the object type.



		
