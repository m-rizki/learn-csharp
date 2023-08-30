# Store and iterate through sequences of data using Arrays and the foreach statement in C\#

## Introduction

Learning objectives:

- Create and initialize a new array.
- Assign and retrieve the values of array elements.
- Iterate through each element of an array using the `foreach` statement.

## Exercise - Get started with array basics

```c#
// The new operator creates a new instance of an array in the computer's memory that can hold three string values.
// string[] -> array of string, [3] -> number of elements that the array can hold 
string[] fraudulentOrderIDs = new string[3]

fraudulentOrderIDs[0] = "A123";
fraudulentOrderIDs[1] = "B456";
fraudulentOrderIDs[2] = "C789";
// fraudulentOrderIDs[3] = "D000";

// Retrieve values from elements of an array
Console.WriteLine($"First: {fraudulentOrderIDs[0]}");
Console.WriteLine($"Second: {fraudulentOrderIDs[1]}");
Console.WriteLine($"Third: {fraudulentOrderIDs[2]}");

// Reassign the value of an array
fraudulentOrderIDs[0] = "F000";

Console.WriteLine($"Reassign First: {fraudulentOrderIDs[0]}");
```

### Initialize an array

```c#
string[] fraudulentOrderIDs = { "A123", "B456", "C789" };

Console.WriteLine($"First: {fraudulentOrderIDs[0]}");
Console.WriteLine($"Second: {fraudulentOrderIDs[1]}");
Console.WriteLine($"Third: {fraudulentOrderIDs[2]}");

fraudulentOrderIDs[0] = "F000";

Console.WriteLine($"Reassign First: {fraudulentOrderIDs[0]}");

// Use the Length property of an array
Console.WriteLine($"There are {fraudulentOrderIDs.Length} fraudulent orders to process.");
```

### knowledge check

Array:

- A sequence of individual data elements accessible through a single variable name.
- An array data structure with a single name and multiple data locations.

## Exercise - Implement the foreach statement

### Looping through an array using foreach

```c#
string[] names = { "Rowena", "Robin", "Bao" };
foreach (string name in names)
{
    Console.WriteLine(name);
}
```

### Create and initialize an array of int

```c#
int[] inventory = { 200, 450, 700, 175, 250 };
int sum = 0;
int bin = 0;
foreach (int items in inventory)
{
    sum += items;
    bin++;
    Console.WriteLine($"Bin {bin} = {items} items (Running total: {sum})");
}
Console.WriteLine($"We have {sum} items in inventory.");
```

## Complete a challenge activity for nested iteration and selection statements

```c#
string[] teamMember = {"B123", "C234", "A345", "C15", "B177", "G3003", "C235", "B179"};

foreach (string member in teamMember) {
  if(member.StartsWith("B")) {
    Console.WriteLine(member);
  }
}
```
