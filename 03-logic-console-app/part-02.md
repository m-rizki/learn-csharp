# Control variable scope and logic using code blocks in C\#

## Introduction

Learning objectives

- Understand the impact of declaring and initializing variables inside and outside of code blocks.
- Improve the readability code blocks in if statements.
- Identify namespaces, classes, and methods in your code.
- Understand the use of the using statement to instruct the compiler where to look for classes referenced in your code.

## Exercise - Code blocks and variable scope

```c#
bool flag = true;
if (flag)
{
    int value = 10;
    Console.WriteLine($"Inside of code block: {value}"); // 10
}
```

```c#
bool flag = true;
if (flag)
{
    int value = 10;
    Console.WriteLine("Inside of code block: " + value);
}
Console.WriteLine($"Outside of code block: {value}"); // error
```

```c#
// Move the variable outside
bool flag = true;
int value;

if (flag)
{
    value = 10;
    Console.WriteLine("Inside of code block: " + value);
}
Console.WriteLine($"Outside of code block: {value}"); // error
```

```c#
// Initialize the variable with a value
bool flag = true;
int value = 0;

if (flag)
{
    value = 10;
    Console.WriteLine("Inside of code block: " + value); // 10
}
Console.WriteLine("Outside of code block: " + value); // 10
```

## Exercise - Remove code blocks from if statements

```c#
bool flag = true;
if (flag)
{
    Console.WriteLine(flag);
}
```

```c#
// Remove the curly braces
bool flag = true;
if (flag)
    Console.WriteLine(flag);
```

```c#
// Examine the readability of single-line form if statements
bool flag = true;
if (flag) Console.WriteLine(flag);
```

```c#
string name = "steve";

if (name == "bob")
    Console.WriteLine("Found Bob");
else if (name == "steve") 
    Console.WriteLine("Found Steve");
else
    Console.WriteLine("Found Chuck");
```

## Challenge

```c#
using System;

int[] numbers = { 4, 8, 15, 16, 23, 42 };
int total = 0;
bool found = false;

foreach (int number in numbers)
{
    total += number;
    if (number == 42)
        found = true;
}

if (found)
    Console.WriteLine("Set contains 42");

Console.WriteLine($"Total: {total}");
```
