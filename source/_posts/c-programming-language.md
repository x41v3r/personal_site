---
title: "C Programming Language"
date: 2024-12-22 23:08:37
categories:
- C/Cpp
tags:
- C
---

# 1 Introduction to C

&emsp;&emsp;C is a general-purpose programming language. It has been closely associated with the UNIX system where it was developed, since both the system and most of the programs that run on it are written in C. 

```c
#include <stdio.h>  //include information about standard library

main()  //define a funcation named "main"
{  //statements of "main" are enclosed in braces
    printf("hello, world\n");
}
```

> &emsp;&emsp;A C program begins executing at the beginning of **main**. This means that every C program must have a **main** somewhere.

# 2 Types, constants and declarations

## 2.1 Variable names

There are some restrictions on the names of variables and symbolic constants:

* Names are made up of letters and digits; **the first character must be a letter**. 
* The underscore `_` counts as a letter, it is sometimes useful for **improving the readability of long variable names**. (Don't begin variable names with underscore, however, since library routines often use such names. )
* **Upper case and lower case letters are distinct**, so "x" and "X" are two different names. (Traditional C practice is to use lower case for variable names, and all upper case for symbolic constants.)

## 2.2 Data types and sizes

There are only a few basic data types in C:

|   type   |                                     description                                      |
| :------: | :----------------------------------------------------------------------------------: |
|  `char`  |   **A single byte**, capable of holding one character in the local character set.    |
|  `int`   | An integer, *typically reflecting the natural size of integers on the host machine*. |
| `float`  |                           Single-precision floating point.                           |
| `double` |                           Double-precision floating point.                           |

&emsp;&emsp;In addition, there are a number of qualifiers that can be applied to these basic types. 

`short` and `long` apply to integers:

```c
short int sh;
long int counter;
```

&emsp;&emsp;The word "int" can be omitted in such declarations, and typically is.

```c
short sh;
long counter;
```

> &emsp;&emsp;The intent is that `short` and `long` should provide different lengths of integers where practical; `int` will normally be the natural size for a particular machine.

On a 32-bit machine, `short` is often 16 bits, `long` 32 bits, and `int` either 16 or 32 bits.

On a 64-bit machine, `short` is 16 bits, `long` 64 bits, and `int` 32 bits.

...

> &emsp;&emsp;Each compiler is free to choose appropriate sizes for its own hardware, subject only to the restriction that *`short`s and `int`s are at least 16 bits, `long`s are at least 32 bits, and `short` is no longer than `int`, which is no longer than `long`*.

## 2.3 Constants

&emsp;&emsp;An integer constant like `1234` is an `int`. A `long` constant is written with a terminal `l` or `L`, as in `123456789L`; an integer too big to fit into an `int` will also be taken as a `long`. The `unsigned int` constants are written with a terminal `u` or `U`, and the suffix `ul` or `UL` indicates `unsigned long`.

```c
int a = 1234;
unsigned int ua = 1234u;

long b = 1234567890L;
unsigned long ub = 1234567890UL;
```

The value of an integer *can be specified in octal or hexadecimal instead of decimal*: A leading `0` on an integer constant means **octal**; a leading `0x` or `0X` means **hexadecimal**.  

```c
int a = 037;  // 31 in octal
int b = 0x1F;  // 31 in hexadecimal

printf("a(037) = %d\n", a);  // a(037) = 31
printf("b(0x1F) = %d\n", b);  // b(0x1F) = 31
```

&emsp;&emsp;Floating-point constants contain a decimal point (123.4) or an exponent (1e-2) or both; their type is `double`, unless suffixed. The suffixes `f` or `F` indicate a `float` constant; `l` or `L` indicate a `long double`.

```c
double d = 12.34;
float f = 12.34f;
long double ld = 12.34L;
```

&emsp;&emsp;A character constant is an integer, **written as one character within single quotes**, such as `'x'`. The value of a character constant is the numeric value of the character in the machine's character set.

```c
char c = 'x';
```

> &emsp;&emsp;For example, in the ASCII character set the character constant `'0'` has the value `48`, which is unrelated to the numeric value `0`. If we write `'0'` instead of a numeric value like `48` that depends on character set, *the program is independent of the particular value and easier to read*.

```c
char c = '0';
int ci = c;  //ci = 48 
```

## 2.4 Declarations

&emsp;&emsp;*All variables must be declared before use*, although certain declarations can be made implicitly by context.

A declaration specifies a type, and contains a list of one or more variables of that type, as in:

```c
int lower, upper, step;
char c, line[100];
```

Variables can be distributed among declarations in any fashion; the lists above could equally well be written as:

```c
int lower;
int upper;
int step;
char c;
char line[1000];
```

> &emsp;&emsp;This latter form takes more spaces, but is convenient for adding a comment to each declaration for subsequent modifications.

&emsp;&emsp;A variable may also be initialized in its declaration.

If the name is followed by an equals sign and an expression, the expression serves as an initializer, as in:

```c
char esc = '\\';
int i = 0;
int limit MAXLINE+1;
float eps = 1.0e-5;
```

# 3 Operators and expressions

## 3.1 Arithmetic operators

&emsp;&emsp;The binary arithmetic operators are `+`, `-`, `*`, `/`, and the modulus operator `%`.

Integer division truncates any fractional part.

> The direction of truncation for `/` and the sign of the result for `%` are machine-dependent for negative operands, as is the action taken on overflow or underflow.

The expression

```c
x % y
```

produces the remainder when `x` is divided by `y`, and thus is zero when `y` divides `x` exactly. 

For example, a year is a leap year if it is divisible by 4 but not by 100,except that years divisible by 400 are leap years. Therefore

```c
if ((year % 4 == 0 && year % 100 !=0) || year % 400 == 0)
    printf("%d is a leap year\n", year);
else
    printf("%d is not a leap year\n", year);
```

The `%` operator *can not be applied to `float` and `double`*.

The binary `+` and `-` operators have the same precedence, which is lower than the precedence of `*`, `/`, and `%`, which is in turn lower than unary `+` and `-`.

Arithmetic operators associate left to right.

## 3.2 Relational and logical operators

&emsp;&emsp;The relational operators are `>`, `>=`, `<` and `<=`.

They all have the same precedence. Just below them in precedence are the equality operators: `==` and `!=`.

Relational operators have lower precedence than arithmetic operators, so an expression like `i < lim-1` is taken as `i <(lim-1)`, as would be expected.

&emsp;&emsp;There are 3 relational operators: `&&`, `||` and `!`.

Expressions connected by `&&` or `||` are evaluated left to right, and *evaluation stops as soon as the truthfalsehood of the result is known*. Most C programs rely on these properties.

The precedence of `&&` is higher than that of `||`, and both are lower than relational and equality operators.

## 3.3 Type conversions



