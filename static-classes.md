## Static Classes

### What are static classes?

Similiarly to static fields, you can also have static classes. Just like static fields, static classes do NOT need to be instantiated.
An example of a static class is the Console class. 

For example, when you use
```csharp
Console.WriteLine("hey there");
```
you do not need to create a new instance of a class. Therefore, the Console class is static! Cool, right?

In order to make a class static, you just create a new class file as you normally would and write "static" after public and before the class name, like so:
```csharp
public static StaticClass
{
  // everything in here
}
```

But wait. Not everything. Static classes actually do NOT require a constructor. Why? Well, because you don't need to create an instance, so you don't exactly need the constructor! Use of a static class is not dependent upon a instantiation. 

So what's the real use of them? They can be useful for storing helpful methods and actions within them. When creating these methods, you also need to use the static keyword.

**Example**
```csharp
static void MethodNameHere()
{
  // code to be run
}
```

So here's a larger example of a static class. What if we just wanted to be able to write out something in the console in a different color? Let's make a static class with this *obviously super handy method* in it.
```csharp
using System // because we need to use Console, which is part of this namespace

static class Utilities
{
  static void ColorfulWriteLine(string message, ConsoleColor color)
  {
    Console.ForegroundColor = color;
    Console.WriteLine(message);
    Console.ResetColor();
  }
}
```

Okay, cool. Now in our program, we can call this method using dot notation:
```csharp
Utilities.ColorfulWriteLine("hey there", ConsoleColor.Blue);
```

Fun Fact: ConsoleColor is an enum! See [Enumerations](../master/enums.md) if you need a refresher :wink:

### Cool, right?

