+++
title = "use if Statement With Multiple Conditions but Same Statement in Csharp"
date = 2021-02-07
draft = false
keywords = ["use if statement with multiple conditions in `csharp`"]
description = "Use if Statement With Multiple Conditions in `CSharp` to return same statement."
postlink = 1341513
inarticle = true
tags = ["`CSharp`", "`CSharp` conditional statement"]
author = "Abdullahi Salawudeen"

+++

`CSharp` like most programming languages supports logical conditions. These conditions can be performed on any `Boolean` expression or for different decisions in the program execution.

High-level programming languages like `Java`, `C`, `C++`, `Python`, `JavaScript`, `Ruby,` and `Perl` have conditional statements. Similarly, `C#` also has conditional statements.

```
If statement;
Switch statement;
```

## Conditional Statements

Generally, conditional statements are used to control the execution or flow of a program. A statement is executed based on if a condition is true or false. Conditional statements can either be `Conditional Branching` or `Conditional Looping`.

There are two (2) conditional branching statements in `CSharp`: `IF` and `Switch` statements. Further discussion is available via [this reference](https://www.c-sharpcorner.com/UploadFile/8af593/conditional-statement-in-C-Sharp/).

The `if` statement checks whether or not a specific condition is met.

Below is the syntax of the `if` statement in `CSharp`.

```c#

If(<Condition>)  
<statements>;  
Else if(<Condition>)  
<statements>;  
---------------------  
-----------------------  
Else  
<statements>;  
```

Below is an example code.

```c#
using System;  
class demo{
	public static void Main()  
	{  
		int a=5,b=6;  
  
  		if(a>b)  
    	{  
       		Console.WriteLine("a is greater than b");  
    	}  
  		else if(a< b)  
    	{  
      		Console.WriteLine("b is greater than a");  
    	}  
  		else   
    	{  
    		Console.WriteLine("both a and b are Equal");  
    	}   
	} 
// Output: b is greater than a
```

The `switch` statement does comparison of two (2) logical expressions, then executes the statement where the comparison returns true.

Below is the syntax of the `switch` statement in `CSharp`.

```c#
Switch(<Expression>)  
{  
Case <Value> :  
<statements>  
Break;  
-----------------------  
-------------------------  
------------------------  
Default :  
<statements>  
Break;  
}  　　
```

it is mandatory to use a `break`  after every `case` block including the `default`.

Below is an example code.

```c#
using System;  

class demo
{
	public static void Main()  
	{    
  		string colour = "Blue";  
    	switch (colour)  
    	{  
    		case "Red":  
        		Console.WriteLine("This is colour Red");  
           		break;  
    		case "Blue" :  
        		Console.WriteLine("This is colour Blue");  
          		break;  
     		case "Pink":  
        		Console.WriteLine("This is colour Pink");  
        		break;  
    		default:  
        		Console.WriteLine("The default colour is Black");  
         		break;    
  
		}  
	}
} 
// Output: This is colour Blue
```

### `Operators` in `CSharp`

`Operators` are used to perform different types of operations on variables and values in `CSharp`. `Operators` can be categorized into four categories in `CSharp`. `Arithmetic `, `Assignment`, `Comparison`, and `Logical` operators.

`Arithmetic` operators are used to perform general mathematical operations like addition, subtraction, multiplication, division, increment, and decrement. The `Arithmetic` operators in `CSharp` are `+, -, *, /, %, ++, and --`.

`Assignment` operators are used to assign values to variables in `CSharp`. The `Equal (=)` sign is basically the assignment operator but can be used in combination with the arithmetic operators. The assignment operators available in `C#` include `=, +=, -+, *=, /+, %=, and ^=`.

The `Comparison` operators allows the comparison of two values in `CSharp`. there are six (6) `comparison` operators in `C#`.

```
<	Less than: a < b;
>	Greater than: a > b;
==	Equal to: a == b;
<=	Less than or equal to: a <= b;
>=	Greater than or equal to: a >= b;
!=	Not Equal to: a != b;
```

The `Logical` operators are three (3) in `CSharp`. The `Logical and (&&)` and `Logical or (||)` operators are used on multiple values while the `Logical not (!)` operator is commonly called a `unary` operator because it can be applied on a single value.

The `Logical and (&&)` returns `true`	if two (2) compare statements are both `true` else, it returns `false`. The `Logical or (||)` returns `true`	if one (1) or both of the compared statements are `true`. It returns `false` only when both compared statements are `false`. The `Logical not (!)` negates any compare statement or argument. It returns `true` if result is `false` and vice versa.

The logical operators can be used independently or in combination with each other.

## Use `if` statement with multiple logical conditions to return a statement in `CSharp`

There is a straight and easy conversion of numeric values from `int` or `long` to `float` or `double` but it is not so for `char` or `string` data types. According to the `ASCII` table, all characters have an equivalent numeric value. A `char` data type could be converted to an `int` equivalent in the ASCII table. 

However, numeric values may be stored as `char` data type, then converted to the exact numeric value of `int` data type and not the `ASCII` equivalent.

`Char.GetNumericValue()` method is in the `System` namespace. It converts a specified numeric Unicode character to a double-precision floating-point number. If the method is applied on a `char` variable with numeric value enclosed in single quotes, that number is returned else -1 is returned. Further discussion is available via [this reference](https://docs.microsoft.com/en-us/dotnet/api/system.char.getnumericvalue?view=net-6.0#code-try-4).

Below is an example code.

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
   			Console.WriteLine("Columnname is neither equal to a nor b bor c nor A2 but the check box is checked");
		} 
        //the else statement is necessary to stop the program from executing infinitely
  		else{
        	Console.WriteLine("columnname is unknown and checkbox is false");
        }
	}
} 
// Output: Columnname is neither equal to a nor b bor c nor A2 but the check box is checked
```

### The `ternary conditional operator`

The conditional operator `?:` also known as the `ternary conditional` operator works like an if statement. It evaluates a Boolean expression and returns the result of one of two expressions. If the Boolean expression is true, the first statement is returned (i.e. statement after the `?`) else the second statement is returned (i.e. statement after the `:`). Further discussion is available via [this reference](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/conditional-operator).

Below is the synthax.

```
condition ? consequent : alternative;
```

### Using the `ternary conditional operator` with multiple logical conditions to return a statement

As observed with the `if` statement above, it also possible to use the `ternary` operator with multiple logical conditions.

Below is the code example.

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
// Output: columnname is unknown and checkbox is false
```

