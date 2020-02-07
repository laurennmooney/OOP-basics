## The Four Pillars of Object Oriented Programming

There are four main **pillars** of object oriented programming. But, what is a pillar, exactly? Well, its something that provide _essential support_ for something. Therefore, the pillars of OOP are ideas or paradigms that provide support for OOP.

**What are these four pillars?**

1. Abstraction
2. Encapsulation
3. Inheritance
4. Polymorphism

### Abstraction

What does "abstraction" really refer to? Basically, _something only exists as an idea_. It has no definition, nothing is clear-cut, or concrete, and it's open to interpretation, just like abstract art. When it comes to OOP, abstraction really means to **expose functionality but hide the implementation details of that functionality**, while presenting the features to the outside world. It provided information about what an object does BUT _not how it does it_.

What are the advantages to abstraction?

- It reduces code complexity - it makes it easier for other developers to use our code. They don't need to worry about the details; they only have expectations of what that method is going to do or return.
- It hides the details and exposes only essential pieces or operations that are relevant for other objects

**Example:**

```csharp
public interface Actor {

    public abstract void actHappy();
    public abstract void actSad();
    public abstract void actAngry();
    public abstract void actInLove();
}
```

_Notice how there are NO implementation details for the methods that are part of this abstract interface_

Below, there two classes, Bob and Jill, and each one implements the abstract interface and uses its methods. However, Bob and Jill may have different implementations of these methods **because they are open for interpretation** (just like abstract art).

```csharp
public class Bob implements Actor
{

    public void actHappy()
    {
        // what Bob does when he's happy
    }

    public void actSad()
    {
      // what Bob does when he's sad
    }

    public void actAngry()
    {
      // what Bob does when he's angry
    }

    public void actInLove()
    {
      // what Bob does when he's in love
    }
}

public class Jill implements Actor {

    public void actHappy()
    {
      // what Jill does when she's happy
    }

    public void actSad()
    {
      // what Jill does when she's sad
    }

    public void actAngry()
    {
      // what Jill does when she's angry
    }

    public void actInLove()
    {
      // what Jill does when she's in love
    }
}
```

## Encapsulation

Encapsulation means to restrict access to some of an objects components. This comes into play with access modifiers, like _public_ and _private_ (and _protected_). This allows an object or class to keep some of its data hidden from other objects, and the data can only be accessed or modified by _public_ getter or setter methods. Basically, access modifiers define the scope and the visibility of a class member. See below.

**Example:**

```csharp
public class Student
{

    private string name;
    private string major;
    private int age;

    public string getName()
    {
        return name;
    }

    public void setName(string name)
    {
        this.name = name;
    }

    public string getMajor()
    {
        return major;
    }

    public void setName(string major)
    {
        this.major = major;
    }

    public int getName()
    {
        return age;
    }

    public void setName(int age)
    {
        this.age = age;
    }
}
```

So for a little more detail on some access modifiers:

1. **private**: only functions of the same class can access private members. This includes classes that are derived from the class who's member is marked as private (this will be explained further in inheritance).
2. **protected**: allows a _derived_ class to access the members of its base class.
3. **public**: can be accessed from outside the class. In other words, you can access these members (typically properties and methods) from outside the class, as long as an instance of the class has been created... unless its static of course.

Why are fields always private? It helps to hide implementation details (related to abstraction). Things that are implementation specific, you want to encapsulate them inside of your class (you want to keep them within your class). However, whatever you want to expose and let users or other developers interact with, then you can make them public or protected.

So, other objects cannot directly access or use the object's state, only the object itself can through public methods that other object's can call on.

Let's check out a real life example for a better idea:

**Example**

```csharp
class Car
{
    private int _fuel;
    private bool _engineStarted;

    public Car(int fuel)
    {
        _fuel = fuel;
    }

    public void StartEngine()
    {
        _engineStarted = true;
        StarterMotorTurnsEngineOver();
    }

    public void Drive()
    {
        if (_engineStarted)
        {
            if (_fuel <= 0)
            {
                Console.WriteLine("Cannot drive. Not enough fuel.");
            }
            else
            {
                Console.WriteLine("Driving...");
                _fuel--;
            }
        }
        else
        {
            Console.WriteLine("Cannot drive. Please start engine.");
        }
    }

    private void StarterMotorTurnsEngineOver() // hiding this from outside members
    {
        Console.WriteLine("Starter motor turned engine over");
        TurnCrankShaft();
    }

    private void TurnCrankShaft() // hiding this too
    {
        Console.WriteLine("Turns the crankshaft");
        EngineCycleStarts();
    }

    private void EngineCycleStarts() // yup
    {
        Console.WriteLine("Engine cycle starts");
        BeginCombustion();
    }

    private void BeginCombustion() // and again
    {
        Console.WriteLine("Begin combustion");
    }
}
```

In the above example, we are using the _literal_ process of starting a car engine (no I don't actually know these details. This is just an example that helped me!). So the method StartEngine() is **public** and can be accessed outside of the class. Then, the method StarterMotorEngineTurnsOver() is called within StartEngine(). Alas, a chain of events occur as this method calls another method and that other method calls another and so on. Notice though that those chain-event methods have a **private** access modifier. 

What this is doing is allowing an outside member to use the StartEngine() method -- which will still call the private methods no problem, because of the fact that the StartEngine() method is within that class -- but will NOT allow outside members to call the four private methods.

Just like in real life, we are hiding the details of starting the car engine. Sure, all those things happen **_under the hood_** (haaaaa), but all we know is that when we turn the key, the engine starts. We don't need to know every step in order to make it happen. Yay, encapulation.

**So if we were to do thiiiis:**

```csharp
class Program
{
    Car myCar = new Car();

    myCar.startEngine();
}
```

Then we would see this in our console:

```csharp
Starter motor turned engine over
Turns the crankshaft
Engine cycle starts
Begin combustion
```

We don't need to know how - **_it just happens_**.

### Inheritance

The concept of inheritance is (just like genes) when a class inherits properties or methods of other class - or gains access to them. Pretty simple, right?

**Example:**

So, we start with a simple class, called Person

```csharp
class Person
{
    public string FirstName { get; set }
    public string LastName { get; set }

    public Person(string FirstName, string LastName)
    {
        this.FirstName = FirstName;
        this.LastName = LastName;
    }

    public void Walk()
    {
        // code here
    }

    public void Eat()
    {
        // code here
    }

    public void Sleep()
    {
        // code here
    }
}
```

However, we then can make another class that inherits the Person class. This is called a **derived class** (aka, child class or subclass).

```csharp
class Child : Person // the colon indicates that the class inherits from the class following the colon
{
    public Child(string FirstName, string LastName) : base(FirstName, LastName)
    {
        // base is a keyword that tells the class to use the constructor from the inherited class
        // in this case, Person
    }

    public void Play()
    {
        // code
    }

    public void Cry()
    {
        // code
    }
}
```

So, now that Child has inherited Person's methods, you can do this in your program:

```csharp
Child child = new Child(Sophia, Rose);
child.Sleep(); // Child inherits the Sleep() method from Person
child.Play(); // However, this method only exists on Child

Person person = new Person(Bob, Jenkins);
person.Play(); // this will give an error, because this method does not exist on Person
```

### Polymorphism

This one is a little more complex. Personally, I've been told this is the last of the four pillars that a developer will come to understand and grasp. I can see why.

Polymorphism literally means "many shapes" in Greek. It is the concept of an object have many forms. This allows a child class that was _derived_ from a parent class to be treated as their _base_ class with no issue. Additionally, child/derived classes can override certain methods in their parent class. This actually requires use of the keyword "virtual" in the parent class method and the keyword "override" in the derived class method.

**This is the best example I have (for now)**:

```csharp
// parent class of Character
class Character
{
    protected string name;
    public virtual void Speak()
    {
        Console.WriteLine($"Hi, my name is {name}!");
    }
}

// derived class of Tommy
class Tommy : Character
{
    public override void Speak()
    {
        Console.WriteLine("Hey, I'm Tommy!");
    }
}

// so if you make an instance of class Tommy
Character tommy = new Tommy();
tommy.Speak(); // "Hi, I'm Tommy!" will be printed to the console, not the Character Speak() method output
```

### Trust me, as I become more comfortable with these, I will update with more examples!

[HOME](../master/README.md)
