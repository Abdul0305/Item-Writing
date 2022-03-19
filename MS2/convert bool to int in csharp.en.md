+++
title = "Convert Boolean to Integer in C#"
date = 2022-02-16
draft = false
keywords = ["Convert Bool to Int in C#"]
description = "In this tutorial, learn the different methods of converting boolean to integer data type in C# with examples. Use the Convert.ToInt32 keyword."
postlink = 8457366
inarticle = true
tags = ["Csharp", "Csharp bool to int conversion"]
author = "Abdullahi Salawudeen"

+++

This article will introduce how to convert `Boolean` data type to `integer` in `C#`.

## Use the `ConvertToInt32` statement to convert from Boolean to integer data type in C#

Traditionally, there is no implicit conversion of data type from `boolean` to `integer`. However, the Convert.ToInt32() method converts a specified value to a 32-bit signed integer. It is worthy to mention that Convert.ToInt32() method is similar to the `int.Parse()` method but the `int.Parse()` method only accepts `string` data type as argument and throws error when a `null` is passed as argument whereas `Convert.ToInt32()` method is not affected by this limitations. Further discussion is available via [this reference](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/statements/jump-statements).

Below is an example of code using `Convert.ToInt32()` method.

```c#
// C# program to illustrate the
// use of Convert.ToInt32 statement
// and Convert.ToBoolean
using System;
 
class Test {
 
    // Main Method
    static public void Main()
    {
        bool boolinput = true;  
		int intRresult = Convert.ToInt32(boolinput); 
        bool boolRresult = Convert.ToBoolean(intRresult); 
        Console.Write("When Boolean is True, the converted integer value is: ");
        Console.WriteLine(intRresult);
        Console.Write("When integer is 1, the converted boolean value is: ");
        Console.WriteLine(boolRresult);
    }
}
```

Output:

```text
When Boolean is True, the converted integer value is: 1
When integer is 1, the converted boolean value is: True
```



Below is an example of code using `int.Parse()` method.

```c#
// C# program to illustrate the
// use of int.Parse statement
using System;
 
class Test {
 
    // Main Method
    static public void Main()
    {
        bool boolinput = true;  
		int intRresult = int.Parse(boolinput); 
        
        Console.Write("When Boolean is True, the converted integer value is: ");
        Console.WriteLine(intRresult);
        Console.Write("When integer is 1, the converted boolean value is: ");
        
    }
}
```

Output:

```text
program.cs(12,30): error CS1503: Argument 1: cannot convert from 'bool' to 'string'
```

The above error is displayed using the `int.Parse` method to convert a `Boolean` data type to `integer`. It is observed that the method is expecting a `string` as argument not a `Boolean` data type.

### Use the `Switch` statement to convert from Boolean to integer data type in C#

The `switch` statement is used to conditionally branch during the execution of a program. It decides the code block to be executed. The value of the expression is compared with the values of each `case`, If there is a match, the associated block of code is executed. The `switch` expression is evaluated once.

Below is an example of code using `switch` statement.

```c#
// C# program to illustrate the
// use of switch statement
using System;

namespace Test
{
    class Program
    {
        static void Main(string[] args)
        {
            int i = 1;
            bool b = true;
            switch (i)
            {
                case 0:
                    b = false;
                    Console.WriteLine("When integer is 0, boolean is:");
                    Console.WriteLine(b);
                    break;
                case 1:
                    b = true;
                    Console.WriteLine("When integer is 1, boolean is:");
                    Console.WriteLine(b);
                    break;
            }

            switch (b)
            {
                case true:
                    i = 1;
                    Console.WriteLine("When boolean is true, integer is:");
                    Console.WriteLine(i);
                    break;
                case false:
                    i = 0;
                    Console.WriteLine("When boolean is false, integer is:");
                    Console.WriteLine(i);
                    break;
            }
        }
    }
}
```

Output:

```text
When integer is 1, boolean is:
True
When boolean is true, integer is:
1
```



## Use the `ternary` conditional operator to convert from Boolean to integer data type in C#

The conditional operator `?:` also known as the `ternary conditional` operator is similar to the `if` statement. It evaluates a Boolean expression and returns the result of one of two expressions. If the Boolean expression is true, the first statement is returned (i.e. statement after the `?`) else the second statement is returned (i.e. statement after the `:`). Further discussion is available via [this reference](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/operators/conditional-operator).

Below is an example of code.

```c#
// C# program to illustrate the
// use of ternary operator
using System;
 
class Test {
 
    // Main Method
    static public void Main()
    {
        bool boolinput = true;          
		int intRresult = boolinput ? 1 : 0; 
        bool boolRresult = (intRresult==1) ? true : false;  
        Console.Write("When Boolean is True, the converted integer value is: ");
        Console.WriteLine(intRresult);
        Console.Write("When integer is 1, the converted boolean value is: ");
        Console.WriteLine(boolRresult);
    }
}
```

Output:

```text
When Boolean is True, the converted integer value is: 1
When integer is 1, the converted boolean value is: True
```

## Use `if` statement to convert from Boolean to integer data type in C#

The `if` statement checks whether or not a specific condition is true or false after executing some logical expression. In this scenario, whenever the expression returns `true`, the numeric value `1` is returned else, `0`. Similarly, when the numeric value is `1`, the Boolean value `true` is returned else, `false` is returned.

Below is an example of code.

```c#
// C# program to illustrate the
// use of if statement
using System;
 
class Test {
 
    // Main Method
    static public void Main()
    {
        bool boolinput = true;  
        int intResult;
        if(boolinput){
            intResult = 1;
        }else{
            intResult = 0;
        }       
	
        bool boolResult;
        if(intResult==1){
            
            boolResult = true;
        }else{
            boolResult = false;
        }         
        Console.Write("When Boolean is True, the converted integer value is: ");
        Console.WriteLine(intResult);
        Console.Write("When integer is 1, the converted boolean value is: ");
        Console.WriteLine(boolResult);
    }
}
```

Output:

```text
When Boolean is True, the converted integer value is: 1
When integer is 1, the converted boolean value is: True
```
