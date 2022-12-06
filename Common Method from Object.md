# Common Method from **Object**

every Java class implicitly extends the class Object, which defines the following methods and provides default implementations that you should override: 

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

### Way Implementation equals, hashCode ,and toString

1. equals

   1. There are a couple ways to approach this, but best practice suggests a multi-step “filtering” approach that first **weeds out special cases**

      1. If the reference values of obj and this are equal 

      2. : If obj is null, then its object value does not equal the object value of this.

      3.  If the types of obj and this are not the same, then their object values are not equal

         1. Java gives us a way to check a slightly more general interpretation of “types are not the same”, which is better for this purpose than checking whether dynamic types are the same

            instanceof Operator helps check the dynamic type

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

# Two Remaining Problems

1. What if the loop doesn’t execute at all because q and this are both empty (but with different entry types)?
   1. There is no apparent way around this in Java!
2. What happens with an “unordered” math model type, e.g., Set or Map?
   1. – A slightly bigger mess, but it can be handled

