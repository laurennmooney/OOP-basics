## Exceptions

### What are exceptions?

Exceptions are a response to an exceptional circumstance. When an exception is thrown, the application will stop.

An exception is just another class with its own built-in methods. You can create a new instance of the exception class and "throw" you're own exception.

**Example:**

```csharp
Console.WriteLine("Enter a number:")
string input = Console.ReadLine();

int convertedNumber;
bool isConvertedSuccessfully = int.TryParse(input, out convertedNumber);

if (!isConvertedSuccessfully)
{
    throw new Exception("Conversion was not successful");
}
```

In this example, if the user inputs a string and not a number, the conversion will fail and we manually throw an exception (an unhandled one).

Basically, exceptions are used to provide detailed information about the cause of a particular failure. An exception should be thrown if the program is unable to successfully perform the action it is designed to do. This is an execution failure, and an exception should be thrown as a result.

An exception should be thrown when:

- The method cannot complete its defined functionality
- An inappropriate call to an object is made, based on the object state (_InvlidOperationException_)
- When an argument to a method causes an exception (_ArgumentException_)

Exceptions contain a property named StackTrace, a string that contains the name of the methods on the current call stack, together with the file name and line number where the exception was thrown for each method. This StackTrace object created automatically by the common language runtime (CLR) from the point of the throw statement, so that exceptions must be thrown from the point where the stack trace should begin. Thank you, [Microsoft](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/exceptions/creating-and-throwing-exceptions).

### Handling Exceptions

It is important to handle exceptions so that your application doesn't just stop. Instead, by handling the exception, the application keeps going and just logs the error, that way we can go back and fix it later.

Maybe you've seen something that looks like this:

```csharp
try
{
    // code here
}
catch
{
    // more code here
}
finally
{
    // and yet more code
}
```

This is a try/catch/finally. This kind of does how it reads: it tries something, it catches whatever exception might be thrown when "trying" (and handles it), and finally - which allows us to run any code whether there was an exception or not.

**Here's an example:**

```csharp
try
{
    Console.WriteLine("Enter a number:")
    string input = Console.ReadLine();

    int convertedNumber;
    bool isConvertedSuccessfully = int.TryParse(input, out convertedNumber);

    if (!isConvertedSuccessfully)
    {
        throw new Exception("Conversion was not successful");
    }
}
catch (Exception ex)
{
    Console.WriteLine($"There was an error: {ex.Message}");
}
finally
{
    Console.WriteLine("The rest of the program is still running");
}
```

It's good practice to not have any code outside of the try/catch/finally, in case there is an exception in the remaining code that would then be unhandled.

Another concept to understand is rethrowing exceptions. Say we moved the main logic of the converter into its own class:

```csharp
class StringToIntConverter
{
    public int convert(string input)
    {
        try
        {
            int convertedNumber;
            bool isConvertedSuccessfully = int.TryParse(input, out convertedNumber);

            if (!isConvertedSuccessfully)
            {
                throw new Exception("Conversion was not successful");
            }

            return convertedNumber;
        }
        catch (Exception ex)
        {
            // normally if you had somewhere to log the exception, you would log it first and then...
            throw;  // rethrowing
        }
    }
}
```

Then we go back to the main program:

```csharp
try
{
    Console.WriteLine("Enter a number:")
    string input = Console.ReadLine();

    try
    {
        StringToIntConverter stringToIntConverter = new StringToIntConverter();
        stringToIntConverter.convert(input);
    }
    catch (Exception ex)
    {
        Console.WriteLine($"There was an error with conversion: {ex.Message}");
    }
}
catch (Exception ex)
{
    Console.WriteLine($"There was an error: {ex.Message}");
}
finally
{
    Console.WriteLine("The rest of the program is still running.");
}
```

So now, the exception in the class will be rethrown back up to the caller.

### Best Practices

So there are a couple ways that are acceptable ways of throwing exceptions:

1. The way we did it in the class above:

```csharp
catch (Exception ex)
{
    throw;
}
```

2. You can create a new exception and pass in the actual exception:

```csharp
catch (Exception ex)
{
    throw new Exception("new message here", ex);
}
```

However, what IS NOT a good practice is this:

```csharp
catch (Exception ex)
{
    throw ex;
}
```

This is because it removes the StackTrace (which is basically a history of all the calls that have happened), which removes the origin of where the exception started.

[HOME](../master)
