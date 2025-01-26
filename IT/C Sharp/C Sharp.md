## [[C Sharp Style Guide]]

## Basic I/O
- `Console.WriteLine(string)` 
- `string input = Console.ReadLine()`

## Data Type Conversion
- Implicit happens if no data will be lost in the conversion:
```csharp
int myInt = 3;  
// Turns it into a double  
double myDouble = myInt;
```
- Explicit needs a cast operator or using methods:
```csharp
double myDouble = 3.2;  
// Round myDouble to the nearest whole number  
int myInt = (int)myDouble;
Convert.ToString(myInt);
```
## Floating Point Numeric Types
### Digit Separator and scientific notation
```csharp
double d = 0.42e2; // 42
float f = 3_000.5F; // 3000.5
decimal m = 134.45E-2m; // 1.3445
```
### Double
- Double is the standard for literals without suffixes.
- Can use the suffixes `d` or `D` to be specific.
- Is larger than float but smaller than decimal, should be used when performance is more important than ensuring accuracy.
### Float
- Uses suffixes `f` or `F` .
- Least precision but very small size.
### Decimal
- Most precise, usually used for financial applications.
- Uses suffixes `m` or `M`.

## Built-In math
- `Math.Abs()`—will find the absolute value of a number. Example: `Math.Abs(-5)` returns 5.
- `Math.Sqrt()`—will find the square root of a number. Example: `Math.Sqrt(16)` returns 4.
- `Math.Floor()`—will round the given double or decimal down to the nearest whole number. Example: `Math.Floor(8.65)` returns 8.
- `Math.Min()`—returns the smaller of two numbers. Example: `Math.Min(39, 12)` returns 12.
- `Math.Pow()`
- `Math.Max()`
- `Math.Ceiling()`

## Var
- `var` are implicitly typed variables.

## Strings
### String Interpolation
```csharp
string interpolation = $"Your favorite musician is {var1} and mine is {var2}.";
```
### Methods
- `.Length` property on a string.
- `.IndexOf()`
- `.Substring()` 
## Operators
### Ternary Operator
```csharp
bool result = 1 == 2 ? true : false;
```
### Spread element
`..` can be used to inline collection values in a collection expression.
```csharp
string[] vowels = [ "a", "e", "i", "o", "u" ]; 
string[] consonants = [ "b", "c", "z" ]; 
string[] alphabet = [ ..vowels, ..consonants, "y" ];
```
## Yield statement
- `yield` statement is used in an iterator to provide the next value or signal the end of an iteration.
- `yield return` will provide the next value in the iteration.
- `yield break` to explicitly signal the end of the iteration. An iteration will also finish when control reaches the end of the iterator.
## Using statement
- The `using` statement ensures the correct use of an `IDisposable` instance.
- When the control leaves the block of the using statement, an acquired `IDisposable` instance is disposed, even if and exception occurs within the block of the `using` statement.
```csharp
var numbers = new List<int>();
using (StreamReader reader = File.OpenText("numbers.txt"))
{
    string line;
    while ((line = reader.ReadLine()) is not null)
    {
        if (int.TryParse(line, out int number))
        {
            numbers.Add(number);
        }
    }
}
```
- We can also use a `using` *declaration*, which doesn't require braces. The local variable is disposed at the end of the scope in which it's declared.
```csharp
static IEnumerable<int> LoadNumbers(string filePath)
{
    using StreamReader reader = File.OpenText(filePath);
    
    var numbers = new List<int>();
    string line;
    while ((line = reader.ReadLine()) is not null)
    {
        if (int.TryParse(line, out int number))
        {
            numbers.Add(number);
        }
    }
    return numbers;
}
```
## Named Arguments
Named arguments can only be called after positional arguments.
```csharp
static void YourMethodName(int a = 0, int b = 0, int c = 0, int d = 0, int e = 0) {...}
YourMethodName(2, 1, d: 4) // a is 2, b is 1, d is 4  
YourMethodName(d: 4, 2, 1) // Error!
```

## [[Method (or Function) Overloading]]

## Return and Out
One way to return multiple values is using `out`. Out parameters must be assigned a value within the method.
```csharp
public static bool TryParse (string s, out int result);

bool success = Int32.TryParse("10602", out int number); // success = true, number = 10602
```

## Expression body definitions & lambda expressions
```csharp
member => expression;
static bool isEven(int num) => num % 2;
(input-parameters) => expression // parentheses not necessary if only one parameter and type can be removed if it can be inferred
(input-parameters) => { statement; } // multiple expressions
```

## Arrays
```csharp
int[] plantHeights = { 3, 4, 6 };
int[] plantHeights = new int[] { 3, 4, 6 };
```
If you decide to define an array and then initialize it later (rather in one line like above) you **must** use the `new` keyword:
```csharp
int[] plantHeights;  
// This works  
plantHeights = new int[] { 3, 4, 6 };  

// This will cause an error  
plantHeights = { 3, 4, 6 };
```
### Methods
- `Array.Sort()`
- `Array.IndexOf()`
- `Array.Find()`
- `Array.Copy()`
- `Array.Reverse()`
- `Array.Clear()`

## For Each
Works on collections:
```csharp
foreach(type element in sequence)  
{  
  statement;  
}
```

## Jump Statements
- `break` will break out of a loop block.
- `continue` will bypass the code and go to the next iteration.

## Classes
Classes have lots of different types of members.
### Fields and Properties
```csharp
class Forest
{
    // Field
    public int area;   
    
    // Property
    public int Area  
    {  
      get { return area; }  
      set { area = value; }  
    }
}
```
- A property controls the access to a field. 
- Usually fields will be in lowercase and Properties the same name but in uppercase.
- Useful for validating and adding logic to getters and setters.
#### Automatic property
```csharp
// Automatic Property
public int Area { get; set; }
```
- Since the getter and setter pattern is so common, there is a short-hand for it.
- No need to define the equivalent field, it is defined in the background.

### Access Modifiers
- `public` — a public member can be accessed by any class
- `private` — a private member can only be accessed by code in the same class
- C# encourages [[Encapsulation|encapsulation]] by defaulting class members to `private` and classes to `public`.
- `protected` — a _protected_ member can be accessed by the current class and any class that inherits from it.

### Static modifier
- The `static` modifier makes it so the member, class, or function belongs to the type itself and not to a specific instance.
- A static method can only access other static members.
- Static constructors will run once before a class is used (before an object is instantiated and before a static member is accessed).
- Static classes cannot be instantiated, so they are usually used when making utilities or libraries, like `Math` or `Console`.

### Constructors
```csharp
class Forest  
{  
  public int Area;  
  
  public Forest(int area)  
  {  
    Area = area;  
  }  
}
Forest f = new Forest(400);
```
- A private constructor is used to prevent parameterless constructors. 
- They are used to prevent instantiating classes that should not be instantiated outside.
- Private constructors are sometimes used in classes that are almost static, but aren't for some reason.

## [[Interfaces]]
- Looks a bit like a class.
- It's common to prefix interfaces with `I`.
```csharp
interface IAutomobile  
{  
  string Id { get; }  
  void Vroom();  
}

class Sedan : IAutomobile  
{  
  public string Id { get; }   
  void Vroom() { }
}
```
- Classes that implement interfaces have to define all members of the interface.
- Interfaces cannot specify **Constructors** and **Fields**.
- Interfaces dictate what a class **MUST** have, not what it must not have.

## Inheritance
- In C# classes can only have one superclass(no multiple inheritance), but they may implement multiple interfaces.
```csharp
class Sedan : Vehicle, IAutomobile { }
```
- `base` keyword is used to access the superclass.
```csharp
class Sedan : Vehicle  
{  
  public Sedan (double speed) : base(speed)  
  {  
      base.SpeedUp(); // Accessing a method of the superclass
  }  
}
```
- If `base` is not used on the child's constructor, C# will implicitly call the default parameterless constructor for its superclass.

### Overriding inherited members
- Overriding members can be done by using the `virtual` and `override` keywords.
```csharp
 public virtual void SpeedUp() // on the superclass
 public override void SpeedUp() // on the child
```
- `virtual` allows the member to be overridden in subclasses.
- `override` allows the member to override a method define in the superclass.
- Members can also be overridden by defining a new member with the same name, effectively hiding the inherited member that still exists. 

### Abstract modifier
- `abstract` is added to a superclass member so that the subclasses are forced to define it, similar to an interface. 
- If one member of class is abstract, the class itself can't exist as an instance, it must also be abstract.
```csharp
abstract class Vehicle { }
```
- An abstract member from the superclass must be overridden in the subclass.

[[C Sharp Reference Types]]

## Lists
### Object Initialization
```csharp
List<string> citiesList2 = new List<string> { "Delhi", "Los Angeles" };
```
- Basic construction uses parentheses `( )` and no values.
- Object initialization uses curly braces `{ }` and the actual values go in-between.
```csharp
using System.Collections.Generic;
List<string> citiesList = new List<string>();
citiesList.Add("Delhi");
```
- We can find the number of elements in the list using the `Count` property:
- We can check if an element exists in a list using the `Contains()` method:
```csharp
bool success = citiesList.Remove("Delhi"); // success is true
```
- `citiesList.Clear();` will remove all elements from the list.
- `AddRange()` — takes an array or list as an argument. Adds the values to the end of the list. Returns nothing.
- `InsertRange()` — takes an `int` and array or list as an argument. Adds the values at the `int` index. Returns nothing.
- `RemoveRange()` — takes two `int` values. The first `int` is the index at which to begin removing and the second `int` is the number of elements to remove. Returns nothing.
- `GetRange()` — takes two `int` values. The first `int` is the index of the first desired element and the second `int` is the number of elements in the desired range. Returns a list of the same type.
### Generic Collection
- List class is a generic collection. They are data structures that are defined with a generic type. `List<T>`.

## [[C Sharp LINQ|LINQ]]

## Dictionary
```csharp
using System.Collections.Generic;
public class Dictionary<TKey,TValue>
```
### KeyValuePair
- When you use foreach to enumerate dictionary elements, the elements are retrieved as KeyValuePair objects. 
```csharp
foreach( KeyValuePair<string, string> kvp in openWith ) { 
    Console.WriteLine("Key = {0}, Value = {1}", kvp.Key, kvp.Value); 
}
```
## Set
```csharp
using System.Collections.Generic;
public class HashSet<T>
```
## [[Enumerated type|Enum]]
```csharp
enum Level 
{
  Low,
  Medium,
  High
}
Level myVar = Level.Medium;
```
