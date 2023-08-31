# part-03 Perform operations on arrays using helper methods in C\#

## Intro

Learning objectives

- Sort and reverse the order of array elements.
- Clear and resize the elements of an array.
- Split a string into an array of strings or characters (chars).
- Join array elements into a string.

```c#
string[] pallets = { "B14", "A11", "B12", "A13" };

Console.WriteLine("Sorted...");
Array.Sort(pallets);
foreach (var pallet in pallets)
{
    Console.WriteLine($"-- {pallet}");
}

// Reversed sorted
Console.WriteLine("");
Console.WriteLine("Reversed...");
Array.Reverse(pallets);
foreach (var pallet in pallets)
{
    Console.WriteLine($"-- {pallet}");
}
```

## Exercise - Explore Clear() and Resize()

```c#
string[] pallets = { "B14", "A11", "B12", "A13" };
Console.WriteLine("");

Console.WriteLine($"Before: {pallets[0].ToLower()}"); // b14
Array.Clear(pallets, 0, 2);
// Console.WriteLine($"After: {pallets[0].ToLower()}"); // error

Console.WriteLine($"Clearing 2 ... count: {pallets.Length}");
foreach (var pallet in pallets)
{
    Console.WriteLine($"-- {pallet}");
}

Console.WriteLine(pallets[0] == null); // True
```

### Resize the array to add more elements

```c#
string[] pallets = { "B14", "A11", "B12", "A13" };
Console.WriteLine("");

Array.Clear(pallets, 0, 2);
Console.WriteLine($"Clearing 2 ... count: {pallets.Length}");
foreach (var pallet in pallets)
{
    Console.WriteLine($"-- {pallet}");
}

Console.WriteLine("");
Array.Resize(ref pallets, 6);
Console.WriteLine($"Resizing 6 ... count: {pallets.Length}");

pallets[4] = "C01";
pallets[5] = "C02";

foreach (var pallet in pallets)
{
    Console.WriteLine($"-- {pallet}");
}
```

### Resize the array to remove elements

```c#
string[] pallets = { "B14", "A11", "B12", "A13" };
Console.WriteLine("");

Array.Clear(pallets, 0, 2);
Console.WriteLine($"Clearing 2 ... count: {pallets.Length}");
foreach (var pallet in pallets)
{
    Console.WriteLine($"-- {pallet}");
}

Console.WriteLine("");
Array.Resize(ref pallets, 6);
Console.WriteLine($"Resizing 6 ... count: {pallets.Length}");

pallets[4] = "C01";
pallets[5] = "C02";

foreach (var pallet in pallets)
{
    Console.WriteLine($"-- {pallet}");
}

Console.WriteLine("");
Array.Resize(ref pallets, 3);
Console.WriteLine($"Resizing 3 ... count: {pallets.Length}");

foreach (var pallet in pallets)
{
    Console.WriteLine($"-- {pallet}");
}
```

What best describes the code Array.Clear(pallets, 0, 2); where pallets is a string array?
Array.Clear(pallets, 0, 2); removes 2 array elements starting from item 0.
Clear is a method of arrays that removes (replaces with Null) specific elements in an array.

## Exercise - Discover Split() and Join()

### Use the ToCharArray() to reverse a string

```c#
string value = "abc123";
char[] valueArray = value.ToCharArray();
Array.Reverse(valueArray);
string result = new string(valueArray);
Console.WriteLine(result); // 321cba
```

### Combine all of the chars into a new comma-separated-value string using Join()

```c#
string value = "abc123";
char[] valueArray = value.ToCharArray();
Array.Reverse(valueArray);
string result = String.Join(",", valueArray);
Console.WriteLine(result); // 3,2,1,c,b,a
```

### Split() the comma-separated-value string into an array of strings

```c#
string value = "abc123";
char[] valueArray = value.ToCharArray();
Array.Reverse(valueArray);
string result = String.Join(",", valueArray);
Console.WriteLine(result);

// Split() is used with variables of type string to create an array of strings.
string[] items = result.Split(',');
foreach (string item in items)
{
    Console.WriteLine(item);
}
```

## Exercise - Complete a challenge to reverse words in a sentence

```c#
string pangram = "The quick brown fox jumps over the lazy dog";

// Step 1
string[] message = pangram.Split(' ');

//Step 2
string[] newMessage = new string[message.Length];

// Step 3
for (int i = 0; i < message.Length; i++)
{
    char[] letters = message[i].ToCharArray();
    Array.Reverse(letters);
    newMessage[i] = new string(letters);
}

//Step 4
string result = String.Join(" ", newMessage);
Console.WriteLine(result); // ehT kciuq nworb xof spmuj revo eht yzal god
```

## Exercise - Complete a challenge to parse a string of orders, sort the orders and tag possible errors

```c#
string orderStream = "B123,C234,A345,C15,B177,G3003,C235,B179";
string[] items = orderStream.Split(',');
Array.Sort(items);

foreach (var item in items)
{
    if (item.Length == 4)
    {
        Console.WriteLine(item);
    }
    else
    {
        Console.WriteLine(item + "\t- Error");
    }
}
/*
A345
B123
B177
B179
C15     - Error
C234
C235
G3003   - Error
*/
```
