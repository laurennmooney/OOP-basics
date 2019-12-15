### What is a namespace:

A namespace is basically a way of structuring files in your program.

- For example, say you created the class Human, and then you created a file called like, BuildingAHuman (statring basic, okay), and you moved that class file into that folder.
- You will now add a namespace to that class of Human, like below:

```csharp
namespace BuildingAHuman
{
    class Human
    {
        public int height;
        public int weight;
    }
}
```

So basically, the namespace will be the name of the folder that the class is contained in.

In order to access the files, or classes, within a folder, or namespace, in the main program, you need to use a "using" statement at the top of the file, like so:

```csharp
using BuildingAHuman;

class Program
{
    static void Main()
    {
        Human human = new Human();
    }
}
```

By telling the program to "use" that namespace, it gives it access to all the classes that are included in that namespace. Nice, right?

Notice most files in C# have a few basic using statements included at the top, like "using System" - well the System namespace contains several classes, including the Console class. So by using System, you now have access to using all the methods in the Console class, like Console.WriteLine().

Namespaces can have subnamespaces, like of like a folder can have subfolders. So you may also see dot notation used for using statements, if a file is only using a particular subnamespace within a main namespace.

- Say we have more than just the class Human inside the BuildingAHuman namespace. What if we had a class of say, Eyes, in the BuildingAHuman namespace, and we only wanted to use that (for whatever reason), it would look like this:

```csharp
using BuildingAHuman.Eyes;
```

:boom:
