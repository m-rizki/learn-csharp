# part-4 Create readable code with conventions, whitespace, and comments in C\#

## Choose variable names that follow rules and conventions

### Variable name rules

- Variable names can contain alphanumeric characters and the underscore character. Special characters like the pound `#`, the dash `-`, and the dollar sign `$` are not allowed.
- Variable names must begin with an alphabetical letter or an underscore, not a number. Developers use the underscore for a special purpose, so try to not use that for now.
- Variable names must NOT be a C# keyword. For example, these variable name declarations won't be allowed: `float float;` or `string string;`.
- Variable names are case-sensitive, meaning that `string MyValue;` and `string myValue;` are two different variables.

### Variable name conventions

- Variable names should use camel case, which is a style of writing that uses a lower-case letter at the beginning of the first word and an upper-case letter at the beginning of each subsequent word. >For example: `string thisIsCamelCase;`.
- Variable names should be descriptive and meaningful in your application. You should choose a name for your variable that represents the kind of data it will hold (not the data type). >For example: `bool orderComplete;`, NOT `bool isComplete;`.
- Variable names should be one or more entire words appended together. Don't use contractions because the name of the variable may be unclear to others who are reading your code. >For example: `decimal orderAmount;`, NOT `decimal odrAmt;`.
- Variable names shouldn't include the data type of the variable. You might see some advice to use a style like `string strMyValue;`. It was a popular style years ago. However, most developers don't follow this advice anymore and there are good reasons not to use it.

### Variable name examples

```c#
char userOption;
int gameScore;
float particlesPerMillion;
bool processedCustomer;
```

## Exercise - Create effective code comments

```c#
// This is a code comment!

/*
block comment
that comments out
multiple lines
*/
```

```c#
/*
  The following code creates five random OrderIDs
  to test the fraud detection process.  OrderIDs 
  consist of a letter from A to E, and a three
  digit number. Ex. A123.
*/
Random random = new Random();
string[] orderIDs = new string[5];

for (int i = 0; i < orderIDs.Length; i++)
{
    int prefixValue = random.Next(65, 70);
    string prefix = Convert.ToChar(prefixValue).ToString();
    string suffix = random.Next(1, 1000).ToString("000");

    orderIDs[i] = prefix + suffix;
}

foreach (var orderID in orderIDs)
{
    Console.WriteLine(orderID);
}
```

## Exercise - Use whitespace to make your code easier to read

The `{` and `}` symbols create code blocks. Many C# constructs require code blocks. These symbols should be placed on a separate line so that their boundaries are clearly visible and readable.

```c#
Random dice = new Random();

int roll1 = dice.Next(1, 7);
int roll2 = dice.Next(1, 7);
int roll3 = dice.Next(1, 7);

int total = roll1 + roll2 + roll3;
Console.WriteLine($"Dice roll: {roll1} + {roll2} + {roll3} = {total}");

if ((roll1 == roll2) || (roll2 == roll3) || (roll1 == roll3)) 
{
    if ((roll1 == roll2) && (roll2 == roll3)) 
    {
        Console.WriteLine("You rolled triples!  +6 bonus to total!");
        total += 6; 
    } 
    else 
    {
        Console.WriteLine("You rolled doubles!  +2 bonus to total!");
        total += 2;
    }
}
```

## improve code readability challenge activity

```c#
string str = "The quick brown fox jumps over the lazy dog.";
// convert the message into a char array
char[] charMessage = str.ToCharArray();
// Reverse the chars
Array.Reverse(charMessage);
int x = 0;
// count the o's
foreach (char i in charMessage) { if (i == 'o') { x++; } }
// convert it back to a string
string new_message = new String(charMessage);
// print it out
Console.WriteLine(new_message);
Console.WriteLine($"'o' appears {x} times.");
```

```c#
/*
   This code reverses a message, counts the number of times 
   a particular character appears, then prints the results
   to the console window.
 */

string originalMessage = "The quick brown fox jumps over the lazy dog.";

char[] message = originalMessage.ToCharArray();
Array.Reverse(message);

int letterCount = 0;

foreach (char letter in message)
{
    if (letter == 'o')
    {
        letterCount++;
    }
}

string newMessage = new String(message);

Console.WriteLine(newMessage);
Console.WriteLine($"'o' appears {letterCount} times.");
```
