## What on earth is the "this" keyword?

The this keyword is something that can be very confusing for some, and that's usually because it can be used different ways at certain times.
Here we will be looking at it while its being used to reference properties of a class.

**For reference, this is how we wrote the Human class before:**

```csharp
class Human
{
    public int Height;
    public int Weight;
}
```

We have properties of Height and Weight, declared with uppercase letters at the beginning. However, this is not the typical way of doing it.

- Typically, these declarations are called **FIELDS** of a class, not properties.
- You will usually declare these fields using camelCase, not PascalCase.
- We will get into properties vs fields and their differences later, but fields are the types of properties that the class can have. The constructor will be responsible for assignment of the properties (that correspond to the fields) to values for the particular instance of the class. See [Properties and Fields](../master/propertiesVSfields.md) for more detail!

```csharp
class Human
{
    public int height;
    public int weight;

    // including the constructor
    public Human(int height, int weight)
    {
        height = height;
        weight = weight;
    }
}
```

However, there is an issue with the way it is written above. The computer won't be able to tell the difference between the height that is the property and the height that is the argument value being initialized to the property. You'll get an error and the code won't compile. Bummer...

This is where "this" comes into play. By using "this", it tells the computer that the variable it is referring to is the property of the instance of the class being constructed by the constructor, not the value it is being initialized to by the argument being passed.

- I think of it as "okay so _THIS INSTANCE OF THE HUMAN_ height is going to be equal to the height passed in, and _THIS INSTANCE OF THE HUMAN_ weight is going to be equal to the weight being passed in.

**Example:**

```csharp
class Human
{
    public int height;
    public int weight;

    public Human(int height, int weight)
    {
        this.height = height;
        this.weight = weight;
    }
}
```

The this keyword allows differentiation between the field and the argument.

_So when should you really use the this keyword?_
It's a loaded question, but usually its safe to assume that whenever you have a naming conflict, then you should use "this"
**Always use "this." to show that you are pointing at a member from your Class IF there is a name conflict.**

[HOME](../master)