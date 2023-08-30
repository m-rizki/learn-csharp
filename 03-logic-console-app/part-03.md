# Branch the flow of code using the switch-case construct in C\#

## Learning objectives

- Use the switch-case construct to match a variable or expression against several possible outcomes.
- Convert code that uses an if-elseif-else construct into a switch-case construct.

## Exercise - Implement a switch statement

### How does a switch statement work?

```c#
switch (fruit)
{
    case "apple":
        Console.WriteLine($"App will display information for apple.");
        break;

    case "banana":
        Console.WriteLine($"App will display information for banana.");
        break;

    case "cherry":
        Console.WriteLine($"App will display information for cherry.");
        break;
}
```

```c#
int employeeLevel = 100;
string employeeName = "John Smith";

string title = "";

switch (employeeLevel)
{
    case 100:
    case 200:
        title = "Senior Associate";
        break;
    case 300:
        title = "Manager";
        break;
    case 400:
        title = "Senior Manager";
        break;
    default:
        title = "Associate";
        break;
}

Console.WriteLine($"{employeeName}, {title}");
```

## Exercise - Complete a challenge activity using switch statements

```c#
// SKU = Stock Keeping Unit
string sku = "01-MN-L";

string[] product = sku.Split('-');

string type = "";
string color = "";
string size = "";

switch (product[0])
{
    case "01":
        type = "Sweat shirt";
        break;
    case "02":
        type = "T-Shirt";
        break;
    case "03":
        type = "Sweat pants";
        break;
    default:
        type = "Other";
        break;
}

switch (product[1])
{
    case "BL":
        color = "Black";
        break;
    case "MN":
        color = "Maroon";
        break;
    default:
        color = "White";
        break;
}

switch (product[2])
{
    case "S":
        size = "Small";
        break;
    case "M":
        size = "Medium";
        break;
    case "L":
        size = "Large";
        break;
    default:
        size = "One Size Fits All";
        break;
}

Console.WriteLine($"Product: {size} {color} {type}");
```

```c#
// functional proramming paradigm
// SKU = Stock Keeping Unit
string sku = "01-MN-L";

string[] product = sku.Split('-');

string type = "";
string color = "";
string size = "";

type = product[0] switch
{
    "01" => "Sweat shirt",
    "02" => "T-Shirt",
    "03" => "Sweat pants",
    _ => "Other",
};

color = product[1] switch
{
    "BL" => "Black",
    "MN" => "Maroon",
    _ => "White",
};

size = product[2] switch
{
    "S" => "Small",
    "M" => "Medium",
    "L" => "Large",
    _ => "One Size Fits All",
};

Console.WriteLine($"Product: {size} {color} {type}");
```
