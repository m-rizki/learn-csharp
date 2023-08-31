# part-05 Modify the content of strings using built-in string data type methods in C\#

## Intro

Learning objectives

- Identify the position of a character or string inside of another string
- Extract portions of strings
- Remove portions of strings
- Replace values in strings with different values

## Exercise - Use the string's IndexOf() and Substring() helper methods

### Write code to find parenthesis pairs embedded in a string

```c#
string message = "Find what is (inside the parentheses)";

int openingPosition = message.IndexOf('(');
int closingPosition = message.IndexOf(')');

Console.WriteLine(openingPosition); // 13
Console.WriteLine(closingPosition); // 36
```

### Add code to retrieve the value between parenthesis

```c#
string message = "Find what is (inside the parentheses)";

int openingPosition = message.IndexOf('(');
int closingPosition = message.IndexOf(')');

int length = closingPosition - openingPosition;
Console.WriteLine(message.Substring(openingPosition, length)); // (inside the parentheses
```

### Modify the starting position of the sub string

```c#
string message = "Find what is (inside the parentheses)";

int openingPosition = message.IndexOf('(');
int closingPosition = message.IndexOf(')');

openingPosition += 1;

int length = closingPosition - openingPosition;
Console.WriteLine(message.Substring(openingPosition, length)); // inside the parentheses
```

```c#
string message = "What is the value <span>between the tags</span>?";

int openingPosition = message.IndexOf("<span>");
int closingPosition = message.IndexOf("</span>");

openingPosition += 6;
int length = closingPosition - openingPosition;
Console.WriteLine(message.Substring(openingPosition, length)); // between the tags
```

### Avoid magic values

```c#
string message = "What is the value <span>between the tags</span>?";

const string openSpan = "<span>";
const string closeSpan = "</span>";

int openingPosition = message.IndexOf(openSpan);
int closingPosition = message.IndexOf(closeSpan);

openingPosition += openSpan.Length;
int length = closingPosition - openingPosition;
Console.WriteLine(message.Substring(openingPosition, length)); // between the tags
```

### Recap

- IndexOf() gives you the first position of a character or string inside of another string.
- IndexOf() returns -1 if it can't find a match.
- Substring() returns just the specified portion of a string, using a starting position and optional length.
- There's often more than one way to solve a problem. You used two separate techniques to find all instances of a given character or string.
- Avoid hardcoded magic values. Instead, define a const variable. A constant variable's value can't be changed after initialization.

## Exercise - Use the string's IndexOfAny() and LastIndexOf() helper methods

```c#
string message = "(What if) I have [different symbols] but every {open symbol} needs a [matching closing symbol]?";

// The IndexOfAny() helper method requires a char array of characters. 
// You want to look for:

char[] openSymbols = { '[', '{', '(' };

// You'll use a slightly different technique for iterating through 
// the characters in the string. This time, use the closing 
// position of the previous iteration as the starting index for the 
//next open symbol. So, you need to initialize the closingPosition 
// variable to zero:

int closingPosition = 0;

while (true)
{
    int openingPosition = message.IndexOfAny(openSymbols, closingPosition);

    if (openingPosition == -1) break;

    string currentSymbol = message.Substring(openingPosition, 1);

    // Now  find the matching closing symbol
    char matchingSymbol = ' ';

    switch (currentSymbol)
    {
        case "[":
            matchingSymbol = ']';
            break;
        case "{":
            matchingSymbol = '}';
            break;
        case "(":
            matchingSymbol = ')';
            break;
    }

    // To find the closingPosition, use an overload of the IndexOf method to specify 
    // that the search for the matchingSymbol should start at the openingPosition in the string. 

    openingPosition += 1;
    closingPosition = message.IndexOf(matchingSymbol, openingPosition);

    // Finally, use the techniques you've already learned to display the sub-string:

    int length = closingPosition - openingPosition;
    Console.WriteLine(message.Substring(openingPosition, length));
}

/*
What if
different symbols
open symbol
matching closing symbol
*/
```

IndexOfAny() returns the first position of an array of char that occurs inside of another string.

## Exercise - Use the Remove() and Replace() methods

```c#
// remove
string data = "12345John Smith          5000  3  ";
string updatedData = data.Remove(5, 20);
Console.WriteLine(updatedData); // 123455000  3  

// replacce
string message = "This--is--ex-amp-le--da-ta";
message = message.Replace("--", " ");
message = message.Replace("-", "");
Console.WriteLine(message); // This is example data
```

- The Remove() method works like the Substring() method, except that it deletes the specified characters in the string.
- The Replace() method swaps all instances of a string with a new string.

## Challenge

```c#
const string input = "<div><h2>Widgets &trade;</h2><span>5000</span></div>";

string quantity = "";
string output = "";

// Your work here

// Extract the quantity
int quantityStart = input.IndexOf("<span>");
int quantityEnd = input.IndexOf("</span>");
quantityStart += "<span>".Length; // Added length of the tag so index moves to end of the tag
int quantityLength = quantityEnd - quantityStart;
quantity = input.Substring(quantityStart, quantityLength); //Extracts from end of open tag to beginning of close tag
quantity = $"Quantity: {quantity}";

// Set output to input, replacing the trademark symbol with the registered trademark symbol
output = input.Replace("&trade;", "&reg;");

// Remove the opening <div> tag
int divStart = input.IndexOf("<div>");
int divLength = "<div>".Length;
output = output.Remove(divStart, divLength);

// Remove the closing <div> tag
int divCloseStart = output.IndexOf("</div>");
int divCloseLength = "</div>".Length;
output = output.Remove(divCloseStart, divCloseLength);
output = $"Output: {output}";

Console.WriteLine(quantity);
Console.WriteLine(output);

/*
Quantity: 5000
Output: <h2>Widgets &reg;</h2><span>5000</span>
*/
```
