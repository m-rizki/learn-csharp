# Write Your First C# Method

## Intro

Learning Objectives

- Create your first c sharp method
- Identify parts of code that can be modularized
- Use methods to organize code into specific tasks

## Understand the syntax of methods

```c#
// return type is void, its mean return no data.
void SayHello();
```

```c#
void SayHello() 
{
    Console.WriteLine("Hello World!");
}
```

## Calling a method

```c#
Console.Write("Input!");
```

```c#
// Can be called before or after its definition
SayHello();

void SayHello() 
{
    Console.WriteLine("Hello World!");
}
```

```c#
int[] a = {1,2,3,4,5};

Console.WriteLine("Contents of Array:");
PrintArray();

void PrintArray()
{
    foreach (int x in a)
    {
        Console.Write($"{x} ");
    }
    Console.WriteLine();
}
```

### Method execution

```c#
Console.WriteLine("Before calling a method");
SayHello();
Console.WriteLine("After calling a method");

void SayHello() 
{
    Console.WriteLine("Hello World!");
}
```

### Best practices

```c#
void ShowData(string a, int b, int c);
void DisplayDate(string month, int day, int year);
```

## Exercise - Create your first method

```c#
Console.WriteLine("Generating random numbers:");
DisplayRandomNumbers();

void DisplayRandomNumbers() 
{
    Random random = new Random();

    for (int i = 0; i < 5; i++) 
    {
        Console.Write($"{random.Next(1, 100)} ");
    }

    Console.WriteLine();
}
```

## Exercise - Create reusable methods

```c#
int[] times = {800, 1200, 1600, 2000};
int diff = 0;

Console.WriteLine("Enter current GMT");
int currentGMT = Convert.ToInt32(Console.ReadLine());

Console.WriteLine("Current Medicine Schedule:");
DisplayTimes();

Console.WriteLine("Enter new GMT");
int newGMT = Convert.ToInt32(Console.ReadLine());

if (Math.Abs(newGMT) > 12 || Math.Abs(currentGMT) > 12)
{
    Console.WriteLine("Invalid GMT");
}
else if (newGMT <= 0 && currentGMT <= 0 || newGMT >= 0 && currentGMT >= 0) 
{
    diff = 100 * (Math.Abs(newGMT) - Math.Abs(currentGMT));
    AdjustTimes();
} 
else 
{
    diff = 100 * (Math.Abs(newGMT) + Math.Abs(currentGMT));
    AdjustTimes();
}

Console.WriteLine("New Medicine Schedule:");
DisplayTimes();

void DisplayTimes()
{
    /* Format and display medicine times */
    foreach (int val in times)
    {
        string time = val.ToString();
        int len = time.Length;

        if (len >= 3)
        {
            time = time.Insert(len - 2, ":");
        }
        else if (len == 2)
        {
            time = time.Insert(0, "0:");
        }
        else
        {
            time = time.Insert(0, "0:0");
        }

        Console.Write($"{time} ");
    }
    Console.WriteLine();
}

void AdjustTimes() 
{
    /* Adjust the times by adding the difference, keeping the value within 24 hours */
    for (int i = 0; i < times.Length; i++) 
    {
        times[i] = ((times[i] + diff)) % 2400;
    }
}

/*
Enter current GMT
-6
Current Medicine Schedule:
8:00 12:00 16:00 20:00 
Enter new GMT
+6
New Medicine Schedule:
20:00 0:00 4:00 8:00
*/
```

## Exercise - Build code with methods

```c#
string[] ipv4Input = {"107.31.1.5", "255.0.0.255", "555..0.555", "255...255"};
string[] address;
bool validLength = false;
bool validZeroes = false;
bool validRange = false;

foreach (string ip in ipv4Input) 
{
    address = ip.Split(".", StringSplitOptions.RemoveEmptyEntries);

    ValidateLength(); 
    ValidateZeroes(); 
    ValidateRange();

    if (validLength && validZeroes && validRange) 
    {
        Console.WriteLine($"{ip} is a valid IPv4 address");
    } 
    else 
    {
        Console.WriteLine($"{ip} is an invalid IPv4 address");
    }
}

void ValidateLength() 
{
    validLength = address.Length == 4;
};

void ValidateZeroes() 
{
    foreach (string number in address) 
    {
        if (number.Length > 1 && number.StartsWith("0")) 
        {
            validZeroes = false;
            return;
        }
    }

    validZeroes = true;
}

void ValidateRange() 
{
    foreach (string number in address) 
    {
        if (int.Parse(number) > 255) 
        {
            validRange = false;
            return;
        }
    }
    validRange = true;
}

/*
107.31.1.5 is a valid IPv4 address
255.0.0.255 is a valid IPv4 address
555..0.555 is an invalid IPv4 address
255...255 is an invalid IPv4 address
*/
```

## Exercise - Complete the challenge to create a reusable method

```c#
Random random = new Random();
int luck = random.Next(100);

string[] text = {"You have much to", "Today is a day to", "Whatever work you do", "This is an ideal time to"};
string[] good = {"look forward to.", "try new things!", "is likely to succeed.", "accomplish your dreams!"};
string[] bad = {"fear.", "avoid major decisions.", "may have unexpected outcomes.", "re-evaluate your life."};
string[] neutral = {"appreciate.", "enjoy time with friends.", "should align with your values.", "get in tune with nature."};

TellFortune();
luck = random.Next(100);
TellFortune();

void TellFortune() 
{
    Console.WriteLine("A fortune teller whispers the following words:");
    string[] fortune = (luck > 75 ? good : (luck < 25 ? bad : neutral));
    for (int i = 0; i < 4; i++) 
    {
        Console.Write($"{text[i]} {fortune[i]} ");
    }
}
```
