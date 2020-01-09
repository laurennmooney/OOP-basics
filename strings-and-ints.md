## Strings and Ints: The Data Types, Built-in Methods, and Manipulation

### What are strings? And ints?

Hopefully, you already know this: a string is literally a string of characters - a sentence, a word, a name. **Textual data.** They are wrapped in double quotes.

Ints are integers, aka numbers.

Moving on.

### Converting strings to ints

Say you're taking in data from a user. This is returned to the application as a string, which can be an issue if your application is needing that input to be an actual number. For example, if you wrote up a simple calculator application and asked the user for a number, the user may enter 5. However, the application will read this as a string, like "5", and that could break things.

```csharp
string input = Console.ReadLine();


```

Here, input will be a string. You obviously cannot add a string to an int.

This is where converting a string to a number comes in handy.

Important to note is some data types have their own built-in methods that can be performed on them. Ints are one of these (so are strings, but we will get to that).

Building on the example above:

```csharp
string input = Console.ReadLine();

int inputAsNumber;
int TryParse(input, out inputAsNumber);

int result = 10 + 10 - 100 * inputAsNumber;
```

Above, we are using TryParse(), which is a pre-written method on the int data type (as well as other numerical types). TryParse() _actually_ returns a bool of either true - if the conversion was successful - or false.

So if the user enters 1000, it will convert the string "1000" to the int 1000.

#### Comparisons of strings

There may be times where you need to compare values of a string. Strings also have their own methods, some of which allow you to do this. One of these methods is Equals();

```csharp
string someText = "Here is some text.";
string someOtherText = "Here is some other text.";


// String.Equals(String)
someText.Equals(someOtherText);
```

This Equals() method will return you a bool value.

It is important to note that there are three types of comparisons that can be done here:

1. Ordinal: character-by-character comparison, and it is case-sensitive
2. InvariantCulture: takes into consideration neutral language rules
3. CurrentCulture: takes into consideration specific language rules (the users current region)

Equals(String) performs an ordinal comparison by default. However, you can specify the type of conversion with another form of this method (these are called **overloads**).

```csharp
String.Equals(String, StringComparison comparisonType);

someText.Equals(someOtherText, StringComparison.InvariantCulture);
```

If you are doing an ordinal comparison and want to ignore the case, you can justttt:

```csharp
bool isEqual = someText.Equals(someOtherText, StringComparison.OrdinalIgnoreCase);
```

Cool.

### String Concatination and String.Format()

So you can concatinate strings several different ways.

1. You can just add the strings together with variable names.

```csharp
string hi = "Hello";
string name = "Lauren";

string greet = hi + " " + name;
Console.WriteLine(greet); // this will print "Hello Lauren"
```

2. You can use template literals

```csharp
string hi = "Hello";
string name = "Lauren";

string greeting = $"{hi} {name}"
Console.WriteLine(greet); // this will also print "Hello Lauren"
```

3. You can use the .Format method on a string

```csharp
string hi = "Hello";
string name = "Lauren";

string greeting = string.Format("{0} {1}. How are you?", hi, name);
Console.WriteLine(greet); // this will also print "Hello Lauren. How are you?"
```

So what this does is that it takes in a template, which is the first argument to the method. Following that, you pass the arguments you want inserted into the template. In this case, hi will replace {0} and name will replace {1}.

Yup.

**_To Be Continued...._**
