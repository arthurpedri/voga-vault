```csharp
using System.Collections.Generic;  
using System.Linq;
```
- Often we use LINQ with generic collections
```csharp
// 1. Data source. 
int[] numbers = new int[7] { 0, 1, 2, 3, 4, 5, 6 }; 

// 2. Query creation. 
// numQuery is an IEnumerable<int> 
var numQuery = 
    from num in numbers 
    where (num % 2) == 0 
    select num; 

// 3. Query execution. 
foreach (int num in numQuery) 
{ 
    Console.Write("{0,1} ", num); 
}
```
- In LINQ, the execution of the query is distinct from the query itself.
- You don't retrieve any data by creating a query variable, only on execution.
- Technically, LINQ can be used with any type that supports `foreach` loops.
### Forcing Immediate execution
- To force immediate execution and cache the result we can call `.ToList()` or `.ToArray()`.
```csharp
var numQuery3 = 
    (from num in numbers 
     where (num % 2) == 0 
     select num).ToArray();
```
### Returns
- Every query will return either a single value or an ==object of type `IEnumerable<T>`==.
## Query and Method syntax
```csharp
// Query syntax
var queryResult = from x in heroes
    where x.Contains("a")
    select $"{x} contains an 'a'";

// Method syntax
var methodResult = heroes
    .Where(x => x.Contains("a"))
    .Select(x => $"{x} contains an 'a'");
```
- Usually for single operator queries we will use the method syntax and for everything else the query syntax.