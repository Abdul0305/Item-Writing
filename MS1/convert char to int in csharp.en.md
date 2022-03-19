+++
title = "Convert Char to int in CSharp"
date = 2021-02-05
draft = false
keywords = ["convert char to int in `csharp`"]
description = "Different methods in `CSharp` to convert `char` datatype to `int` datatype."
postlink = 3665757
inarticle = true
tags = ["`CSharp`", "`CSharp` Data type"]
author = "Abdullahi Salawudeen"

+++

Generally, high-level programming languages are either loosely typed or strongly typed. A strongly typed language mostly compiled languages on the contrary requires every variable to be properly and explicitly specified.  `C#` or `CSharp` is a strongly typed object-oriented programming language. This implies that every variable must be declared while indicating the type of values that variable is going to store.  

Variables are containers or memory allocations used to hold or store data in memory. Variables in `CSharp` can be called, manipulated, or reallocated in memory as the program executes. `CSharp` variables are stored in different forms or types called `Data types`. Further discussion is available via [this reference](https://www.w3schools.com/cs/cs_variables.php).

The size and type of variables in `C#` must be specified using `Data types`. It is advisable to explicitly declare the data type of a variable at the point of creation. This is cost-effective, error-free, and increases code maintainability. Common `CSharp` data types are `int`, `long`, `float`, and `double` for storing numbers while `char` and `string` stores alphabets and other characters. Last is the `bool` data type used to store Boolean values. The `char` data type stores a single character. The character must be enclosed in single quotes, like `'A'` or `'x'`.

Below is the code sample of how to declare a variable with `Char` data type.

```c#
type variableName = value;
char grade = 'A';
char myCharacter = 'X';
char myLuckyNumber = '3';
```

As stated earlier, variables can be manipulated in `CSharp` such that variables can be converted or transformed from one data type to another. the third example of the `char` data types may be converted to an `int` data type stored as the number 3.

## Use `Char.GetNumericValue()` method to convert `char` data type to `int` data type in `CSharp`

There is a straight and easy conversion of numeric values from `int` or `long` to `float` or `double` but it is not so for `char` or `string` data types. According to the `ASCII` table, all characters have an equivalent numeric value. A `char` data type could be converted to an `int` equivalent in the ASCII table. 

However, numeric values may be stored as `char` data type, then converted to the exact numeric value of `int` data type and not the `ASCII` equivalent.

`Char.GetNumericValue()` method is in the `System` namespace. It converts a specified numeric Unicode character to a double-precision floating-point number. If the method is applied on a `char` variable with numeric value enclosed in single quotes, that number is returned else -1 is returned. Further discussion is available via [this reference](https://docs.microsoft.com/en-us/dotnet/api/system.char.getnumericvalue?view=net-6.0#code-try-4).

Below is an example code.

```c#
using System;

public class GetNumericValue {
    public static void Main() { 
        int result = (int)Char.GetNumericValue('8');
        Console.WriteLine(result);		// Output: "8"
        
        Console.WriteLine(Char.GetNumericValue('X'));	// Output: "-1"
    }
}
```



## Use `Convert.ToInt32()` method to convert `char` data type to `int` data type in `CSharp`

Traditionally, there is a straightforward conversion of data type between `numeric` data types. Similarly, `char` and `string` data types can also be converted easily using `ToString()` and `ToCharArray()` methods.

```c#
//convert char to string
char myGrade = 'A';
string myGradeInString = myGrade.ToString();

// convert string to char
string myName = "Abdullahi Salawudeen";  
char[] myNameArray = myName.ToCharArray();  
foreach (char ch in myNameArray)  
{  
    Console.WriteLine(ch);  
}
```

Like the `Char.GetNumericValue()`, `Convert.ToInt32()` is also in the System namespace. It converts a specified value to a 32-bit signed integer. `ToInt32()` method in itself has so many variants depending on the data type of the argument passed. We will be using the `ToInt32(String)` variant. A further discussion on the `Convert.ToInt32()` method is available via [this reference](https://docs.microsoft.com/en-us/dotnet/api/system.convert.toint32?view=net-6.0).

```c#
using System;

public class ConvertCharToInt {
    public static void Main() {
        char c = '3' ;
        Console.WriteLine(Convert.ToInt32(c.ToString()));		// Output: "3"
        Console.WriteLine(Convert.ToInt32(c));		// Output: "51"
    }
}
```

**Note** that, if the `char` data type is passed as an argument into the `Convert.Tolnt32()` method, the `ASCII` equivalent is returned which is not our intention in this tutorial.

## Use `Int32.Parse()` method to convert `char` data type to `int` data type in `CSharp`

`Int32.Parse()` method is similar to the `ConvertToInt32()` method. It converts the `string` representation of a number to its 32-bit signed integer equivalent. The downside of this method is that a numeric value must be passed as the `string` argument.

To use `Int32.Parse()` method to convert a `char` data type to `int`, the `char` data type must first be converted to `string` data type. the `char` data type value **must** contain a numeric value in single quotes else the code will throw an `overflow exception`. A further discussion on the `Int32.Parse()` method is available via [this reference](https://docs.microsoft.com/en-us/dotnet/api/system.int32.parse?view=net-6.0).

Below is an illustration:

``` c#
using System;

public class GetNumericValue {
    public static void Main() {
        char c = '3';
        char s = 'x';
        string str = c.ToString();
        string ex = s.ToString();


        Console.WriteLine(Int32.Parse(str));		// Output: "8"
        //Console.WriteLine(Int32.Parse(ex));	// Output: "ThrowEx"
    }
}
```

An exception is thrown if the char value is not numeric in single quotes. Below is an illustration:

```c#
using System;

public class GetNumericValue {
    public static void Main() {
       
        char s = 'x';
        string ex = s.ToString();

        Console.WriteLine(Int32.Parse(ex));	// Output: "System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.FormatException: Input string was not in a correct format..."
    }
}
```

