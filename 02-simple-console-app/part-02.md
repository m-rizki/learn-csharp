# Add decision logic to your code using `if`, `else`, and `else if` statements in C\#

## Create decision logic with if statements

### Add an if statement to display different messages based on the value of the total variable

```c#
Random dice = new Random();

int roll1 = dice.Next(1, 7);
int roll2 = dice.Next(1, 7);
int roll3 = dice.Next(1, 7);

int total = roll1 + roll2 + roll3;

Console.WriteLine($"Dice roll : {roll1} + {roll2} + {roll3} = {total}");

if (total > 14)
{
  Console.WriteLine("you win");
}

if (total < 15)
{
  Console.WriteLine("sorry, you lose");
}
```

### Boolean expression

```c#
string message = "The quick brown fox jumps over the lazy dog.";

bool result = message.Contains("dog"); // true

Console.WriteLine(result);

if (message.Contains("fox"))
{
  Console.WriteLine("What does the fox say?");
}
```

Boolean expressions can be created by using operators to compare two values.

- `==`, the "equals" operator, to test for equality
- `>`, the "greater than" operator, to test that the value on the left is greater than the value on the right
- `<`, the "less than" operator, to test that the value on the left is less than the value on the right
- `>=`, the "greater than or equal to" operator
- `<=`, the "less than or equal to" operator
- and so on

### Add another if statement to implement the doubles bonus

### Add another if statement to implement the triples bonus

```c#
Random dice = new Random();

int roll1 = dice.Next(1, 7);
int roll2 = dice.Next(1, 7);
int roll3 = dice.Next(1, 7);

int total = roll1 + roll2 + roll3;

Console.WriteLine($"Dice roll: {roll1} + {roll2} + {roll3} = {total}");

if ((roll1 == roll2) || (roll2 == roll3) || (roll1 == roll3))
{
    Console.WriteLine("You rolled doubles! +2 bonus to total!");
    total += 2;
}

if ((roll1 == roll2) && (roll2 == roll3)) 
{
    Console.WriteLine("You rolled triples! +6 bonus to total!");
    total += 6;
}

if (total >= 15)
{
    Console.WriteLine("You win!");
}

if (total < 15)
{
    Console.WriteLine("Sorry, you lose.");
}
```

## Create nested decision logic with if, else if, and else

### Use if and else statements instead of two separate if statements

### Modify the code to remove the stacking bonus for doubles and triples using nesting

### Use if, else, and else if statements to give a prize instead of a win-lose message

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
    Console.WriteLine("You rolled triples! +6 bonus to total!");
    total += 6;
  }
  else
  {
    Console.WriteLine("You rolled doubles! +2 bonus to total!");
    total += 2;
  }
}

if (total >= 16)
{
  Console.WriteLine("Win a new car.");
}
else if (total >= 10)
{
  Console.WriteLine("Win a new Laptop");
}
else if (total == 7)
{
  Console.WriteLine("Win a Trip");
}
else
{
  Console.WriteLine("Win a kitten");
}
```

## Complete a challenge activity to apply business rules

```c#
// See https://aka.ms/new-console-template for more information
Random random = new Random();

int daysUntilExpiration = random.Next(12);
int discountPercentage = 0;

if (daysUntilExpiration == 0)
{
  Console.WriteLine("Your subscription has expired.");
}
else if (daysUntilExpiration == 1)
{
  Console.WriteLine("Your subscription expires within a day!");
  discountPercentage = 20;
}
else if (daysUntilExpiration < -5)
{
  Console.WriteLine($"Your subscription expires in {daysUntilExpiration} days.");
  discountPercentage = 10;
}
else if (daysUntilExpiration <= 10)
{
  Console.WriteLine("Your subscription will expire soon. Renew now!");
}

if(discountPercentage > 0) {
  Console.WriteLine($"Renew now and save {discountPercentage}%.");
}
```

## knowlege check

An else statement can't be placed before an else if statement.
