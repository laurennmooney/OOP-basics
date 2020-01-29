## Enumerations

### What are Enumerations?

An enumeration, or enum, can be used to define a set of constants, which can be used to limit some kind of option or variable(s). This allows you to give a specific set of options to choose from. Basically, its allows you to create _a collection of related constants to choose from._

Just like a class, an enum has its own file. In Visual Studio, you can just add a new class, and instead of leaving "class" you would change it to "enum" - the color of the name changes too (at least in Visual Studio, it does).

```csharp
enum Color
{
    red,
    blue,
    yellow
}
```

Note, all values of an enum are separated by a comma. They are each on their own row, and no data type specification is required. They are literall

Let's refer back to our Human class example. Say we wanted to assign them an eye color, but you wanted to limit the options of eye color. This is where an enum can come in handy.

```csharp
enum EyeColor
{
    Blue,
    Brown,
    Green,
    Hazel
}
```

So now there are four options for eye color: blue, brown, green, and hazel.

You can use enums just like you use classes, but you don't have to instantiate them like you do a class. You can actually use them as a field for a class.

```csharp
class Human
{
    private int height;
    private int weight;

    public EyeColor eyeColor; // this is the field using the enum

    public int Height { get; set };
    public int Weight { get; set };

    public Human(int height, int weight, EyeColor eyeColor)
    {
        this.height = height;
        this.weight = weight;
        this.eyeColor = eyeColor;
    }
}
```

In this example, eyeColor is of type EyeColor, which is an enum. When selecting a value within an enum, you will use dot notation, just like you would when referencing a certain property on an object.

**Example: Selecting Blue as the eyeColor**

```csharp
Human human = new Human(63, 110, EyeColor.Blue);
```

Typically, the value following the . will be a different color than the enum name preceding it.

You could also use enums to create conditions within the constructor of a class.

**For an obnoxious example, what if there was a world where people with hazel eyes were all REALLY tall and people with blue eyes were REALLY short?**

```csharp
class Human
{
    // all public just for this example, okay.
    public readonly HEIGHT;
    public int weight;
    public EyeColor eyeColor;

    public Human(int weight, EyeColor eyeColor)
    {
        this.weight = weight;
        this.eyeColor = eyeColor;

        if (this.eyeColor == EyeColor.Hazel)
        {
            HEIGHT = 75;
        }
        else if (this.eyeColor == EyeColor.Blue)
        {
            HEIGHT = 45;
        }
        else
        {
            HEIGHT = 67;
        }
    }
}
```

Enums help prevent possible mistakes by a user - it gives them a set of values from which they can choose, all of which are handled.

This helps to protect your code.

[HOME](../master)
