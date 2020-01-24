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
- It reduces code complexity - it makes it easier for other developers to use our  code. They don't need to worry about the details; they only have expectations of what that method is going to do or return. 
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

Encapsulation means to restrict access to some of an objects compoenents. This comes into play with access modifiers, like _public_ and _private_. This allows an object or class to keep some of its data hidden from other objects, and the data can only be accessed or modified by _public_ getter or setter methods. See below.

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

So, other objects cannot directly access or use the object's state, only the object itself can through public methods that other object's can call on.

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
