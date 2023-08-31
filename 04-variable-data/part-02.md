# Convert data types using casting and conversion techniques in C\#

Learning objectives

- Use the casting operator to cast a value into a different data type.
- Use conversion methods to convert a value into a different data type.
- Guard against the loss of data when performing a cast or conversion operation.
- Use the TryParse() method to safely convert a string into a numeric data type.

## Exercise - Explore data type casting and conversion

```c#
int first = 2;
string second = "4";
int result = first + second;
Console.WriteLine(result); // error CS0029: Cannot implicitly convert type 'string' to 'int'
```

```c#
int first = 2;
string second = "4";
string result = first + second; // Compilers make safe conversions
Console.WriteLine(result); // "24"
```

```c#
int myInt = 3;
Console.WriteLine($"int: {myInt}"); // int: 3

decimal myDecimal = myInt;
Console.WriteLine($"decimal: {myDecimal}"); // decimal: 3
```

```c#
decimal myDecimal = 3.14m;
Console.WriteLine($"decimal: {myDecimal}"); // decimal: 3.14

int myInt = (int)myDecimal;
Console.WriteLine($"int: {myInt}"); // int: 3
```

```c#
decimal myDecimal = 1.23456789m;
float myFloat = (float)myDecimal;

Console.WriteLine($"Decimal: {myDecimal}"); // Decimal: 1.23456789
Console.WriteLine($"Float  : {myFloat}"); // Float:   1.234568
```

### toString()

```c#
int first = 5;
int second = 7;
string message = first.ToString() + second.ToString();
Console.WriteLine(message); // 57
```

### parse()

```c#
string first = "5";
string second = "7";
int sum = int.Parse(first) + int.Parse(second);
Console.WriteLine(sum); // 12
```

### Convert class

```c#
string value1 = "5";
string value2 = "7";
int result = Convert.ToInt32(value1) * Convert.ToInt32(value2);
Console.WriteLine(result); // 35
```

```c#
int value = (int)1.5m; // casting truncates
Console.WriteLine(value); // 1

int value2 = Convert.ToInt32(1.5m); // converting rounds up
Console.WriteLine(value2); // 2
```

## Exercise - Examine the TryParse() method

```c#
string name = "Bob";
Console.WriteLine(int.Parse(name)); // System.FormatException: 'Input string was not in a correct format.'
```

```c#
string value = "102a";
int result = 0;
if (int.TryParse(value, out result))
{
    Console.WriteLine($"Measurement: {result}");
}
else
{
    Console.WriteLine("Unable to report the measurement.");
}
```

```c#
string value = "102";
int result = 0;
if (int.TryParse(value, out result))
{
    Console.WriteLine($"Measurement: {result}");
}
else
{
    Console.WriteLine("Unable to report the measurement.");
}

Console.WriteLine($"Measurement (w/ offset): {50 + result}");
```

```c#
string value = "bad";
int result = 0;
if (int.TryParse(value, out result))
{
    Console.WriteLine($"Measurement: {result}");
}
else
{
    Console.WriteLine("Unable to report the measurement.");
}

if (result > 0)
    Console.WriteLine($"Measurement (w/ offset): {50 + result}");
```

## Exercise

```c#
string[] values = { "12.3", "45", "ABC", "11", "DEF" };

decimal total = 0m;
string message = "";

foreach (var value in values)
{
    decimal number; // stores the TryParse "out" value
    if (decimal.TryParse(value, out number))
    {
        total += number;
    } else
    {
        message += value;
    }
}

Console.WriteLine($"Message: {message}");
Console.WriteLine($"Total: {total}");
```

```c#
int value1 = 12;
decimal value2 = 6.2m;
float value3 = 4.3f;

// The Convert class is best for converting the fractional decimal numbers into whole integer numbers
// Convert.ToInt32() rounds up the way you would expect.
int result1 = Convert.ToInt32((decimal)value1 / value2);
Console.WriteLine($"Divide value1 by value2, display the result as an int: {result1}");

decimal result2 = value2 / (decimal)value3;
Console.WriteLine($"Divide value2 by value3, display the result as a decimal: {result2}");

float result3 = value3 / value1;
Console.WriteLine($"Divide value3 by value1, display the result as a float: {result3}");
```
