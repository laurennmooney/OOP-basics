## Properties and Fields

### What are properties and fields and what are the differences?

So like I mentioned back in [thiskeyword](../master/thiskeyword.md), the "properties" we declared at the top of our class are ACTUALLY called fields.
Generally, _FIELDS ARE ALMOST ALWAYS PRIVATE, NOT PUBLIC_ - like we had before. By the way, these are called access modifiers.

**Example:**

```csharp
class Human
{
    // THESE ARE FIELDS, NOT PROPERTIES
    private int height;
    private int weight;
}
```

By making fields private, only the class they are contained within can access them. Obviously, this creates a problem if you want to use these fields somewhere else in your program.

- They can only be accessed via a PROPERTY or some other logic in your class.
  So the property is declared below the fields and above the constructor.
- Visual Studio has a shortcut you can use to make a property (prop + TAB + TAB)
  It usually has a public access modifier, the data type of the property you want to access, and the name of the property.
  The name of the property follows the name of the field. HOWEVER, they are typed differently. Fields are written in camelCase, while properties are written in PascalCase.

**Example:**

```csharp
class Human
{
    // THESE ARE FIELDS, AGAIN
    private int height;
    private int weight;

    // THESE ARE PROPERTIES
    public int Height { get; set }
}
```

Notice how there is a { get; set } following the name of the property. These are getters and setters. What these are used for is to get and set the variable.. pretty self-explanatory.

- These can actually be expanded and have their own code as well.

**Example:**

```csharp
class Human
{
    private int height;
    private int weight;

    public int Height
    {
        get
        {
            return height;
        }
        set
        {
            height = value;
        }
    }
}
```

So, the word "value" is used above. Value is another keyword which refers to the value being passed (like if you passed 63 for height, value = 63).

- lowercase height because it is referring to the field.
  We don't really need to write this out though, its implied by { get; set }. However, expanding the getters and setters allows you to implement validation logic inside of the scopes of get and set, using conditionals.

---

### Validation implementation in a property:

As stated above, we can expand getters and setters to allow for validation logic.

**We are going to switch up the class example for a real-life idea of how this can be used.**

```csharp
class User
{
    private string username;
    private int password;

    public string Username
    {
        get
        {
            return username;
        }
        set
        {
            if (value.Length >= 4 && value.Length <= 10)
            {
                username = value;
            }
            else
            {
                Console.WriteLine("Oops, this username isn't valid. Please use a username with 4 to 10 characters!);
            }
        }
    }

    public int Password
    {
        get
        {
            return password;
        }
        set
        {
            if (value >= 4 && value <= 10)
            {
                password = value;
            }
            else
            {
                Console.WriteLine("Oops, this password isn't valid. Please use a password between 4 and 10.);
            }
    }

    public User(string username, int password)
    {
        this.username = username;
        this.password = password;
    }
    }
```

---

### ReadOnly, WriteOnly, and ReadWrite properties:

Properties are not required to have a getter and a setter at the same time.

- Getter: Read.
- Setter: Write.
  So if a property is Read-Only (getter only) - you are unable to set the value outside of the class.
  On the other hand, if the property is Write-Only - you are unable to get the value outside of the class.

_"Well then how do you even set the value of a readonly property???"_

- You can do it in the constructor.

```csharp
class User
{
    private string username;
    private int password;

    public string Username { get };
    public int password { set };

    public User(string username)
    {
        this.username = username;
    }
}
```

So now if you create a new instance of the class, you will pass in the value you want as the username.
You can see the password, but cannot read it.

```csharp
User user = new User("Lauren");

user.Password = 2;

Console.WriteLine(user.Username); // prints "Lauren"
Console.WriteLine(user.Password); // will give you an error in IDE and not compile
```
