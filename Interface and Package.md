# Interface

Interfaces contains;

- instance methods
- stataic final varaible
- no constructor
- not static method
  - Interfaces allo static method with implementation
    - but it will aginst our use of interface of client view
- not instance
  - which not client view information

Interfaces are a compile-time construct

- Used by the Java compiler for type-checking with declared types: to make sure variables are used only where they make sense
- Recall the rules for declared types and object (dynamic) types
- Once a Java program compiles, only object types are kept at run-time • Declared types literally “disappear” in the JVM



# Package

component family is bundled into its own package, i.e., a grouping of interfaces and classes that the designer thinks “belong together” for logical reasons

Package is provide:

1.  Logical structuring: packages are **hierarchical**, i.e., you may have packages within packages
2. A namespace: units in **different** packages may have the **same name** **without** **conflict**
3. Another level of access control between public and private

