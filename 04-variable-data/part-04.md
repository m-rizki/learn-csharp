# Format alphanumeric data for presentation in C\#

## Intro

Learning objectives

- Merge string templates with variables using composite formatting.
- Use various format specifiers to properly display percentages, currency, and numbers.
- Use padding methods to properly align string values to the right and left.

## Exercise - Investigate string formatting basics

```c#
string first = "Hello";
string second = "World";
string result = string.Format("{0} {1}!", first, second);
Console.WriteLine(result); // Hello World!
Console.WriteLine("{0} {0} {0}!", first, second); // Hello Hello Hello!
```

```c#
// What is string interpolation?
string first = "Hello";
string second = "World";
Console.WriteLine($"{first} {second}!"); // Hello World!
Console.WriteLine($"{second} {first}!"); // World Hello!
Console.WriteLine($"{first} {first} {first}!"); // Hello Hello Hello!
```

### Formatting currency

```c#
decimal price = 123.45m;
int discount = 50;
Console.WriteLine($"Price: {price:C} (Save {discount:C})"); // Price: $123.45 (Save $50.00)
// Notice how adding the :C to the tokens inside of the curly braces formats the number as currency regardless of whether you use int or decimal.
```

### Formatting numbers

```c#
decimal measurement = 123456.78912m;
Console.WriteLine($"Measurement: {measurement:N} units"); // Measurement: 123,456.79 units
// By default, the N numeric format specifier displays only two digits after the decimal point.

// display more precision
Console.WriteLine($"Measurement: {measurement:N4} units"); // Measurement: 123,456.7891 units
```

### Formatting percentages

```c#
decimal price = 67.55m;
decimal salePrice = 59.99m;

string yourDiscount = String.Format("You saved {0:C2} off the regular {1:C2} price. ", (price - salePrice), price);

yourDiscount += $"A discount of {((price - salePrice)/price):P2}!"; //inserted
Console.WriteLine(yourDiscount); // You saved $7.56 off the regular $67.55 price. A discount of 11.19%!
```

Which is the output of Console.WriteLine($"Tax rate: {tax:P1}");, where tax is defined by decimal tax = .12051m;?
Tax rate: 12.05 % -> tax:P1 rounds the percentage to a single decimal place.

## Exercise - Explore string interpolation

```c#
int invoiceNumber = 1201;
decimal productShares = 25.4568m;
decimal subtotal = 2750.00m;
decimal taxPercentage = .15825m;
decimal total = 3185.19m;

Console.WriteLine($"Invoice Number: {invoiceNumber}");
Console.WriteLine($"   Shares: {productShares:N3} Product");
Console.WriteLine($"     Sub Total: {subtotal:C}");
Console.WriteLine($"           Tax: {taxPercentage:P2}");
Console.WriteLine($"     Total Billed: {total:C}");
```

## Exercise - Discover padding and alignment

```c#
string paymentId = "769";
string payeeName = "Mr. Stephen Ortega";
string paymentAmount = "$5,000.00";

var formattedLine = paymentId.PadRight(6);
formattedLine += payeeName.PadRight(24);
formattedLine += paymentAmount.PadLeft(10);

Console.WriteLine("1234567890123456789012345678901234567890");
Console.WriteLine(formattedLine);

/*
1234567890123456789012345678901234567890
769   Mr. Stephen Ortega       $5,000.00
*/
```

Given string myWords = "Learning C#", what is the best output description for Console.WriteLine(myWords.PadLeft(12));?
One space is added to the start of the string. myWords is 11 characters long, adding on space completes the padding to 12.

## Exercise - Complete a challenge to apply string interpolation to a form letter

```c#
string customerName = "Ms. Barros";

string currentProduct = "Magic Yield";
int currentShares = 2975000;
decimal currentReturn = 0.1275m;
decimal currentProfit = 55000000.0m;

string newProduct = "Glorious Future";
decimal newReturn = 0.13125m;
decimal newProfit = 63000000.0m;

Console.WriteLine($"Dear {customerName},");
Console.WriteLine($"As a customer of our {currentProduct} offering we are excited to tell you about a new financial product that would dramatically increase your return.\n");
Console.WriteLine($"Currently, you own {currentShares:N} shares at a return of {currentReturn:P}.\n");
Console.WriteLine($"Our new product, {newProduct} offers a return of {newReturn:P}.  Given your current volume, your potential profit would be {newProfit:C}.\n");

Console.WriteLine("Here's a quick comparison:\n");

string comparisonMessage = "";

comparisonMessage = currentProduct.PadRight(20);
comparisonMessage += String.Format("{0:P}", currentReturn).PadRight(10);
comparisonMessage += String.Format("{0:C}", currentProfit).PadRight(20);

comparisonMessage += "\n";
comparisonMessage += newProduct.PadRight(20);
comparisonMessage += String.Format("{0:P}", newReturn).PadRight(10);
comparisonMessage += String.Format("{0:C}", newProfit).PadRight(20);

Console.WriteLine(comparisonMessage);

/*
Dear Ms. Barros,
As a customer of our Magic Yield offering we are excited to tell you about a new financial product that would dramatically increase your return.

Currently, you own 2,975,000.00 shares at a return of 12.75 %.

Our new product, Glorious Future offers a return of 13.13 %.  Given your current volume, your potential profit would be $63,000,000.00.

Here's a quick comparison:

Magic Yield         12.75 %   $55,000,000.00      
Glorious Future     13.13 %   $63,000,000.00
*/
```
