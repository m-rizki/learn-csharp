# Evaluate Boolean expressions to make decisions in C\#

## Exercise - Evaluate an expression

### equality operator

```c#
Console.WriteLine("a" == "a");
Console.WriteLine("a" == "A");
Console.WriteLine(1 == 2);

string myValue = "a";
Console.WriteLine(myValue == "a");

// this output is true
string value1 = " a";
string value2 = "A ";
Console.WriteLine(value1.Trim().ToLower() == value2.Trim().ToLower());
```

### inequality operator

```c#
Console.WriteLine("a" != "a");
Console.WriteLine("a" != "A");
Console.WriteLine(1 != 2);

string myValue = "a";
Console.WriteLine(myValue != "a");
```

### Comparison operators

```c#
Console.WriteLine(1 > 2);
Console.WriteLine(1 < 2);
Console.WriteLine(1 >= 1);
Console.WriteLine(1 <= 1);
```

### Methods that return a Boolean value

```c#
string pangram = "The quick brown fox jumps over the lazy dog.";
Console.WriteLine(pangram.Contains("fox"));
Console.WriteLine(pangram.Contains("cow"));
```

### logical negation

```c#
// These two lines of code will create the same output

Console.WriteLine(pangram.Contains("fox") == false);
Console.WriteLine(!pangram.Contains("fox"));

// Logical Negation operator
string pangram = "The quick brown fox jumps over the lazy dog.";
Console.WriteLine(!pangram.Contains("fox"));
Console.WriteLine(!pangram.Contains("cow"));
```

## Exercise - Implement the conditional operator

```c#
<evaluate this condition> ? <if condition is true, return this value> : <if condition is false, return this value>
```

```c#
int saleAmount = 1001;
int discount = saleAmount > 1000 ? 100 : 50;
Console.WriteLine($"Discount: {discount}");
```

### Use the conditional operator inline

```c#
int saleAmount = 1001;
// int discount = saleAmount > 1000 ? 100 : 50;

Console.WriteLine($"Discount: {(saleAmount > 1000 ? 100 : 50)}");
```

## Exercise - Complete a challenge activity using conditional operators

```c#
Random coin = new Random();
int flip = coin.Next(0, 2);
Console.WriteLine((flip == 0) ? "heads" : "tails");
```

```c#
Random coin = new Random();
Console.WriteLine((coin.Next(0, 2) == 0) ? "heads" : "tails");
```

## Exercise - Complete a challenge activity using Boolean expressions

```c#
string permission = "Admin|Manager";
int level = 53;

if (permission.Contains("Admin"))
{
  if (level > 55)
  {
    Console.WriteLine("Welcome, Super Admin user.");
  }
  else
  {
    Console.WriteLine("Welcome, Admin user.");
  }
}
else if (permission.Contains("Manager"))
{
  if (level >= 20)
  {
    Console.WriteLine("Contact an Admin for access.");
  }
  else
  {
    Console.WriteLine("You do not have sufficient privileges.");
  }
}
else
{
  Console.WriteLine("You do not have sufficient privileges.");
}
```
