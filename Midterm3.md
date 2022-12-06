# After midterm 2

## Java Interface

### Interface may be used to define:

- instance methods
- static final variables
  -  it is unusual for an interface to define variables
- No constructors
- no static methods
- no instance variables

### Core interface  (kernel)

Its our kernel interface

- – The mathematical model for the type
-  – Contract(s) for the constructor(s)
-  – Contract(s) for kernel methods
-  – Contract(s) for methods inherited from Java library interfaces that do not have their own contract specifications (if applicable; e.g., an iterator or a comparator)
- The enhanced interface defines contracts for all other methods for the type

### Kernel interface design guidelines

Kernel methods generally should be:

- A minimal set of methods that is functionally complete, i.e., powerful enough to:
  - Give a variable of the type any allowable value
  - Determine the value of a variable of the type
- Powerful enough to allow a client to:
  -  Implement equals and toString
  -  Check every kernel method’s precondition

### Enhance interface

most powerful interface

### Notice there is Circularity 

![image-20221206141100229](/Users/jacksonchen/Library/Application Support/typora-user-images/image-20221206141100229.png)

Java permit the circularity because

1. Java **interface** define as **type**, i.e., the type name along with the set of its instance methods
2. An interface type may be used in Java **even if there is no implementation** of it in scope

Interfaces are a compile-time construct

- – Used by the Java compiler for type-checking with declared types: to make sure variables are used only where they make sense • 
  - Recall the rules for declared types and object (dynamic) types 
    - The declared type of a variable may be an interface type 
    - The object type can never be an interface type, because you may not instantiate a variable using new followed by an interface type
    - If the declared type is an interface type, then the object type (a class) must implement the declared type (an interface
- – Once a Java program compiles, only object types are kept at run-time 
  - • Declared types literally “disappear” in the JVM

### Packages

Each OSU CSE component family is bundled into its own package, i.e., a grouping of interfaces and classes that the designer thinks “belong together” for logical reasons

 – Example: the Queue-family components are all in the package components.queue

A package provides:

1. – Logical structuring: packages are hierarchical, i.e., you may have packages within packages
2. A namespace: units in different packages may have the same name without conflict • See also import statements
3. Another level of access control between public and private

## Object class method

### Common Method from **Object**

Eevery Java class implicitly extends the class Object, which defines the following methods and provides default implementations that you should override: 

- boolean equals(Object obj)
- int hashCode() 
- String toString()

### Default implmentation of equals, hashCode ,and toString

1. equals 
   1. Default implementation of equals: “for any non-null reference values x and y, this method [i.e., x.equals(y)] returns true if and only if x and y refer to the same object (x == y has the value true).”
2. hashCode
   1. “typically implemented by converting the internal address of the object into an integer, but this implementation technique is not required by the JavaTM programming language
3. toString
   1. Default implementation of toString: “returns a string consisting of the name of the class of which the object is an instance, the at-sign character '@', and the unsigned hexadecimal representation of the hash code of the object.”

Object cannot possibly know anything about the abstract mathematical model values (i.e., the object values) of variables

### The Crux of the Problem

- Object cannot possibly know anything about the **abstract mathematical model values** (i.e., the object values) of variables
  - which means the equal method compare reference value , maybe its not what the developer wants to compare with.
  - equals, hashCode, and toString should all behave in ways that depend on these abstract mathematical model values

### Way Implementation equals, hashCode ,and toString

1. equals

   1. There are a couple ways to approach this, but best practice suggests a multi-step “filtering” approach that first **weeds out special cases**

      1. If the reference values of obj and this are equal 

      2. : If obj is null, then its object value does not equal the object value of this.

      3. If the types of obj and this are not the same, then their object values are not equal

         1. Java gives us a way to check a slightly more general interpretation of “types are not the same”, which is better for this purpose than checking whether dynamic types are the same

            instanceof Operator helps check the dynamic type

### Steps to implements equal method 

There are a couple ways to approach this, but best practice suggests a multi-step “**filtering**” approach that first weeds out special cases

1. Step1: if the Reference value of Object obj and this are equal, then return true
2. Step2: if the obj is null then it's object value is not equal to this, then return false
3. Step3: if the type of obj and this are not same, then they are not equal
   1. using instance of to check
      1. how about collections? wo we have to use raw type, every type erasure will become object class type

### Type Erasure

For generic types, the JVM keeps track of the raw type (e.g., Queue1L or Queue2) of each variable as its dynamic type, but does not keep track of any generic type parameters (e.g., for this variable T is Integer, for that variable T is String)

This mechanism is called type erasure – Effectively (but not technically), the type parameter is replaced by Object

```
if (!(obj instanceof XYZ<?>))
//This checks whether obj has a dynamic type that implements “XYZ of unknown”, which is all the JVM knows about.
```

```
//Step 1
if (obj == this) {
return true;
}
//Step 2
if (obj == null) {
return false;
}
//Step 3
if (!(obj instanceof XYZ<?>)) {
return false;
}
//Now it's time to casting
XYZ<?> x = (XYZ<?>) obj; //we limit ourselves to using XYZKernel methods to determine whether their mathematical model values are equal.
```

### Two Remaining Problems

1. What if the loop doesn’t execute at all because q and this are both empty (but with different entry types)?
   1. There is no apparent way around this in Java!
2. What happens with an “unordered” math model type, e.g., Set or Map?
   1. – A slightly bigger mess, but it can be handled

##  Java Collections Framework

### Views in the JCF

Views for Map: 

- – Keys: Set<T> keySet()
-  – Values: Collection <T> values() 
- – Pairs: Set<Map.Entry<K,V>> entrySet()



