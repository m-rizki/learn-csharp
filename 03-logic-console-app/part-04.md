# Iterate through a code block using for statement in C\#

```c#
for (int i = 0; i < 10; i++)
{
    Console.WriteLine(i);
}
```

```c#
for (int i = 10; i >= 0; i--)
{
    Console.WriteLine(i);
}
```

```c#
for (int i = 0; i < 10; i += 3)
{
    Console.WriteLine(i);
}
```

```c#
// Use the break keyword to break the iteration statement
for (int i = 0; i < 10; i++)
{
    Console.WriteLine(i);
    if (i == 7) break;
}
```

```c#
// Loop through each element of an array
string[] names = { "Alex", "Eddie", "David", "Michael" };
for (int i = names.Length - 1; i >= 0; i--)
{
    Console.WriteLine(names[i]);
}
```

```c#
string[] names = { "Alex", "Eddie", "David", "Michael" };

for (int i = 0; i < names.Length; i++)
{
    if (names[i] == "David") names[i] = "Sammy";
}


foreach (var name in names)
{
    Console.WriteLine(name);
}
```

## Exercise - Complete a challenge activity using for and if statements

### FizzBuzz challenge

FizzBuzz is a popular coding challenge and interview question. It exercises your understanding of the `for` statement, the `if` statement, the `%` remainder operator, and your command of basic logic.

```c#
for (int i = 1; i < 101; i++)
{
    if ((i % 3 == 0) && (i % 5 == 0))
        Console.WriteLine($"{i} - FizzBuzz");
    else if (i % 3 == 0)
        Console.WriteLine($"{i} - Fizz");
    else if (i % 5 == 0)
        Console.WriteLine($"{i} - Buzz");
    else
        Console.WriteLine($"{i}");
}
```
