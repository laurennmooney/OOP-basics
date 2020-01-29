## Constant and Read-Only Fields

### What are constants?

Basically, constants are values that cannot be reassigned/reinitialized after their first assignment. This prevents changing of the value from what it was originally set at.

These types of fields can only get their values from inside the constructor.

There are two types of constants:

1. Const keyword - this must be defined before you run your code. In other words, this is hard-coded, so you set the specific value. For example, you might hard-code a specific const value in the constructor of a class.
2. Readonly keyword - these are defined after you run the code and it gets its value somewhere down the line.

### Readonly keyword

**So, let's take a look at our example from [Static Fields](../master/static.fields) and expand on it a bit**

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

In the example above, we have a field of id, which is a static field and therefore, can be accessed wherever. This also allows its value to be changed. However, since we are setting an id to each instance of a User, what if we don't want that id value to be able to be changed? This is where **readonly** fields come in.

**Example below:**

```csharp
class User
{
    public static int currentId; // change id to currentId

    public readonly int ID; // create a new field of ID, which is a readonly field

    private string username;
    private int password;

    public string Username { get };
    public int password { set };

    public User() // remember empty constructors??
    {
        currentId++; // change this so it increments the currentId for each instance of the class
        ID = currentId; // set the ID to what the currentId is, which will then be incremented.
    }

    public User(string username)
    {
        currentId++; // change this so it increments the currentId for each instance of the class
        ID = currentId; // set the ID to what the currentId is, which will then be incremented.
        this.username = username;
    }
}
```

In this example, we added a readonly field of ID and changed what used to be id to currentId. With this, we can now access what the currentId of the class is. However, the ID of the class can only be initialized at the time of instantiation of the class.

**So if you tried to do this... you will get an error**

```csharp
User user = new User();
user.ID = 200;
```

In Visual Studio, the error will read _"A readonly field cannot be assigned to (except in a constructor or variable initializer)"_

Typically, naming convention for constants is ONLY CAPITAL LETTERS (this may be vary by company, but generally, this is the rule of thumb).

- If there are spaces in the name, then underscores are used. For example, PINATTEMPTLIMIT would be PIN_ATTEMPT_LIMIT.

### Const keyword

Now we will touch on the const keyword.
When using const, you MUST initialize the value of the field at the time of declaration.

In the example above with readonly, you could declare the field but not initialize the value until an instance of the class is created. However, if you try to do this with const, you will get an error.

**Shortened example from above using const and readonly:**

```csharp
class User
{
    public static int currentId;

    public const int HEIGHT = 70; // without the value being assigned, an error will be throw.

    public readonly int ID;
}
```

Const fields are _STATIC BY DEFAULT_ - so you do not need to create an instance of the class to access the value. Additionally, the value will be the same for ALL INSTANCES of the class. And, since its a constant, the value is unable to be changed.

[HOME](../master)