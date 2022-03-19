+++
title = "Use If Statement With Multiple Conditions but Same Statement in C#"
date = 2021-02-07
draft = false
keywords = ["use if statement with multiple conditions in `csharp`"]
description = "In this tutorial, learn the different methods of using if Statement With Multiple Conditions in `CSharp` to return same statement."
postlink = 1341513
inarticle = true
tags = ["`CSharp`", "`CSharp` if statement"]
author = "Abdullahi Salawudeen"

+++

This article will introduce how to use the `if` statement with multiple conditions to return a statement in C#. 

## Use `if` statement with multiple logical conditions to return a statement in `CSharp`

Generally, conditional statements are used to control the execution or flow of a program. A statement is executed based on if a condition is true or false. Conditional statements can either be `Conditional Branching` or `Conditional Looping`.

There are two (2) conditional branching statements in `CSharp`: `IF` and `Switch` statements. Further discussion is available via [this reference](https://www.c-sharpcorner.com/UploadFile/8af593/conditional-statement-in-C-Sharp/).

The `if` statement checks whether or not a specific condition is met after executing some logical expression. `Operators` used to perform comparison and logical operations on variables and values can be categorized into `Comparison` and `Logical` operators. 

There are six (6) `comparison` operators in `C#`.

```text
<	Less than: a < b;
>	Greater than: a > b;
==	Equal to: a == b;
<=	Less than or equal to: a <= b;
>=	Greater than or equal to: a >= b;
!=	Not Equal to: a != b;
```

The `Logical` operators are three (3) in `CSharp`. The `Logical and (&&)` and `Logical or (||)` operators are used on multiple values while the `Logical not (!)` operator is commonly called a `unary` operator because it can be applied on a single value.

Below is an example code using the `if` statement with multiple logical conditions.

```c#
{
	public static void Main()  
	{
    	string a = "Abdul", b = "Salawu", c = "Stranger", A2 = "Age";
        bool checkbox = true;
    	string columnname = "Abdullahi Salawudeen";
        
        if (columnname != a && columnname != b && columnname != c
  			&& (checkbox || columnname != A2))
		{
   			Console.WriteLine("Columnname is neither equal to a nor b nor c nor A2 but the check box is checked");
		} 
        //the else statement is necessary to stop the program from executing infinitely
  		else{
        	Console.WriteLine("columnname is unknown and checkbox is false");
        }
	}
}
```

Output:

```text
Columnname is neither equal to a nor b nor c nor A2 but the check box is checked
```

### Using the `ternary conditional operator` with multiple logical conditions to return a statement

As observed with the `if` statement above, it also possible to use the `ternary` operator with multiple logical conditions.

The conditional operator `?:` also known as the `ternary conditional` operator works like an if statement. It evaluates a Boolean expression and returns the result of one of two expressions. If the Boolean expression is true, the first statement is returned (i.e. statement after the `?`) else the second statement is returned (i.e. statement after the `:`). Further discussion is available via [this reference](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/conditional-operator).

Below is the syntax.

```c#
condition ? consequent : alternative;
```



Below is the code example using the `ternary operator` with multiple logical conditions.

```c#
using System;  

class demo
{
	public static void Main()  
	{
    	string a = "Abdul", b = "Salawu", c = "Stranger", A2 = "Age";
        bool checkbox = false;
    	string columnname = A2;
         string x =(columnname != a && columnname != b && columnname != c
  			&& (checkbox || columnname != A2)) ? "Columnname is neither equal to a nor b bor c nor A2 nor is the check box true" : "columnname is unknown and checkbox is false";
            
            Console.WriteLine(x);
        
	}
} 
```

Output: 

```text
columnname is unknown and checkbox is false
```

