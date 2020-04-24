# Format Specifiers for string.Format
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

# Logical AND, OR and Conditional AND, OR Operators

The `&` operator evaluates both operands even if the left-hand operand evaluates to false.<br>
The `|` operator evaluates both operands even if the left-hand operand evaluates to true.

The conditional logical AND operator `&&`, also known as the "short-circuiting" logical AND operator.<br>
The conditional logical OR operator `||`, also known as the "short-circuiting" logical OR operator.

If the left-hand operand of `&&` evaluates true, the right-hand operand will not evaluate.<br>
In the same way, If the left-hand operand of `||` evaluates false, the right-hand operand will not evaluate.