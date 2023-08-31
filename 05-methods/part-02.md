# Create C# methods with parameters

Learning Objectives

- Learn more about using parameters
- Understand method scope
- Understand pass-by-reference and pass-by-value parameter types
- Learn how to use optional and named arguments

## Exercise - Use parameters in methods

### Add parameters to methods

```c#
CountTo(5);

void CountTo(int max) 
{
    for (int i = 0; i < max; i++)
    {
        Console.Write($"${i}, ");
    }
}
```

```c#
int[] schedule = { 800, 1200, 1600, 2000 };

void DisplayAdjustedTimes(int[] times, int currentGMT, int newGMT)
{
  int diff = 0;
  if (Math.Abs(newGMT) > 12 || Math.Abs(currentGMT) > 12)
  {
    Console.WriteLine("Invalid GMT");
  }
  else if (newGMT <= 0 && currentGMT <= 0 || newGMT >= 0 && currentGMT >= 0)
  {
    diff = 100 * (Math.Abs(newGMT) - Math.Abs(currentGMT));
  }
  else
  {
    diff = 100 * (Math.Abs(newGMT) + Math.Abs(currentGMT));
  }

  for (int i = 0; i < times.Length; i++)
  {
    int newTime = ((times[i] + diff)) % 2400;
    Console.WriteLine($"{times[i]} -> {newTime}");
  }
}

DisplayAdjustedTimes(schedule, 6, -6);
```

## Exercise - Understand method scope

### Test variable scope

```c#
string[] students = {"Jenna", "Ayesha", "Carlos", "Viktor"};

DisplayStudents(students);
DisplayStudents(new string[] {"Robert","Vanya"});

void DisplayStudents(string[] students) 
{
    foreach (string student in students) 
    {
        Console.Write($"{student}, ");
    }
    Console.WriteLine();
}
```

```c#
double pi = 3.14159;

void PrintCircleArea(int radius)
{
    double area = pi * (radius * radius);
    Console.WriteLine($"Area = {area}");
}

void PrintCircleCircumference(int radius)
{
    double circumference = 2 * pi * radius;
    Console.WriteLine($"Circumference = {circumference}");
}

PrintCircleInfo(12);
PrintCircleInfo(24);

void PrintCircleInfo(int radius) 
{
    Console.WriteLine($"Circle with radius {radius}");
    PrintCircleArea(radius);
    PrintCircleCircumference(radius);
}
```

## Exercise - Use value and reference type parameters

### Test pass by value

```c#
int a = 3;
int b = 4;
int c = 0;

Multiply(a, b, c);
Console.WriteLine($"global statement: {a} x {b} = {c}");

void Multiply(int a, int b, int c) 
{
    c = a * b;
    Console.WriteLine($"inside Multiply method: {a} x {b} = {c}");
}
```

### Test pass by reference

```c#
int[] array = {1, 2, 3, 4, 5};

PrintArray(array);
Clear(array);
PrintArray(array);

void PrintArray(int[] array) 
{
    foreach (int a in array) 
    {
        Console.Write($"{a} ");
    }
}

void Clear(int[] array) 
{
    for (int i = 0; i < array.Length; i++) 
    {
        array[i] = 0;
    }
}
```

### Test with strings

```c#
string status = "Healthy";

Console.WriteLine($"Start: {status}");
SetHealth(false);
Console.WriteLine($"End: {status}");

void SetHealth(bool isHealthy) 
{
    status = (isHealthy ? "Healthy" : "Unhealthy");
    Console.WriteLine($"Middle: {status}");
}
```

## Exercise - Methods with optional parameters

### Create an RSVP application

```c#
string[] guestList = { "Rebecca", "Nadia", "Noor", "Jonte" };
string[] rsvps = new string[10];
int count = 0;

void RSVP(string name, int partySize = 1, string allergies = "none", bool inviteOnly = true)
{
  if (inviteOnly)
  {
    if (inviteOnly)
    {
      bool found = false;
      foreach (string guest in guestList)
      {
        if (guest.Equals(name))
        {
          found = true;
          break;
        }
      }
      if (!found)
      {
        Console.WriteLine($"Sorry, {name} is not on the guest list");
        return;
      }
    }
  }

  rsvps[count] = $"Name: {name}, \tParty Size: {partySize}, \tAllergies: {allergies}";
  count++;
}

void ShowRSVPs()
{
  Console.WriteLine("\nTotal RSVPs:");
  for (int i = 0; i < count; i++)
  {
    Console.WriteLine(rsvps[i]);
  }
}


RSVP("Rebecca");
RSVP("Nadia", 2, "Nuts");
RSVP(name: "Linh", partySize: 2, inviteOnly: false);
RSVP("Tony", allergies: "Jackfruit", inviteOnly: true);
RSVP("Noor", 4, inviteOnly: false);
RSVP("Jonte", 2, "Stone fruit", false);
```

## Exercise - Complete the challenge to display email addresses

```c#
string[,] corporate = 
{
    {"Robert", "Bavin"}, {"Simon", "Bright"},
    {"Kim", "Sinclair"}, {"Aashrita", "Kamath"},
    {"Sarah", "Delucchi"}, {"Sinan", "Ali"}};

string[,] external = 
{
    {"Vinnie", "Ashton"}, {"Cody", "Dysart"},
    {"Shay", "Lawrence"}, {"Daren", "Valdes"}
};

string externalDomain = "hayworth.com";

for (int i = 0; i < corporate.GetLength(0); i++) 
{
    DisplayEmail(first: corporate[i,0], last: corporate[i,1]);
}

for (int i = 0; i < external.GetLength(0); i++) 
{
    DisplayEmail(first: external[i,0], last: external[i,1], domain: externalDomain);
}

void DisplayEmail(string first, string last, string domain = "contoso.com") 
{
    string email = first.Substring(0, 2) + last;
    email = email.ToLower();
    Console.WriteLine($"{email}@{domain}");
}
```
