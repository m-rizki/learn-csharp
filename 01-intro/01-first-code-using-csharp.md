# Intro

## Write Your First C# Code

```c#
// write & write line
Console.WriteLine("This is the first line.");

Console.Write("This is ");
Console.Write("the second ");
Console.Write("line.");
```

```c#
// integer literals
Console.WriteLine(123);

// floating-point literals
/*
Float Type    Precision
----------------------------
float         ~6-9 digits
double        ~15-17 digits
decimal        28-29 digits
*/

Console.WriteLine(0.25F); // or 0.25f

Console.WriteLine(12.39816m); // m is decimal context

// boolean
Console.WriteLine(true);
```

## Store and Retrieve Data Using Literal and Variable Values in C\#

```c#
// Declare a variable
string firstName;
char userOption;
int gameScore;
decimal particlesPerMillion;
bool processedCustomer;

// variable with assignment
string firstName;
firstName = "Bob";

// Declare implicitly typed local variables
var message = "Hello world!";

// Variables using the var keyword must be initialized
var message; // (1,5): error CS0818: Implicitly-typed variables must be initialized
```

## Perform Basic String Formatting in C\#

```c#
// Character escape sequences
Console.WriteLine("Hello\nWorld!");
Console.WriteLine("Hello\tWorld!");

Console.WriteLine("Hello \"World\"!");

Console.WriteLine("c:\\source\\repos");

// Verbatim string literal
Console.WriteLine(@"    c:\source\repos    
        (this is where your code goes)");

// Format output using verbatim string literals
Console.Write(@"c:\invoices");

// Unicode escape characters
// Kon'nichiwa World
Console.WriteLine("\u3053\u3093\u306B\u3061\u306F World!");

// string concatenation
string firstName = "Bob";
string message = "Hello " + firstName;
Console.WriteLine(message);

// string interpolation
string message = $"{greeting} {firstName}!";

// Combine verbatim literals and string interpolation
string projectName = "First-Project";
Console.WriteLine($@"C:\Output\{projectName}\Data");
```

## Perform Basic Operations on Numbers in C\#

```c#
// Add two numeric values
int firstNumber = 12;
int secondNumber = 7;
Console.WriteLine(firstNumber + secondNumber);

// Mix data types to force implicit type conversions
string firstName = "Bob";
int widgetsSold = 7;
Console.WriteLine(firstName + " sold " + widgetsSold + 7 + " widgets."); // Bob sold 77 widgets.

// Add parentheses to clarify your intention to the compiler
string firstName = "Bob";
int widgetsSold = 7;
Console.WriteLine(firstName + " sold " + (widgetsSold + 7) + " widgets."); // Bob sold 14 widgets.

// Perform basic math operations
int sum = 7 + 5;
int difference = 7 - 5;
int product = 7 * 5;
int quotient = 7 / 5;

Console.WriteLine("Sum: " + sum); // Sum: 12
Console.WriteLine("Difference: " + difference); // Difference: 2
Console.WriteLine("Product: " + product); // Product: 35
Console.WriteLine("Quotient: " + quotient); // Quotient: 1

// Add code to perform division using literal decimal data
decimal decimalQuotient = 7.0m / 5;
Console.WriteLine($"Decimal quotient: {decimalQuotient}"); // Decimal quotient: 1.4

// work
decimal decimalQuotient = 7 / 5.0m;
decimal decimalQuotient = 7.0m / 5.0m;

// wont work
int decimalQuotient = 7 / 5.0m;
int decimalQuotient = 7.0m / 5;
int decimalQuotient = 7.0m / 5.0m;
decimal decimalQuotient = 7 / 5;

// Add code to perform division using literal decimal data
int first = 7;
int second = 5;
decimal quotient = (decimal)first / (decimal)second;
Console.WriteLine(quotient); // 1.4

// Write code to determine the remainder after integer division
Console.WriteLine($"Modulus of 200 / 5 : {200 % 5}"); // Modulus of 200 / 5 : 0
Console.WriteLine($"Modulus of 7 / 5 : {7 % 5}"); // Modulus of 7 / 5 : 2

// Order of operations
/*
1. Parentheses (whatever is inside the parenthesis is performed first)
2. Exponents
3. Multiplication and Division (from left to right)
4. Addition and Subtraction (from left to right)
*/

int value1 = 3 + 4 * 5;
int value2 = (3 + 4) * 5;
Console.WriteLine(value1); // 22
Console.WriteLine(value2); // 35

// Increment and decrement
int value = 0;     // value is now 0.
value = value + 5; // value is now 5.
value += 5;        // value is now 10.

int value = 0;     // value is now 0.
value = value + 1; // value is now 1.
value++;           // value is now 2.
```

## Use the increment operator before and after the value

```c#
int value = 1;
// Retrieve the current value of the variable value and use that in the string interpolation operation. then Increment the value.
value++;
// confirms that the value was, in fact, incremented.
Console.WriteLine("First: " + value); // First: 2

// Retrieve the current value of the variable value and use that in the string interpolation operation. then Increment the value.
Console.WriteLine("Second: " + value++); // Second: 2

// confirms that the value was, in fact, incremented.
Console.WriteLine("Third: " + value); // Third: 3

// Increment the value.
// Retrieve the new incremented value of the variable value and use that in the string interpolation operation.
Console.WriteLine("Fourth: " + (++value));
```

## Guided project - Calculate and print student grades

```c#
int currentAssignments = 5;

int sophia1 = 93;
int sophia2 = 87;
int sophia3 = 98;
int sophia4 = 95;
int sophia5 = 100;

int nicolas1 = 80;
int nicolas2 = 83;
int nicolas3 = 82;
int nicolas4 = 88;
int nicolas5 = 85;

int zahirah1 = 84;
int zahirah2 = 96;
int zahirah3 = 73;
int zahirah4 = 85;
int zahirah5 = 79;

int jeong1 = 90;
int jeong2 = 92;
int jeong3 = 98;
int jeong4 = 100;
int jeong5 = 97;

int sophiaSum = sophia1 + sophia2 + sophia3 + sophia4 + sophia5;
int nicolasSum = nicolas1 + nicolas2 + nicolas3 + nicolas4 + nicolas5;
int zahirahSum = zahirah1 + zahirah2 + zahirah3 + zahirah4 + zahirah5;
int jeongSum = jeong1 + jeong2 + jeong3 + jeong4 + jeong5;

decimal sophiaScore = (decimal) sophiaSum / currentAssignments;
decimal nicolasScore = (decimal) nicolasSum / currentAssignments;
decimal zahirahScore = (decimal) zahirahSum / currentAssignments;
decimal jeongScore = (decimal) jeongSum / currentAssignments;

Console.WriteLine("Student\t\tGrade\n"); // Student         Grade
Console.WriteLine("Sophia:\t\t" + sophiaScore + "\tA"); // Sophia:         94.6    A
Console.WriteLine("Nicolas:\t" + nicolasScore + "\tB"); // Nicolas:        83.6    B
Console.WriteLine("Zahirah:\t" + zahirahScore + "\tB"); // Zahirah:        83.4    B
Console.WriteLine("Jeong:\t\t" + jeongScore + "\tA"); // Jeong:          95.4    A
```

## Guided Project - Calculate Final GPA

```c#
string studentName = "Sophia Johnson";
string course1Name = "English 101";
string course2Name = "Algebra 101";
string course3Name = "Biology 101";
string course4Name = "Computer Science I";
string course5Name = "Psychology 101";

int course1Credit = 3;
int course2Credit = 3;
int course3Credit = 4;
int course4Credit = 4;
int course5Credit = 3;

int gradeA = 4;
int gradeB = 3;

int course1Grade = gradeA;
int course2Grade = gradeB;
int course3Grade = gradeB;
int course4Grade = gradeB;
int course5Grade = gradeA;

int totalCreditHours = 0;
totalCreditHours += course1Credit;
totalCreditHours += course2Credit;
totalCreditHours += course3Credit;
totalCreditHours += course4Credit;
totalCreditHours += course5Credit;

int totalGradePoints = 0;
totalGradePoints += course1Credit * course1Grade;
totalGradePoints += course2Credit * course2Grade;
totalGradePoints += course3Credit * course3Grade;
totalGradePoints += course4Credit * course4Grade;
totalGradePoints += course5Credit * course5Grade;

decimal gradePointAverage = (decimal) totalGradePoints/totalCreditHours;

int leadingDigit = (int) gradePointAverage;
int trailingDigits = (int) (gradePointAverage * 100) - (leadingDigit * 100);

Console.WriteLine($"Student: {studentName}\n"); // Student: Sophia Johnson
Console.WriteLine("Course\t\t\t\tGrade\tCredit Hours"); // Course              Grade   Credit Hours
Console.WriteLine($"{course1Name}\t\t\t{course1Grade}\t\t{course1Credit}"); // English 101         4       3
Console.WriteLine($"{course2Name}\t\t\t{course2Grade}\t\t{course2Credit}"); // Algebra 101         3       3
Console.WriteLine($"{course3Name}\t\t\t{course3Grade}\t\t{course3Credit}"); // Biology 101         3       4
Console.WriteLine($"{course4Name}\t{course4Grade}\t\t{course4Credit}"); // Computer Science I  3       4
Console.WriteLine($"{course5Name}\t\t{course5Grade}\t\t{course5Credit}"); // Psychology 101      4       3

Console.WriteLine($"\nFinal GPA:\t\t\t{leadingDigit}.{trailingDigits}"); // Final GPA:          3.35
```
