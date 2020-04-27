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
