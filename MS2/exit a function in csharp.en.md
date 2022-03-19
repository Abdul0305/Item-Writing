+++
title = "Exit a Function in C#"
date = 2022-02-16
draft = false
keywords = ["Exit a Function in C#"]
description = "In this tutorial, learn the different methods of exiting a function in C# with examples. Use the break, continue, goto, return, and throw exception statements."
postlink = 2625305
inarticle = true
tags = ["Csharp", "Csharp return statement"]
author = "Abdullahi Salawudeen"

+++

This article will introduce how to exit a function in C#.

## Use the `break` statement to exit a loop in C#

Jump statements are generally used to control the flow of execution of a program. In other words, jump statements unconditionally transfer control from one point to another in the executing program. Further discussion is available via [this reference](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/statements/jump-statements).

Below are the five (5) statements categorized as Jump statements in `C#`. 

```c#
The break statement;
The continue statement;
The goto statement;
The return statement;
The throw statement;
```

The break statement is used to terminate the loop or statement in which it is present. After that, the control will pass to the statement follows the terminated statement, if available. If the break statement is present in the nested loop, then it terminates only those loops which contain the break statement. 

Below is an example of code using `break` statement.

```c#
// C# program to illustrate the
// use of break statement
using System;
 
class Test {
 
    // Main Method
    static public void Main()
    {
        int[] Numbers = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20 };
        foreach (int number in Numbers)
        {
            //print only the first 10 numbers
            if (number > 10)
            {
                break;
            }

            Console.Write($"{number} ");
        }
    }
}
```

Output:

```text
1 2 3 4 5 6 7 8 9 10
```

## Use the `continue` statement to exit a loop in C#

The `continue` statement is used to skip the execution of a block of code when a certain condition is true. Unlike the `break` statement, the `continue` statement transfers the control to the beginning of the loop.

Below is an example of code using a `foreach` method.

```c#
// C# program to illustrate the
// use of continue statement
using System;
 
class Test {
 
    // Main Method
    static public void Main()
    {
        int[] Numbers = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20 };
        foreach (int oddNumber in Numbers)
        {
            //print only the odd numbers 10 numbers
            if (oddNumber %2 == 0)
            {
                continue;
            }

            Console.Write($"{oddNumber} ");
        }
    }
}
```

Output:

```text
1 3 5 7 9 11 13 15 17 19
```

## Use `goto` statement to exit a function in C#

The `goto` statement transfers control to a labelled statement in the program. The label must be a valid identifier which must be placed before the `goto` statement. In other words, it forces the execution of the code on the label. In the example below, the `goto` statement is used to force the execution of case 5.

Below is an example of code.

```c#
// C# program to illustrate the
// use of goto statement
using System;
 
class Test {
 
    // Main Method
    static public void Main()
    {
        int age = 18;
        switch (age) {
 
        case 5:
            Console.WriteLine("5yrs is less than the recognized age for adulthood");
            break;
        case 10:
            Console.WriteLine("Age 10 is still underage");
            break;
        case 18:
            Console.WriteLine("18yrs! You are now an adult and old enough to drink");
 
            // goto statement transfer
            // the control to case 5
            goto case 5;
 
        default:
            Console.WriteLine("18yrs is the recognized age for adulthood");
            break;
        }
    }
}
```

Output:

```text
18yrs! You are now an adult and old enough to drink
5yrs is less than the recognized age for adulthood
```

## Use `return` statement to exit a function in C#

The `return` statement terminates the execution of the function in which it appears then returns control to the calling method's result, if available. However, if a function does not have a value, the `return` statement is used without expression.

Below is an example of code.

```c#
// C# program to illustrate the
// use of return statement
using System;
 
class Test {
 
    // Main Method
    static public void Main()
    {
        int[] Numbers = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20 };
        foreach (int number in Numbers)
        {
            //print only the first 10 numbers
            if (number > 10)
            {
                return;
            }
            return;

            Console.Write($"{number} ");
        }
    }
}
```

Output:

```text
No output
```

## Use `throw` statement to exit a function in C#

`Exceptions` are used to indicate that an error has occurred or alter the execution of a program. The `throw` statement creates an object of a valid `Exception class` using the `new` keyword. All `Exception` class have the `Stacktrace` and `Message` property.

Note that the valid exception must be derived from the `Exception class`. Valid `Exception` class includes `ArgumentException`, `InvalidOperationException`, `NullReferenceException` and `IndexOutOfRangeException`. Further discussion is available via [this reference](https://docs.microsoft.com/en-us/dotnet/csharp/fundamentals/exceptions/creating-and-throwing-exceptions).

Below is an example of code.



```c#
// C# program to illustrate the
// use of throw statement
using System;
 
class Test {
 
    // Main Method
    static public void Main()
    {
        int[] Numbers = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 							19, 20 };
        foreach (int number in Numbers)
        {
            // using try catch block to
			// handle the Exception
			try
			{
		
				
				//print only the first 10 numbers
            	if (number > 10)
            	{
                    Console.WriteLine();
                	throw new NullReferenceException("Number is greater than 10");
                    
            	}
                Console.Write($"{number} ");
                
			}
	
			catch(Exception exp)
			{
				Console.WriteLine(exp.Message );
                return;
			}	
        }
    }
}


```

Output:

```text
1 2 3 4 5 6 7 8 9 10 
Number is greater than 10
```

