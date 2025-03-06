---
title: Java Language Basics
date: 2025-03-03 10:31:19
categories:
- Java
tags: 
---

# 1 Creating Variables and Naming Them

## 1.1 Variables

```java
int cadence = 0;
int speed = 0;
int gear = 1;
```

The Java programming language defines the following kinds of variables:

* Instance Variables (Non-Static Fields)
* Class Variables (Static Fields)
* Local Variables
* Parameters

## 1.2 Naming Variables

# 2 Creating Primitive Type Variables

## 2.1 Primitive Types

&emsp;&emsp;The Java programming language is *statically-typed*, which means that all variables must first be declared before they can be used.

This involves stating the variable's type and name, as shown below:

```java
int gear = 1;
```

Doing so tells the program that a field named `gear` exists, holds numerical data, and has an initial value of `1`. 

&emsp;&emsp;In addition to `int`, the Java programming language supports seven other primitive data types. A primitive type is predefined by the language and is named by a reserved keyword. 

The eight primitive data types supported by the Java programming language are:

<img src="/images/java-8-primitive-datatypes.png">

&emsp;&emsp;In addition to the eight primitive data types listed above, the Java programming language also provides special support for character strings via the `java.lang.String` class.

Enclosing the character string within double quotes will automatically create a new `String` object

```java
String s = "this is a string";
```

> But in any case, the String class is not technically a primitive data type.

## 2.2 Initializing a Variable with a Default Value

&emsp;&emsp;It is not always necessary to assign a value when a field is declared. **Fields** that are declared but not initialized will be set to a reasonable default by the compiler. 

Generally speaking, this default will be **zero** or **null**, depending on the data type. However, relying on such default values, however, *is generally considered bad programming style*.

The following table summarizes the default values for the above data types.

|        Data Type         | Default Value (for fields) |
| :----------------------: | :------------------------: |
|          `byte`          |            `0`             |
|         `short`          |            `0`             |
|          `int`           |            `0`             |
|          `long`          |            `0L`            |
|         `float`          |           `0.0f`           |
|         `double`         |           `0.0d`           |
|          `char`          |          `\u0000`          |
| `String` (or any object) |           `null`           |
|        `boolean`         |          `false`           |

Local variables are slightly different; the compiler never assigns a default value to an uninitialized local variable.

If a local variable is not initialized where it is declared, we need to make sure to assign it a value before we attempt to use it. Accessing an uninitialized local variable will result in a compile-time error.

## 2.3 Creating Values with Literals

&emsp;&emsp;Primitive types are special data types **built into the language**; they are not objects created from a class. 

A literal is the **source code representation of a fixed value**; literals are represented directly in our code without requiring computation. 

As shown below, it is possible to assign a literal to a variable of a primitive type:

```java
boolean result = true;
char capitalC = 'C';
byte b = 100;
short s = 10000;
int i = 100000;
```

### 2.3.1 Integer Literals

An integer literal is of type `long` if it ends with the letter `L` or `l`; otherwise it is of type `int`.

Values of the integral types `byte`, `short`, `int`, and `long` can be created from `int` literals. Values of type `long` that exceed the range of `int` can be created from `long` literals.

```java
long l = 100;
long i1 = 12345678901;  //error
long l2 = 12345678901L;  //pass
```

Integer literals can be expressed by these number systems:

1. Decimal
2. Hexadecimal
3. Binary

```java
// The number 26, in decimal
int decimalValue = 26;

//  The number 26, in hexadecimal
int hexadecimalValue = 0x1a;

// The number 26, in binary
int binaryValue = 0b11010;
```

### 2.3.2 Floating-Point Literals

A floating-point literal is of type `float` if it ends with the letter `F` or `f`; otherwise its type is `double` and it can *optionally* end with the letter `D` or `d`.

```java
float f = 1.23456789; //error
float f = 1.23456789F; //pass
```

The floating point types (`float` and `double`) can also be expressed using `E` or `e` (for scientific notation), `F` or `f` (32-bit `float` literal) and `D` or `d` (64-bit `double` literal; this is the default and by convention is omitted).

```java
double d1 = 123.4;

// same value as d1, but in scientific notation
double d2 = 1.234e2;
float f1  = 123.4f;
```

### 2.3.3 Character and String Literals
