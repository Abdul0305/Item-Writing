+++
title = "sum an Array of Integers in Csharp"
date = 2021-02-05
draft = false
keywords = ["sum Array of Integers in `csharp`"]
description = "methods of summing array of integers in `CSharp` ."
postlink = 2419343
inarticle = true
tags = ["`CSharp`", "`CSharp` Array"]
author = "Abdullahi Salawudeen"

+++

`C#` or `CSharp` is a strongly typed object-oriented programming language. This implies that every variable must be declared while indicating the type of values that variable is going to store. 

## `C#` Arrays

Generally, variables in programming languages are containers or memory allocations, or memory holders used to hold or store data in memory. Similarly, in `CSharp`, variables are used to store data values which can be called, manipulated, or reallocated in memory as the program executes. `CSharp` variables are stored in different forms or types called `Data types`. 

However, a variable can be used to store multiple values of the same `data type`. An `array` is an unordered sequence of elements used in `CSharp` and other high-level programming languages to store multiple values in a single variable. It makes it easy to manipulate data with less code. It could also be used to represent data structures like `lists`, `trees`, `stacks`, and `queues`. Since `CSharp` is strongly typed, runtime errors would be avoided and performance is faster with Arrays. Further discussion is available via [this reference](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/arrays/).

Although there are so many advantages of using Arrays in `CSharp`, there are also limitations such as the size of an array which is fixed the moment it is created. Data manipulation in `arrays` is also limited when it comes to inserting or deleting an element in the middle of an `array`. These limitations birthed `Collections` in `CSharp`. Further discussion is available via [this reference](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/arrays/).

`Arrays` are derived from the base class `System. Array` and can be single-dimensional, multidimensional, or jagged. The number of dimensions is established when the array instance is created.

To declare an `array` in `CSharp` is similar to how variables are declared except with the square brackets []. `Arrays` are declared by specifying the data type of its elements with **square brackets** then the `arrayName`.

Below is the syntax of declaring arrays in `CSharp`.

```c#
type[] arrayName;
// Declare a single-dimensional array of 2 strings.
string[] array1 = new string[2];
array1 = {"Abdullahi","Salawudeen"};

// Declare and initialize array element values.
int[] array2 = new int[] { 1, 3, 5, 7, 9 };

char[] array3 = { 'A', 'B', 'C', 'D', 'E', 'F' };

// Declare a two dimensional array.
int[,] multiDimensionalArray1 = new int[2, 3];

 // Declare and set array element values.
int[,] multiDimensionalArray2 = { { 1, 2, 3 }, { 4, 5, 6 } };
```

where type could be any of `CSharp` data types including `char`, `string`, `int`, and `bool`.

## `Array` Manipulations in `CSharp`

`Array class` is a class defined in the `System` namespace. It is the base class for all arrays in `CSharp`. `Array class` provides the `CreateInstance` to construct an array. The `Array class` has so many properties for creating, manipulating, searching, and sorting arrays in `CSharp`.  Examples of methods provided by the `Array class` include `CreateInstance`, `Copy`, `CopyTo`, `GetValue`, and `SetValue`. `Array` elements are accessed by name using an integer index which starts with zero (0).

Below is a code example of accessing elements of an array.

```c#
int[] myArr = {2,3,4,5,6,7,8};
int[] newArr = {10,13,14,15,16};
myArr[3] = 5;
myArr[5] = 7;
// Copies the first two elements from myArr to newArr.
        System.Array.Copy(myArr, newArr, 2);
Console.Write("newArr: ");
        PrintValues(newArr);
/*
This code produces the following output.

Initially,

newArr:   2      2      14      15      16
*/
```



## Use `sum()` method to sum array of integers in `CSharp`

`IEnumerable` is derived from the `System.Collections.Generic` namespace. It is an interface that defines a `GetEnumerator` function. It allows a loop through a collection of classes or lists of anonymous types.

The sum() method is an extension method found in the `System.Linq` namespace. This method sums up all numeric values in an `IEnumerable` like a `List` or an `array`.  It can be used on objects that implement  `IEnumerable` with all `CSharp` numeric data types like `int`, `long`, `double,` and `decimal`.  This is an optimized way of adding a collection of numbers by avoiding loops. This method encourages fewer lines of code and possibly reduces bugs but has some overhead that makes it slower than the for-loop.

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

/*
This code produces the following output.
6
*/
```

## Use `Array.foreach` method to sum array of integers in `CSharp`

The `foreach` statement is a neat and less complicated method of iterating through the elements of an `array`. `foreach` method processes elements of a single-dimensional array in increasing order, starting with the element at index 0 through the element at index `array.length` - 1.

A `delegate` is a type-safe and secure reference type. It is used to encapsulate a named or anonymous method. A delegate must be instantiated with a method or lambda expression that has a compatible return type. We use the lambda expression nested in a `foreach` statement.

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

/*
This code produces the following output.
6
*/
```

## Use `Enumerable.Aggregate()` method to sum array of integers in `CSharp`

The `Enumerable.Aggregate` method is present in the `System.Linq` namespace. It performs mathematical operation on each element of a list or array while tracking or storing the previous operation. For instance, we have perform an addition operation on an array or list of numbers { 2, 4, 6, 8}. The `Aggregate function` adds 2 and 4, carries the result (i.e. 6) forward, adds that result with the next element (6 + 6), carries the result forward, then add it with the next element(12 + 8) then returns the final result when the last element is processed.

Below is an example of code .

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
      int sum = arr.Aggregate((total, next) => total + next);
      
      Console.WriteLine(sum);
    }
  }
}

/*
This code produces the following output.
6
*/
```

