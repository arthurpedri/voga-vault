## References
- Classes are reference types, when we create a new instance of a class and store it in a variable, the variable is a reference to the object.
- Primitive types are value type variables, and are copied and not referenced.
- When comparing references types with `==`, the compiler performs a referential comparison, which means it checks if two variables refer to the same memory location. 

### References of Different types
```csharp
Dissertation diss = new Dissertation(50);  
IFlippable fdiss = diss;
```
- Since `Dissertation` implements `IFlippable`, we can reference it that way as well, but since `fdiss` is a `IFlippable` reference, it can **ONLY** use `IFlippable` functionality.
- This rule also applies to base classes.
- [[Polymorphism]] can be used even when the subclass is referenced using the superclass, the method in the superclass will still be overridden even if the reference type used is of the superclass:
```csharp
class Dissertation : Book  
{  
  public override string Stringify() { return "This is a Dissertation object!"; }  
}  
class Book  
{  
  public virtual string Stringify() { return "This is a Book object!"; }  
}
Book bk = new Book();  
Book bdiss = new Dissertation();  
Console.WriteLine(bk.Stringify());  // This is a Book object!
Console.WriteLine(bdiss.Stringify()); // This is a Dissertation object!
```

### Upcasting and downcasting
- Referencing objects with a reference of their own type, and inherited type, or an implemented interface is called **upcasting**.
- **Downcasting** is creating a subclass reference from a superclass or interface reference, and must be done explicitly.

### Null and Unassigned References
```csharp
Diary dy = null;
Object o;  
Console.WriteLine (o == null); // error CS0165: Use of unassigned local variable 'o'
```
- An unassigned variable will throw an error, but a `null` reference will not.

### Object Reference
- Every class is derived from `Object`. This means that any class can be referenced by as `Object`.
- Because the functionality of an object is limited by its reference type, using the `Object` type will make us lose all the functionality of the object we are referencing. 
- It can be useful when we are not sure of the type of object we are dealing with and for using the default members of the `Object` type.
- ==Value types and strings also inherit from `Object`==.
#### Useful Members
- `.Equals(Object)` — returns `true` if the current instance and the argument are equal (using value equality for value types and referential equality for reference types). 
- `.GetType()` — returns the type of the object.
- `.ToString()` — returns a string describing the object.
- The `.Equals()` and `.ToString()` methods in `Object` are `virtual`, so they can be overridden.
- `Console.WriteLine()` works for every type because it uses the `.ToString()` method that is inherited from `Object`.

### Strings
- String is a class that represents text, so it is technically a reference type. Its value is stored as a collection of `char` objects.
- It sometimes behaves similarly to a value type instead of a reference type.
    1. Modifying one reference to a string will not modify other references. This is because strings are ==[[Mutability|immutable]]==, anything that appears to modify a string actually returns a new string object.
    2. Comparing strings with the `==` operator performs a ==value comparison==, not referential.
- Like other reference types, `string` references can be `null` or unassigned. They can also be empty.