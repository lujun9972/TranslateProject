[#]: collector: (lujun9972)
[#]: translator: ( )
[#]: reviewer: ( )
[#]: publisher: ( )
[#]: url: ( )
[#]: subject: (Why I switched from Java to Kotlin)
[#]: via: (https://opensource.com/article/20/6/java-kotlin)
[#]: author: (Stephon Brown https://opensource.com/users/stephb)

Why I switched from Java to Kotlin
======
Kotlin is a cross-platform, general-purpose programming language and an
easy move for anyone familiar with Java.
![Person drinking a hot drink at the computer][1]

After [years as an educator][2], I became a professional software developer. That brought me to [Java][3], but recently, I began enjoying a totally different but compatible programming language called [Kotlin][4].

Kotlin is a cross-platform, general-purpose programming language that runs on the Java Virtual Machine (JVM). JetBrains led its implementation, which began in 2010, and it has been [open source][5] since early in its development.

The great news for Java developers is that Kotlin is interoperable with Java. Standard Java code can be included in a Kotlin program, and Kotlin can be included in a Java program. That immense investment in compatibility means if you come from a Java background, picking up Kotlin will feel familiar and be a low risk since it will run alongside any of your existing Java code.

To introduce you to Kotlin, I will go over some of its basic syntax, ranging from variables to defining functions and classes. If you want to follow along and learn some of the language's features, there is a great browser-based [Kotlin playground][6] you can use.

## Variables

Variables in Kotlin will feel familiar. Here are a few examples of creating basic integers:


```
var I = 5
val j = 7
var k:Int = 8
```

There's a subtle and important difference between `var` and `val` assignments: `var` is used when the variable you defined can be reassigned, and `val` is used for local scope values that will not be changed. Each variable's type is optional because the type can be inferred, similar to the dynamic assignment in JavaScript. There are also nullable assignments that use syntax like:


```
`var f: Int? = 9`
```

This means the assigned value can be equal to null. The [reason for using null][7] is outside the scope of this article, but it's important to know that a variable can only equal null when explicitly defined to do so.

If you plan to define a variable with no initial instantiation (value), you must place the type after the variable name:


```
`var s: Int`
```

Strings are composed similarly, with the type after the variable name:


```
`val a:String = "Hello"`
```

Strings have superpowers in Kotlin. They include awesome string template functions that you can [explore][8].

## Arrays

Another basic type is the array. It can store a pre-determined amount of objects of the same defined types. There are a few different ways to create arrays in Kotlin, such as:


```
val arrA = arrayOf(1,2,3)
val arrB = arrayOfNulls&lt;Int?&gt;(3)
val arrC = Array&lt;Int?&gt;(3){5}
```

The first creates an array with a length of three and the elements 1, 2, and 3; the second creates an array of nulls of type nullable integer; and the third creates an array of nullable integers with each of the elements equaling 5.

To retrieve one of the elements, use bracket notation, starting with zero. Therefore, to retrieve the first element in the first array, use: `arrA[0]`.

## Collections

Other ways to group objects in Kotlin are generally referred to as collections. There are a few types of collections in Kotlin. Each can either be mutable (changeable/writable) or immutable (read-only).

  * **Lists:** An ordered group of items can contain repeated items and must be of the same type. Mutable lists can be formed like this: [code] var mutList = mutableListOf(7,5,9,1)
val readList = listOf(1,3,2) 
```
  * **Maps:** Maps, similar to HashMaps in Java, are organized by keys and values. Keys must be distinct. They are instantiated like: [code] var mapMut = mutableMapOf(5 to "One", 6 to "Five" )
val mapRead = mapOf(1 to "Seven", 3 to "six")
```
  * **Sets:** Sets are a data structure where each object in the group is unique. They are created like this: [code] var setMut  = mutableSetOf(1,3, 5, 2)
val readSet = setOf(4,3,2) 
```
Whenever you try to reassign an immutable object, you will get a syntax error stating `Val cannot be reassigned`. This behavior comes in handy when you have a collection that you never want to be edited by any part of the program.

## Functions

Functions a