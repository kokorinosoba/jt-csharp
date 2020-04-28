# Index
- [Index](#index)
- [C# Basic Grammar](#c-basic-grammar)
  - [Format Specifiers for string.Format](#format-specifiers-for-stringformat)
  - [Logical AND, OR and Conditional AND, OR Operators](#logical-and-or-and-conditional-and-or-operators)
  - [Multidimensional Array](#multidimensional-array)
  - [String Comparison](#string-comparison)
  - [@](#)
  - [string](#string)
- [Object Oriented Programming](#object-oriented-programming)
  - [Params keyword](#params-keyword)
  - [Class](#class)
  - [Static](#static)
  - [Static Constructors](#static-constructors)
  - [Access Modifiers](#access-modifiers)
  - [Properties](#properties)
  - [Auto-Implemented Properties](#auto-implemented-properties)
  - [Object Initializer](#object-initializer)
  - [Inheritance](#inheritance)
  - [Override](#override)
  - [This Keyword](#this-keyword)
  - [Base Keyword](#base-keyword)
- [Others](#others)
  - [Attributes](#attributes)
  - [Exception](#exception)
  - [Exception Handling](#exception-handling)
  - [Using Statement](#using-statement)
  - [Checked and Unchecked](#checked-and-unchecked)
- [Reference](#reference)

# C# Basic Grammar
## Format Specifiers for string.Format
[Standard numeric format strings | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/standard/base-types/standard-numeric-format-strings)
| Format specifier | Name                     | Description                                                                                         |
| :--------------: | :----------------------- | :-------------------------------------------------------------------------------------------------- |
|    "C" or "c"    | Currency                 | A currency value.                                                                                   |
|    "D" or "d"    | Decimal                  | Integer digits with optional negative sign.                                                         |
|    "E" or "e"    | Exponential (scientific) | Exponential notation.                                                                               |
|    "F" or "f"    | Fixed-point              | Integral and decimal digits with optional negative sign.                                            |
|    "G" or "g"    | General                  | The more compact of either fixed-point or scientific notation.                                      |
|    "N" or "n"    | Number                   | Integral and decimal digits, group separators, and a decimal separator with optional negative sign. |
|    "P" or "p"    | Percent                  | Number multiplied by 100 and displayed with a percent symbol.                                       |
|    "R" or "r"    | Round-trip               | A string that can round-trip to an identical number.                                                |
|    "X" or "x"    | Hexadecimal              | A hexadecimal string.                                                                               |

## Logical AND, OR and Conditional AND, OR Operators
[Boolean logical operators - C# reference | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/boolean-logical-operators)

The `&` operator evaluates both operands even if the left-hand operand evaluates to false.<br>
The `|` operator evaluates both operands even if the left-hand operand evaluates to true.

The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator.<br>
The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator.

If the left-hand operand of `&&` evaluates true, the right-hand operand will not evaluate.<br>
In the same way, If the left-hand operand of `||` evaluates false, the right-hand operand will not evaluate.

## Multidimensional Array
[Multidimensional Arrays - C# Programming Guide | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/arrays/multidimensional-arrays)
```cs
// Create a two-dimensional array of four rows and two columns.
int[,] array = new int[4, 2];

// With initialization
int[,] array2Da = new int[4, 2] { { 1, 2 }, { 3, 4 }, { 5, 6 }, { 7, 8 } };
// Same meaning to above
int[,] array4 = { { 1, 2 }, { 3, 4 }, { 5, 6 }, { 7, 8 } };

// Without initialization
int[,] array5;
array5 = new int[,] { { 1, 2 }, { 3, 4 }, { 5, 6 }, { 7, 8 } };   // OK
//array5 = {{1,2}, {3,4}, {5,6}, {7,8}};   // Error

// Select a particular array element
array5[2, 1] = 25;
```

## String Comparison
Two string operands are equal when both of them are null or both string instances are of the same length and have identical characters in each character position.
```cs
"String" == "string" // false
```

## @
[@ - C# Reference | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/tokens/verbatim)

1. The @ character prefixes a code element that the compiler is to interpret as an identifier rather than a C# keyword.

```cs
string[] for = { "John", "James", "Joan", "Jamie" };  // Error
string[] @for = { "John", "James", "Joan", "Jamie" }; // OK
```

2. The @ character in this instance defines a verbatim string literal.

```cs
string filename1 = @"c:\documents\files\u0066.txt";
string filename2 = "c:\\documents\\files\\u0066.txt"; // Same meaning above
```

## string
[Strings - C# Programming Guide | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/strings/)

All of the String methods and C# operators that appear to modify a string actually return the results in a new string object.

# Object Oriented Programming
## Params keyword
[params keyword for parameter arrays - C# reference | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/params)

By using the params keyword, you can specify a method parameter that takes a variable number of arguments. The parameter type must be a single-dimensional array.

No additional parameters are permitted after the params keyword in a method declaration, and only one params keyword is permitted in a method declaration.

```cs
public class MyClass
{
    public static void UseParams(params int[] list)
    {
        for (int i = 0; i < list.Length; i++)
        {
            Console.Write(list[i] + " ");
        }
        Console.WriteLine();
    }

    static void Main()
    {
        UseParams(1, 2, 3, 4); // Output: 1 2 3 4

        int[] myIntArray = { 5, 6, 7, 8, 9 };
        UseParams(myIntArray); // Output: 5 6 7 8 9
    }
}
```

## Class
[Classes - C# Programming Guide | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/classes)

A type that is defined as a class is a reference type.

[Difference Between Struct And Class In C#](https://www.c-sharpcorner.com/blogs/difference-between-struct-and-class-in-c-sharp)

Structs share many features with classes but with the following limitations as compared to classes.
- Struct cannot have a default constructor (a constructor without parameters) or a destructor.
- Structs are value types and are copied on assignment.
- Structs are value types while classes are reference types.
- Structs can be instantiated without using a new operator.
- A struct cannot inherit from another struct or class, and it cannot be the base of a class. All structs inherit directly from System.ValueType, which inherits from System.Object.
- Struct cannot be a base class. So, Struct types cannot abstract and are always implicitly sealed.
- Abstract and sealed modifiers are not allowed and struct member cannot be protected or protected internals.
- Function members in a struct cannot be abstract or virtual, and the override modifier is allowed only to the override methods inherited from System.ValueType.
- Struct does not allow the instance field declarations to include variable initializers. But, static fields of a struct are allowed to include variable initializers.
- A struct can implement interfaces.
- A struct can be used as a nullable type and can be assigned a null value.

## Static
Static fields are not constants.

```cs
class Circle
{
    public static double Pi = 3.14;
}

class Program
{
    public static void Main(string[] args)
    {
        Console.WriteLine(Circle.Pi);
        Circle.Pi = 3;
        Console.WriteLine(Circle.Pi);
    }
}
```

## Static Constructors
[Static Constructors - C# Programming Guide | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/static-constructors)

A static constructor is used to initialize any static data, or to perform a particular action that needs to be performed once only. It is called automatically before the first instance is created or any static members are referenced.

```cs
class SimpleClass
{
    // Static variable that must be initialized at run time.
    static readonly long baseline;

    // Static constructor is called at most one time, before any
    // instance constructor is invoked or member is accessed.
    static SimpleClass()
    {
        baseline = DateTime.Now.Ticks;
    }
}
```

## Access Modifiers
[Access Modifiers - C# Programming Guide | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers)
| Modifier           | Description                                                                                                                                    |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| public             | The type or member can be accessed by any other code in the same assembly or another assembly that references it.                              |
| private            | The type or member can be accessed only by code in the same class or struct.                                                                   |
| protected          | The type or member can be accessed only by code in the same class, or in a class that is derived from that class.                              |
| internal           | The type or member can be accessed by any code in the same assembly, but not from another assembly.                                            |
| protected internal | The type or member can be accessed by any code in the assembly in which it's declared, or from within a derived class in another assembly.     |
| private protected  | The type or member can be accessed only within its declaring assembly, by code in the same class or in a type that is derived from that class. |

Assembly: A file or files which contains all location and the version information of the specific programs, such as exe and dll.
In the Visual Studio, an assembly means one project.

## Properties
[Properties - C# Programming Guide | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/properties)

A property is a member that provides a flexible mechanism to read, write, or compute the value of a private field. Properties can be used as if they are public data members, but they are actually special methods called accessors.
- Properties enable a class to expose a public way of getting and setting values, while hiding implementation or verification code.
- A get property accessor is used to return the property value, and a set property accessor is used to assign a new value. These accessors can have different access levels.
- The value keyword is used to define the value being assigned by the set accessor.

```cs
public class Date
{
    private int _month = 7;  // Backing store

    public int Month
    {
        get => _month;
        set
        {
            if ((value > 0) && (value < 13))
            {
                _month = value;
            }
        }
    }
}
```

## Auto-Implemented Properties
[Auto-Implemented Properties - C# Programming Guide | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties)

In C# 3.0 and later, auto-implemented properties make property-declaration more concise when no additional logic is required in the property accessors.

```cs
class Customer
{
    // Auto-implemented properties for trivial get and set
    public double TotalPurchases { get; set; }
    public string Name { get; set; }
    public int CustomerID { get; set; }

    // Constructor
    public Customer() { }

    // .. Additional methods, events, etc.
    public int xxx() { }
}
```

## Object Initializer
[How to initialize objects by using an object initializer - C# Programming Guide | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/how-to-initialize-objects-by-using-an-object-initializer)

You can use object initializers to initialize type objects in a declarative manner without explicitly invoking a constructor for the type.

```cs
public class HowToObjectInitializers
{
    public static void Main()
    {
        // Declare a StudentName by using the constructor that has two parameters.
        StudentName student1 = new StudentName("Craig", "Playstead");

        // Make the same declaration by using an object initializer and sending
        // arguments for the first and last names. The default constructor is
        // invoked in processing this declaration, not the constructor that has
        // two parameters.
        StudentName student2 = new StudentName
        {
            FirstName = "Craig",
            LastName = "Playstead",
        };
    }
}
```

## Inheritance
[Inheritance - C# Programming Guide | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/classes-and-structs/inheritance)

Inheritance, together with encapsulation and polymorphism, is one of the three primary characteristics of object-oriented programming. Inheritance enables you to create new classes that reuse, extend, and modify the behavior defined in other classes. The class whose members are inherited is called the base class, and the class that inherits those members is called the derived class. A derived class can have only one direct base class.

"Derived Class is a Base Class".

```cs
class Car
{
    public string Name;
    public int Price;
    public void DisplayInfo()
    {
        Console.WriteLine("Name: {0}, Price: ¥{1}", Name, Price);
    }
}

class ToyCar: Car
{
    public ToyCar(string name, int price)
    {
        Name = name;
        Price = price;
    }
    public void DisplayInfo()
    {
        Console.WriteLine("ToyCar Name: {0}, Price: ¥{1}", Name, Price);
    }
}

class Program
{
    public static void Main(string[] args)
    {
        ToyCar toy = new ToyCar("Porsche", 400);
        toy.DisplayInfo();
    }
}
```

## Override
[override modifier - C# Reference | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/override)

The override modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.

An override method provides a new implementation of a member that is inherited from a base class. The method that is overridden by an override declaration is known as the overridden base method. The overridden base method must have the same signature as the override method.

You cannot override a non-virtual or static method. The overridden base method must be virtual, abstract, or override.

An override declaration cannot change the accessibility of the virtual method. Both the override method and the virtual method must have the same access level modifier.

```cs
class Car
{
    public string Name;
    public int Price;
    public virtual void DisplayInfo()
    {
        Console.WriteLine("Name: {0}, Price: ¥{1}", Name, Price);
    }
}
class ToyCar : Car
{
    public ToyCar(string name, int price)
    {
        Name = name;
        Price = price;
    }
    public override void DisplayInfo()
    {
        Console.WriteLine("ToyCar Name: {0}, Price: ¥{1}", Name, Price);
    }
}
class Program
{
    public static void Main(string[] args)
    {
        ToyCar toy = new ToyCar("Porsche", 400);
        toy.DisplayInfo();
    }
}
```

## This Keyword
[this keyword - C# Reference | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/this)

The this keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.

```cs
public class Employee
{
    private string alias;
    private string name;

    public Employee(string name, string alias)
    {
        // Use this to qualify the members of the class
        // instead of the constructor parameters.
        this.name = name;
        this.alias = alias;
    }
}
```

## Base Keyword
[base keyword - C# Reference | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/base)

The base keyword is used to access members of the base class from within a derived class:
- Call a method on the base class that has been overridden by another method.
- Specify which base-class constructor should be called when creating instances of the derived class.

```cs
public class Person
{
    protected string ssn = "444-55-6666";
    protected string name = "John L. Malgraine";

    public virtual void GetInfo()
    {
        Console.WriteLine("Name: {0}", name);
        Console.WriteLine("SSN: {0}", ssn);
    }
}
class Employee : Person
{
    public string id = "ABC567EFG";
    public override void GetInfo()
    {
        // Calling the base class GetInfo method:
        base.GetInfo();
        Console.WriteLine("Employee ID: {0}", id);
    }
}

class TestClass
{
    static void Main()
    {
        Employee E = new Employee();
        E.GetInfo();
    }
}
/*
Output
Name: John L. Malgraine
SSN: 444-55-6666
Employee ID: ABC567EFG
*/
```
# Others
## Attributes
[C# reserved attributes: Conditional, Obsolete, AttributeUsage | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/attributes/general)

These attributes can be applied to elements in your code. They add semantic meaning to those elements. The compiler uses those semantic meanings to alter its output and report possible mistakes by developers using your code.

```cs
#define TRACE_ON
using System;
using System.Diagnostics;

namespace AttributeExamples
{
    public class Trace
    {
        [Conditional("TRACE_ON")]
        public static void Msg(string msg)
        {
            Console.WriteLine(msg);
        }
    }

    public class TraceExample
    {
        public static void Main()
        {
            Trace.Msg("Now in Main...");
            Console.WriteLine("Done.");
        }
    }
}
```

If the TRACE_ON identifier isn't defined, the trace output isn't displayed. Explore for yourself in the interactive window.

## Exception
[Using Exceptions - C# Programming Guide | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/exceptions/using-exceptions)

In C#, errors in the program at run time are propagated through the program by using a mechanism called exceptions. Exceptions are thrown by code that encounters an error and caught by code that can correct the error. Exceptions can be thrown by the .NET Framework common language runtime (CLR) or by code in a program. Once an exception is thrown, it propagates up the call stack until a catch statement for the exception is found. Uncaught exceptions are handled by a generic exception handler provided by the system that displays a dialog box.

Exceptions are represented by classes derived from Exception. This class identifies the type of exception and contains properties that have details about the exception. Throwing an exception involves creating an instance of an exception-derived class, optionally configuring properties of the exception, and then throwing the object by using the throw keyword.

```cs
class CustomException : Exception
{
    public CustomException(string message)
    {
    }
}

private static void TestThrow()
{
    CustomException ex =
        new CustomException("Custom exception in TestThrow()");

    throw ex;
}
```

## Exception Handling
[Exception Handling - C# Programming Guide | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/exceptions/exception-handling)

A try block is used by C# programmers to partition code that might be affected by an exception. Associated catch blocks are used to handle any resulting exceptions. A finally block contains code that is run regardless of whether or not an exception is thrown in the try block, such as releasing resources that are allocated in the try block. A try block requires one or more associated catch blocks, or a finally block, or both.

## Using Statement
The using statement ensures that Dispose (or DisposeAsync) is called even if an exception occurs within the using block. You can achieve the same result by putting the object inside a try block and then calling Dispose (or DisposeAsync in a finally block;

```cs

string manyLines=@"This is line one
This is line two
Here is line three
The penultimate line is line four
This is the final, fifth line.";

using var reader = new StringReader(manyLines);
string? item;
do {
    item = reader.ReadLine();
    Console.WriteLine(item);
} while(item != null);

// same meaning above
var reader = new StringReader(manyLines);
try {
    string? item;
    do {
        item = reader.ReadLine();
        Console.WriteLine(item);
    } while(item != null);
} finally
{
    reader?.Dispose();
}
```

## Checked and Unchecked
[Checked and Unchecked - C# Reference | Microsoft Docs](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/checked-and-unchecked)

C# statements can execute in either checked or unchecked context. In a checked context, arithmetic overflow raises an exception. In an unchecked context, arithmetic overflow is ignored and the result is truncated by discarding any high-order bits that don't fit in the destination type.

```cs
// If the previous sum is attempted in a checked environment, an
// OverflowException error is raised.

// Checked expression.
Console.WriteLine(checked(2147483647 + ten));

// Checked block.
checked
{
    int i3 = 2147483647 + ten;
    Console.WriteLine(i3);
}
```

# Reference
1. [【C#】デバッグの手順とは？デバッガ・Debugクラスの使い方を徹底解説 | 侍エンジニア塾ブログ（Samurai Blog） - プログラミング入門者向けサイト](https://www.sejuku.net/blog/100949)
