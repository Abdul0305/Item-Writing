title = "Sum Up an Array of Integers in C#"
date = 2021-02-05
draft = false
keywords = ["Sum Up an Array of Integers in C#"]
description = "In this tutorial, learn the different methods of summing up an array of integers in C# with examples. Use the sum(), Array.foreach, and the Enumerable.Aggregate() method."
postlink = 2419343
inarticle = true
tags = ["Csharp", "Csharp Array"]
author = "Abdullahi Salawudeen"

+++

This article will introduce how to sum up an array of integers in C#.

## Use the `sum()` method to sum up array of integers in C#

`IEnumerable` is derived from the `System.Collections.Generic` namespace. It is an interface that defines a `GetEnumerator` function. It allows a loop through a collection of classes or lists of anonymous types.

The sum() method is an extension method found in the `System.Linq` namespace. This method sums up all numeric values in an `IEnumerable` like a `list` or an array. 

The `sum()` method can be used on objects that implement `IEnumerable` with all C# numeric data types like `int`, `long`, `double`, and `decimal`. It is an optimized way of adding a collection of numbers by avoiding loops.

This method encourages fewer lines of code and possibly reduces bugs but has some overhead that makes it slower than the `for` loop.

Below is an example of code using `sum()`.

```c#
using System;
using System.Linq;
namespace MyApplication
{
  	class Program
  	
  	
  	{
    	static void Main(string[] args)
    	{
      		int[] arr = new int[] { 1, 2, 3 };
      		int sum = arr.Sum();
      		Console.WriteLine(sum);
      	}
  	}
}
```

Output:

```text
6

```

## Use the `Array.foreach` method to sum up array of integers in C#
The `foreach` statement is a neat and less complicated method of iterating through the elements. The `foreach` method processes elements of a single-dimensional array in increasing order, starting with the element at index 0 through the element at index `array.length` - 1.

A `delegate` is a type-safe and secure reference type. It is used to encapsulate a named or anonymous method. 

A delegate must be instantiated with a method or lambda expression with a compatible return type. We use the lambda expression nested in a `foreach` statement.

Below is an example of code using a `foreach` method.

```c#
using System;
namespace MyApplication
{
  	class Program
  	
  	
  	{
    	static void Main(string[] args)
    	{
      		int[] arr = new int[] { 1, 2, 3 };
      		int sum = 0;
      		Array.ForEach(arr, i => sum += i);
      		Console.WriteLine(sum);    
      	}
  	}
}
```

Output:

```text
6

```

## Use `Enumerable.Aggregate()` method to sum up array of integers in C#

The `Enumerable.Aggregate` method is present in the `System.Linq` namespace. It performs a mathematical operation on each element of a list or array while tracking or storing the previous result. 

For instance, we have to perform an addition operation on an array or list of numbers {2,4,6,8}. The `Aggregate function` adds 2 and 4, carries the result (i.e. 6) forward, adds that result with the next element (6+6), carries the result forward, then adds it with the next element(12+8). It returns the final result when the last number is processed.

Below is an example of code.

```c#
using System;
using System.Linq;
namespace MyApplication
{
   	class Program
   	
   	
  	{
     	static void Main(string[] args)
    	{
      		int[] arr = new int[] {1,2,3};
      		int sum = arr.Aggregate((total, next) => total + next);
      
      		Console.WriteLine(sum);    
      	}
  	}
  	
}
```

Output:

```text

6
```