---
layout: post
title: "C# Code gems #1 - Static and Generics"
date: 2012-03-16 17:52
comments: true
categories: code-gems
published: false
---
C# got it's generics support in version 2.0. While first I thought generics would be some kind of syntax sugar, which they are, and not really important for the language; now some years later I would refuse to write C# code without the power of generics.

When implementing generics in a strong typed language, the language designers have two options to implement generics. The first is a **runtime** approach, where all operations on generic types are checked by the compiler at compile time and the compiler inserts cast statements in the IL code/byte code. In pseudo code this code fragment 

{% codeblock lang:csharp %}
    List<String> strings = new List<String>();
    strings.Add("SomeString");
    String someString = strings[0];
{% endcodeblock %}

Is translated to that code fragment by the compiler:

{% codeblock lang:csharp %}
    List strings = new List();
    strings.Add((String)"SomeString");
    String someString = (String)strings[0]:
{% endcodeblock %}

The other approach to implement generics is a **compile** time approach where the compiler creates dedicated sub classes for each generic reference. That means the compiler would create a sub class of List for a `List<String>` and a `List<int>` and so on. The compiler created sub classes derive from `List<T>` but a `List<int>` cannot be assigned to a `List<String>`. More general even for class B that derives from A a `List<B>` could not be assigned to a `List<A>` reference!

C# and C++ took the **compile** time approach, Java for example took the **runtime** approach. While the **compile** time approach has some performance benefits compared to the **runtime** approach, the runtime approach is more flexible and does not lead to the awkwardness that I want to demonstrate now.

What would you expect the following code to output?

{% codeblock lang:csharp %}
public class Counter<T>
{
    private static int Count;

    public int Increase()
    {
        Count+=1;
        return Count;
    }
}

private static void IncreaseCounters()
{
    var intCounter = new Counter<int>();
    var longCounter= new Counter<long>();

    var firstCount = intCounter.Increase();
    Console.WriteLine("FirstCount {0}", firstCount);

    var secondCount = longCounter.Increase();
    Console.WriteLine("SecondCount {0}", secondCount);
}

{% endcodeblock %}

But the output is:

    FirstCount 1
    SecondCount 1
 
As stated above, the C# compiler generates two classes for the **Counter** class, one class **Counter<int>** and one **Counter<long>** class. These two classes do not share the same static **Count** field and so the consequence is that you have one **Count** field in your code but get two static fields created by the compiler.


