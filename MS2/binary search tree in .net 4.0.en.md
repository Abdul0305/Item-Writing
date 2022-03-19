+++
title = "Binary Search Tree in .Net 4.0"
date = 2022-03-16
draft = false
keywords = ["Binary Search Tree in .Net"]
description = "In this tutorial, understand the implementation of binary search tree in .net 4.0. Use the Sorted Set<T> class"
postlink = 3262947
inarticle = true
tags = ["Binary Search Tree in .Net", "Sorted Set"]
author = "Abdullahi Salawudeen"

+++

This article will introduce the implementation of Binary Search Tree or BST for short in `.Net 4.0`.

## Use the `SortedSet<T>` class to implement the Binary Search Tree in .Net 4.0

A `binary search tree (BST)`, commonly called `an ordered` or `sorted` binary tree is a rooted binary tree data structure. The internal nodes each store a key greater than all the keys in the node's left subtree and less than those in its right subtree. The time complexity of operations on the binary search tree is directly proportional to the height of the tree. The average complexity analysis for search, insert and delete operations take `O(log N)` for `n` nodes while the worst case takes O(n). Further discussion is available via [this reference](https://en.wikipedia.org/wiki/Binary_search_tree).





![img](C:\X\Private\Freelance\Item Writing\MS2\180px-Binary_search_tree.svg.png)

The `SortedSet` class implements the `binary search tree` in the `.net framework`, `.netcore`, `UWP`, and `Xamarin`. It is contained in the `System.Collections.Generic` namespace. Further discussion on the implementation is available via [this reference](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/statements/jump-statements).

It is implemented using a `self-balancing red-black tree`. It is used to keep the elements in sorted order, get the subset of elements in a particular range, or get the **Min** or **Max** element of the set.

Complete code implementation for the `SortedSet` class can be found via [this reference](https://github.com/dotnet/corefx/blob/master/src/System.Collections/src/System/Collections/Generic/SortedSet.cs).

Below is the code snippet of derived classes of the `SortedSet` class.

```c#
public class SortedSet<T> : System.Collections.Generic.ICollection<T>, System.Collections.Generic.IEnumerable<T>, System.Collections.Generic.IReadOnlyCollection<T>, System.Collections.Generic.IReadOnlySet<T>, System.Collections.Generic.ISet<T>, System.Collections.ICollection, System.Runtime.Serialization.IDeserializationCallback, System.Runtime.Serialization.ISerializable
```



### Using the `SortedSet` Class to Create a set of Sorted collections.

We use the `new` keyword to create an instance of a sorted array. Irrespective of how the elements are added to the array, the resulting set always returns a set of the ordered array without repeating any of the elements.

Below is a code sample.

```c#
// C# program to illustrate the
// use of SortedSet class to create
// a sorted set of elements
using System;
using System.Collections.Generic;

public class Example
{
   public static void Main()
   {
      var elements = new SortedSet<int>() { 5, 9, 2, 11, 2, 1, 4, 1, 2 };

    foreach (int element in elements)  {
    Console.Write(string.Format(" {0}", element));}
   }
}
// The example displays the following output:
//  1 2 4 5 9 11
```

Output:

```text
 1 2 4 5 9 11
```

Note that all the elements are in sorted order without repetition of 1 and 2.

### Adding element to the sorted collection.

Elements can be added to the sorted array and the returned set of elements is always sorted.

Below is an example of code.

```c 
using System;
using System.Collections.Generic;

public class Example
{
   public static void Main()
   {
      var elements = new SortedSet<int>() { 5, 9, 2, 11, 2, 1, 4, 1, 2 };

    Console.WriteLine("Sorted Set of Elements before Adding new Elements");   

    foreach (int element in elements)  {
        Console.Write(string.Format(" {0}", element));
    }
    Console.WriteLine();

    elements.Add(3);
    elements.Add(100);
    elements.Add(10);
    elements.Add(67);
    
    Console.WriteLine("Sorted Set of Elements after Adding new Elements");   
    foreach (int element in elements)  
           Console.Write(string.Format(" {0}", element)); 
   }
}
// Sorted Set of Elements before Adding new Elements
//  1 2 4 5 9 11
// Sorted Set of Elements after Adding new Elements
//  1 2 3 4 5 9 10 11 67 100
```

Output:

```text
Sorted Set of Elements before Adding new Elements
 1 2 4 5 9 11
Sorted Set of Elements after Adding new Elements
 1 2 3 4 5 9 10 11 67 100
```

Note that the final result is still in sorted order after adding different numbers into the sorted set.

### Using the `GetViewBetween` to get a range of elements in a sorted collection.

The `GetViewBetween` returns a view of a subset in a `SortedSet`. It takes two (2) parameters. The lower and upper values then return a subset view that contains only the values in the specified range. This is useful when trying to get a range of values from a larger set of elements. For example, given a set of all even numbers from 1 to 1000, we are interested in just the first ten even numbers. The `GetViewBetween` class can be used to retrieve such elements. Further discussion is available via [this reference](https://docs.microsoft.com/en-us/dotnet/api/system.collections.generic.sortedset-1.getviewbetween?view=net-6.0).

Below is an example of code.

```c
using System;
using System.Collections.Generic;

public class Example
{
   public static void Main()
   {
      var elements = new SortedSet<int>() {};
     
int counter = 0;
while (counter <= 1000)
{
    if (counter % 2 == 0)
    {
        
        elements.Add(counter);
    }
    counter++;
}


    Console.WriteLine("Even numbers between 1 and 1000");   

    foreach (int element in elements)  {
        Console.Write(string.Format(" {0}", element));
    }
    Console.WriteLine();

   
      
    // foreach (int element in elements) { 
    //        Console.Write(string.Format(" {0}", element)); }
    
    var subSet = elements.GetViewBetween(1, 100);
    Console.WriteLine();
    Console.WriteLine("Even numbers between 1 and 100");   

    foreach (int element in subSet)  
           Console.Write(string.Format(" {0}", element));
    Console.WriteLine();
    var newSubSet = elements.GetViewBetween(1, 10);
    Console.WriteLine();
    Console.WriteLine("Even numbers between 1 and 10");   

    foreach (int element in newSubSet)  
           Console.Write(string.Format(" {0}", element));
   }

    
   }

```

Output:

```text
Even numbers between 1 and 1000
 0 2 4 6 8 10 12 14 16 18 20 22 24 26 28 30 32 34 36 38 40 42 44 46 48 50 52 54 56 58 60 62 64 66 68 70 72 74 76 78 80 82 84 86 88 90 92 94 96 98 100 102 104 106 108 110 112 114 116 118 120 122 124 126 128 130 132 134 136 138 140 142 144 146 148 150 152 154 156 158 160 162 164 166 168 170 172 174 176 178 180 182 184 186 188 190 192 194 196 198 200 202 204 206 208 210 212 214 216 218 220 222 224 226 228 230 232 234 236 238 240 242 244 246 248 250 252 254 256 258 260 262 264 266 268 270 272 274 276 278 280 282 284 286 288 290 292 294 296 298 300 302 304 306 308 310 312 314 316 318 320 322 324 326 328 330 332 334 336 338 340 342 344 346 348 350 352 354 356 358 360 362 364 366 368 370 372 374 376 378 380 382 384 386 388 390 392 394 396 398 400 402 404 406 408 410 412 414 416 418 420 422 424 426 428 430 432 434 436 438 440 442 444 446 448 450 452 454 456 458 460 462 464 466 468 470 472 474 476 478 480 482 484 486 488 490 492 494 496 498 500 502 504 506 508 510 512 514 516 518 520 522 524 526 528 530 532 534 536 538 540 542 544 546 548 550 552 554 556 558 560 562 564 566 568 570 572 574 576 578 580 582 584 586 588 590 592 594 596 598 600 602 604 606 608 610 612 614 616 618 620 622 624 626 628 630 632 634 636 638 640 642 644 646 648 650 652 654 656 658 660 662 664 666 668 670 672 674 676 678 680 682 684 686 688 690 692 694 696 698 700 702 704 706 708 710 712 714 716 718 720 722 724 726 728 730 732 734 736 738 740 742 744 746 748 750 752 754 756 758 760 762 764 766 768 770 772 774 776 778 780 782 784 786 788 790 792 794 796 798 800 802 804 806 808 810 812 814 816 818 820 822 824 826 828 830 832 834 836 838 840 842 844 846 848 850 852 854 856 858 860 862 864 866 868 870 872 874 876 878 880 882 884 886 888 890 892 894 896 898 900 902 904 906 908 910 912 914 916 918 920 922 924 926 928 930 932 934 936 938 940 942 944 946 948 950 952 954 956 958 960 962 964 966 968 970 972 974 976 978 980 982 984 986 988 990 992 994 996 998 1000

Even numbers between 1 and 100
 2 4 6 8 10 12 14 16 18 20 22 24 26 28 30 32 34 36 38 40 42 44 46 48 50 52 54 56 58 60 62 64 66 68 70 72 74 76 78 80 82 84 86 88 90 92 94 96 98 100

Even numbers between 1 and 10
 2 4 6 8 10
```

Note that the final result is still in sorted order irrespective of the size of elements returned.

The subset result of the `GetViewBetween` does not allow the addition of elements outside the range specified. For instance.

```c#
newSubSet.Add(11); 
//this would throw ArgumentOutOfRangeException exception.
newSubSet.Add(1);
//this would add 1 to the set of elements since 1 is between the range of 1 and 10.
```

### Use the `RemoveWhere` class to Remove an element from the sorted collection.

As earlier explained, the `SortedSet` class represents the collection of objects in sorted order. This class comes under the `System.Collections.Generic` namespace. The predicate (`P => P % 2 == 0`) removes even elements from a given integer `SortedSet<T>`.

`RemoveWhere `method returns the total number of elements deleted from a given `SortedSet<T>`.

Below is an example of code.

```c#
using System;
using System.Collections.Generic;

public class Example
{
   public static void Main()
   {
      var elements = new SortedSet<int>() {};
     
        int counter = 1;
        while (counter <= 100)
        {
            elements.Add(counter);
            
            counter++;
        }


        Console.WriteLine("Numbers between 1 and 100");   

        foreach (int element in elements)  {
            Console.Write(string.Format(" {0}", element));
        }
        Console.WriteLine();

   
        Console.WriteLine();
        Console.WriteLine("After removing Even numbers between 1 and 100");   
        elements.RemoveWhere(P => P % 2 == 0);

        foreach (int element in elements) {
            Console.Write(string.Format(" {0}", element));
        }     
   }

    
}
```

Output:

```text
Numbers between 1 and 100
 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 49 50 51 52 53 54 55 56 57 58 59 60 61 62 63 64 65 66 67 68 69 70 71 72 73 74 75 76 77 78 79 80 81 82 83 84 85 86 87 88 89 90 91 92 93 94 95 96 97 98 99 100

After removing Even numbers between 1 and 100
 1 3 5 7 9 11 13 15 17 19 21 23 25 27 29 31 33 35 37 39 41 43 45 47 49 51 53 55 57 59 61 63 65 67 69 71 73 75 77 79 81 83 85 87 89 91 93 95 97 99
```

Other Classes under the `SortedSet` class are available via [this reference](https://www.codeproject.com/Articles/86794/SortedSet-Collection-Class-in-NET-4-0).

