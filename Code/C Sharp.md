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
decimal b = 134.45E-2m; // 1.3445
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

## Strings
### String Interpolation
```csharp
string interpolation = $"Your favorite musician is {var1} and mine is {var2}.";
```
### Methods
- `.Length` property on a string.
- `.IndexOf()`
- `.Substring()` 
## Ternary Operator
```csharp
bool result = 1 == 2 ? true : false;
```

## Named Arguments
Named arguments can only be called after positional arguments.
```csharp
static void YourMethodName(int a = 0, int b = 0, int c = 0, int d = 0, int e = 0) {...}
YourMethodName(2, 1, d: 4) // a is 2, b is 1, d is 4  
YourMethodName(d: 4, 2, 1) // Error!
```

## [[Method (or Function) Overloading]]
