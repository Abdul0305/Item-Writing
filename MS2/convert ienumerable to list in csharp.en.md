+++
title = "Convert Ienumerable to List in C#"
date = 2022-02-14
draft = false
keywords = ["cast ienumerable to list in csharp"]
description = "In this tutorial, learn the different methods of converting IEnumerable to List in C#. Use the ToList(), ToArray(), and AsEnumerable() method"
postlink = 7617771
inarticle = true
tags = ["Csharp List", "Csharp IEnumerable"]
author = "Abdullahi Salawudeen"

+++

This article illustrates how to convert data from `IEnumerable` to `List` in `CSharp`.

## Use `ToList()` to convert data from `IEnumerable` to List in `CSharp`

`IEnumerable` is an `interface` contained in the `System.Collections.Generic` namespace. Like every other `interface`, it exposes a method. This case exposes the `enumerator method`, which supports iteration or loop through generic and non-generic lists, including `LINQ query` and `Arrays`. `IEnumerable` contains only the `GetEnumerator` method which returns an `IEnumerator` object. 

```c#
public interface IEnumerable<out T> : System.Collections.IEnumerable
```

The values returned by the `IEnumerable` interface are **read-only**. This implies that manipulation is limited on these data. An alternate method to manipulate these data is the `ToList()` method in `CSharp`. Elements in a `list` in `CSharp` can be added, removed, ordered, and re-arranged. There are so many operations that can be performed on a `list` compared to the `IEnumerable` values.e

The `C# List` class represents a collection of strongly typed objects that can be accessed by index. `ToList()` function or method is in the `System. Linq` namespace (Language-Integrate Query). In LINQ, the `ToList` operator takes the element from the given source, and it returns a new List. So, in this case, input would be converted to type List. The `ToList()` method returns a list of string instances. The `ToList()` function can be invoked on an `array` reference or `IEnumerable` values and vice versa. Further discussion is available via [this reference]([C# List Tutorial (c-sharpcorner.com)](https://www.c-sharpcorner.com/article/c-sharp-list/)).

Elements of a list can be accessed or manipulated as follows:

```c#
// an array of 4 strings
string[] animals = { "Cow", "Camel", "Elephant" }; 

//creating a new instance of a list
List<string> animalsList = new List<string>(); 

//use AddRange to add elements
animalsList.AddRange(animals);

// declaring a list and passing array elements into the list
List<string> animalsList = new List<string>(animals); 

//Adding an element to the collection
animalsList.Add("Goat"); 
Console.WriteLine(animalsList[2]); // Output Elephant, Accessing elements of a list

// Collection of new animals
string[] newAnimals = { "Sheep", "Bull", "Camel" };

// Insert array at position 3
animalsList.InsertRange(3, newAnimals);

// delete 2 elements at starting with element at position 3
animalsList.RemoveRange(3, 2);
```



To use the `To List` function, the `namespace` must be imported as follows:

```c#
using System.Collections.Generic;
using System.Linq;
```



Below is the syntax of the `ToList()` method.

```c#
List<string> result = countries.ToList();  
```



Below is an example code to convert `IEnumerable` to `List` in `CSharp`.

```c#
using System;  
using System.Collections.Generic;  
using System.Linq;

namespace TestDomain  
{  
    class Program  
    {  
        public static void Main(String[] args)  
        { 
             
            IEnumerable<int> testValues = from value in Enumerable.Range(1, 10) select value;  
            List<int> result = testValues.ToList();  
            foreach (int a in result)  
            {  
                Console.WriteLine(a);  
            }   
        }  
    }  
}
```

Output:

```text
1	
2	
3	
4	
5	
6	
7	
8	
9	
10
```



## Use `ToList()` to convert data from `Array` to List in `CSharp`

Below is an example code to convert `array` to `List` in `CSharp`.

```c#
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
  
namespace ArrayToListApp  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            //create an array of African countries of type string containing the collection of data  
            string[] countries = { "Nigeria", "Ghana", "Egypt", "Liberia", "The Gambia", "Morocco", "Senegal" };  
            //countries.ToList() convert the collection of data into the list.  
            List<string> result = countries.ToList();  
            //foreach loop is used to print the countries  
            foreach (string s in result)  
            {  
                Console.WriteLine(s);  
            }  
                
        }  
    }  
}
```

Output:

```text
Nigeria	
Ghana	
Egypt	
Liberia	
The Gambia	
Morocco 
Senegal
```



## Use `ToArray()` to convert data from `List` to Array in `CSharp`

Below is example code to convert from `List` to `array` in `CSharp`

```c#
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
  
namespace ListToArrayApp  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
			//create an array of African countries of type string containing the collection of data  
            IEnumerable<int> testValues = from value in Enumerable.Range(1, 10) select value;
             
			//countries.ToList() convert the collection of data into the list.  
            List<int> result = testValues.ToList(); 
            int[] array = result.ToArray();//convert string to array.
            //foreach loop is used to print the countries  
            foreach (int i in array)  
            {  
                Console.WriteLine(i);  
            }  
                
        }  
    }  
}
```

output:

```text
1	
2	
3	
4	
5	
6	
7	
8	
9	
10
```



## Use `AsEnumerable()` to convert data from `List` to `IEnumerable` in `CSharp`

Below is an example code to convert `IEnumerable` to `list` and back to `IEnumerable`.

```c#
using System;  
using System.Collections;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
  
namespace ListToArrayApp  
{  
    class Program  
    {  
        static void Main(string[] args) 
        {
   		    List<int> list = new List<int>();
   		    IEnumerable enumerable = Enumerable.Range(1, 5);
            
   		    foreach (int item in enumerable) {
      		    list.Add(item);
   		    }
            Console.WriteLine("Output as List");
   		    foreach (var item in list) {
      		    Console.WriteLine(item);
   		    }
            Console.WriteLine("Output as Enumerable");
            //using the AsEnumerable to	convert list back to Enumerable
   		    IEnumerable resultAsEnumerable = list.AsEnumerable(); 
   		    foreach (var item in resultAsEnumerable) {
      		    Console.WriteLine(item);
   		    }
        }
	}
     
}
```

output:

```text
Output as List
1
2
3
4
5
Output as Enumerable
1
2
3
4
5
```

