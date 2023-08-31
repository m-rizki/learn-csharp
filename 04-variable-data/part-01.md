# Choose the correct data type in your C# code

## Intro

Learning objectives

- Learn the fundamental differences between value types and reference types.
- Describe the properties of many new numeric data types, including new integral types and floating point types.
- Write code that returns the maximum and minimum values that numeric data types can store.
- Use the new keyword to create new instances of a reference type.
- Determine which data type you should choose for a given application.

### Discover value types and reference types

Bits are represented by "1" or "0".

## Exercise - Discover integral types

```c#
Console.WriteLine("Signed integral types:");

Console.WriteLine($"sbyte  : {sbyte.MinValue} to {sbyte.MaxValue}");
Console.WriteLine($"short  : {short.MinValue} to {short.MaxValue}");
Console.WriteLine($"int    : {int.MinValue} to {int.MaxValue}");
Console.WriteLine($"long   : {long.MinValue} to {long.MaxValue}");

Console.WriteLine("");
Console.WriteLine("Unsigned integral types:");

Console.WriteLine($"byte   : {byte.MinValue} to {byte.MaxValue}");
Console.WriteLine($"ushort : {ushort.MinValue} to {ushort.MaxValue}");
Console.WriteLine($"uint   : {uint.MinValue} to {uint.MaxValue}");
Console.WriteLine($"ulong  : {ulong.MinValue} to {ulong.MaxValue}");
```

## Exercise - Discover floating-point types

```c#
Console.WriteLine("");
Console.WriteLine("Floating point types:");
Console.WriteLine($"float  : {float.MinValue} to {float.MaxValue} (with ~6-9 digits of precision)");
Console.WriteLine($"double : {double.MinValue} to {double.MaxValue} (with ~15-17 digits of precision)");
Console.WriteLine($"decimal: {decimal.MinValue} to {decimal.MaxValue} (with 28-29 digits of precision)");
```

Decimal, with ~28-29 digits of precision, has the precision required for many financial applications.

## Exercise - Discover reference types

```c#
// At this point, data is merely a variable that could hold a reference, or rather, a memory address of a value in the heap. Because it's not pointing to a memory address, it's called a null reference.
int[] data;

// The new keyword informs .NET Runtime to create an instance of int array, and then coordinate with the operating system to store the array sized for three int values in memory.
// the new operator is used to allocate memory on the heap for a reference type.
data = new int[3];

// The two lines of code in the previous step are typically shortened to a single line of code
int[] data = new int[3];

// The string data type is also a reference type.
string shortenedString = "Hello World!";
Console.WriteLine(shortenedString);
```
