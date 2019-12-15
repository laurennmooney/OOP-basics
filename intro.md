# Welcome to Object Oriented Programming

## Some basic terminology, which will be described more in depth later:

1. Class - describes an object. Used to create an object.
2. Namespace - used to structure and organize your files/classes in your project.
3. Constructor - constructs your class and gives initial values to your objects.
4. Fields - used to describe your object. They are within a class.
5. Properties - these allow the "outside world" to access the fields of a class.
6. Const and Readonly constants - we'll get there.

### What is Object Oriented Programming (OOP) and why is it used?

#### What is an object?

- Well, anything can be an object! Anything that can be described with a given set of properties, such as a person, car, house, etc. For example, every person has a height and weight, or every car has a color and an engine, and a house has a certain number of doors and windows.
- an object is constructed of at least one or more key/value pairs - called properties.

  ```js
  exampleObject = {
    key1: 1,
    key2: 2
  };
  ```
  
  OR a more detailed example:

```js
human = {
  height: 63,
  weight: 110,
  hairColor: "blonde"
};
```

Every object has properties!
And objects can have their own objects as well.

- Example: a car has an engine and the Engine can have its own properties as well.

#### So what is a class?

- A class is basically a description of an object.
- The class will hold the properties of the given object.
- A class can have a class within it

Classes allow us to create our own custom data types, which are at its lowest level described with the basic, primitive data types (strings, ints, doubles, booleans, etc).

#### So, why do we bother with OOP?

- It allows you to organize your code much easier. We can create our own classes, which will each have its own file.
- It helps to maintain and extend your code.
