Creating a basic class:

    - You use the keyword "class" with the name you want as the class following it.
    - Curly brackets are used after it, which is the opening of the class where you will put properties, methods, etc.

        Example:

            class Human
            {
                public int height;
                public int weight;
            }
    
    - In the example above, height and weight are properties of the class of the name "Human".

    - So, when creating a new object using this specific class (think of a class like an OUTLINE for an object, telling you/the computer of the structure this specific object needs to have), it is typically called "creating a new INSTANCE of the CLASS"

        Example for creating a new instance of a class in the main entry point of your program:

            class program
            {
                static void Main()
                {
                    Human human = new Human();
                }
            }
    
    So now that you've created a new INSTANCE of your class Human, you can assign values to the properties of this object.
        - You can do this by using the . operator, which gives you access to all the members of a given class (members are the fields, properties, methods, and everything else that defines a class):
        
            static void Main
            {
                Human human = new Human();

                human.height = 63;
                human.weight = 110;
            }

------------------------------------------------------------------------------------------------------------------

What are constructors:

    - A constructor is a method that will literally CONSTRUCT your class.
    - This method has the name of the class and no data type with it.
    - All classes have a constructor, even if it is not explicitly defined. Visual Studio will create a default one for you under the hood.
    - A constructor may or may not take in arguments as well. Arguments are the things within the parentheses.
    - You also must assign the values of the arguments given to the properties of the class.

        Example of a constructor of a class:

            class Human
            {
                public int Height;
                public int Weight;


                // this is the constructor!
                public Human(int height, int weight)
                {
                    Height = height;
                    Weight = weight;
                }
            }

    - So with the constructor now being defined, when you create a new instance of the class, you will pass arguments in the parentheses of new ClassName().
    
        Example:

            Human human = new Human(63, 110);

    - this will correctly assign 63 to Height and 110 to Weight

    - So now if you want to access the specific properties of the object to print to the console, you would write it using dot notation, like this:

        Example:

            Console.WriteLine(human.Height); // prints 63 when ran
            Console.WriteLine(human.Weight); // prints 110 when ran

    - You can have multiple constructors in a class. So for example, you could have an empty constructor or you could have one that requires argument(s).

        Example, in a class file:

            class Human
            {
                public int Height;
                public in Weight;

                public Human()
                {

                }

                public Human(int height, int weight)
                {
                    Height = height;
                    Weight = weight;
                }
            }
        
        Example of creating instance of the class with empty constructor and constructor with arguments:

            class Program
            {
                static void Main()
                {
                    Human human1 = new Human(); 
                    // no arguments, so properties can be assigned later, like below

                    human1.Height = 70;
                    human1.Weight = 130;

                    Human human2 = new Human(63, 110) 
                    // arguments provided, so Height and Weight are assigned accordingly.
                }
            }


IT'S IMPORTANT TO NOTE NOW THAT THIS IS ALL A STEP BY STEP INSTRUCTION OF THIS AND THIS IS NOT THE BEST NOR FINAL WAY OF SETTING UP A CLASS.

Please move on to the thiskeyword notes for more detail :)


    