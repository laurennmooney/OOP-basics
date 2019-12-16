## Static variables

### What are static variables?

You've seen the "static" in front of some fields or methods. Like the Main() in the main entry point to a project.
Static means that the field can be accessed without creating an instance of your class.

**So using the example that we switched to of User, let's create a static field of ID:**

```csharp
class User
{
    public static int id;
}
```

If you were to go to the Main() of your project and type:

```csharp
Console.WriteLine(User.id); // this would print 0.
```

What if we wanted to increment the id for every instance of the class?

```csharp
class User
{
    public static int id;

    private string username;
    private int password;

    public string Username { get };
    public int password { set };

    public User() // remember empty constructors??
    {
        id++;
    }

    public User(string username)
    {
        id++;
        this.username = username;
    }
}
```

In the above example, this will assign an id to every instance of the class User, and it will increment with each instance. However, since id is a static field, you can access the field without having an actual instance. Make sense?

Why are static data types useful? Well, they let you share a variable across all instances of a class, and each of these classes can change the value of that fields. Each can access it and each can change it.
