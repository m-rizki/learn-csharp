# Simple console app: part 01

install vs code

[install .net software development kit](https://dotnet.microsoft.com/download)

## Create, build, and run application

### create

```shell
dotnet new console -o ./(foldername)/(foldername)
```

### Build

```c#
// \learn-csharp\02-simple-console-app\src\Program.cs
Console.WriteLine("Hello C#!");
```

```shell
dotnet build
```

### run

```shell
dotnet run
```

## Get Started with .NET Libraries

.NET Class Library, Google search, and developer websites. These tools are the best way to find information on .NET classes and methods.

```c#
// the class name is Console
// member access operator, the "." symbol.
// method's name. In this case, the method's name is WriteLine.
// method invocation operator, which is a set of parentheses ().
// specify the arguments that are passed to the method for example, "Hello World!"
Console.WriteLine("Hello World!");
```

### Call different kinds of methods in the .NET Class Library

```c#
Random dice = new Random();
int roll = dice.Next(1, 7);
Console.WriteLine(roll);
```

### Stateful versus stateless methods

In software development projects, the term state is used to describe the condition of the execution environment at a specific moment in time.

```c#
// stateless methods are implemented so that they can work without referencing or changing any values already stored in memory
// Stateless methods are also known as static methods.
Console.WriteLine();
```

```c#
// stateful methods modify the state of the application by updating values or storing new values in memory.
// They're also known as instance methods.
Random dice = new Random();
int roll = dice.Next(1, 7); // you must first create an instance of the class so that the method can access state.
```

### Creating an instance of a class

```c#
Random dice = new Random(); // class instance
int roll = dice.Next(1, 7);
```

## Return values and input parameters of methods

### Return values

```c#
int roll = dice.Next(1, 7)

Console.WriteLine(dice.Next(1, 7)); // In some cases, you may want to use the return value directly
```

### Input parameters

```c#
// assign a random value to an integer named roll. In this case, the Next() method accepts two parameters,
int roll = dice.Next(1, 7);
```

### Overloaded Methods

this enables you to call the method with or without parameters.

```c#
int number = 7;
string text = "seven";

Console.WriteLine(number);
Console.WriteLine();
Console.WriteLine(text);
```

```c#
// In other cases, overloaded versions of a method accept a different number of input parameters
Random dice = new Random();
int roll1 = dice.Next();
int roll2 = dice.Next(101);
int roll3 = dice.Next(50, 101);

Console.WriteLine($"First Roll: {roll1}");
Console.WriteLine($"Second Roll: {roll2}");
Console.WriteLine($"Third Roll: {roll3}");
```

### Use docs.microsoft.com for information about overloaded methods

One of the top search results should lead to a URL that begins with [https://learn.microsoft.com](https://learn.microsoft.com). In this case, the link's title should appear as Random.Next Method.
