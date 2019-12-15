## Static variables

### What are static variables?

You've seen the "static" in front of some fields or methods. Like the Main() in the main entry point to a project.
Static means that the field can be accessed without creating an instance of your class.

**So using the example that we switched to of User, let's create a static field of ID:**

```csharp
class User
{
    public static int ID;
}
```

If you were to go to the Main() of your project and type:

```csharp
Console.WriteLine(User.ID); // this would print 0.
```

What if we wanted to increment the ID for every instance of the class?

```csharp
class User
{
    public static int ID;

    private string username;
    private int password;

    public string Username { get };
    public int password { set };

    public User() // remember empty constructors??
    {
        ID++;
    }

    public User(string username)
    {
        ID++;
        this.username = username;
    }
}
```

Why are static data types useful? Well, they let you share a variable across all instances of a class, and each of these classes can change the value of that fields. Each can access it and each can change it.
