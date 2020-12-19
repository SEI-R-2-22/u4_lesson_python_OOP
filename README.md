# Python Classes and Object Oriented Programming

## Objectives

- Learn how to create classes in python.
- Learn how to re use class objects.
- Learn how to inherit from parent classes.

## What is Object Oriented Programming?

From [Educative.io](https://www.educative.io/blog/object-oriented-programming):

> Object Oriented programming (OOP) is a programming paradigm that relies on the concept of classes and objects. It is used to structure a software program into simple, reusable pieces of code blueprints (usually called classes), which are used to create individual instances of objects. There are many object-oriented programming languages including JavaScript, C++, Java, and Python.

> A class is an abstract blueprint used to create more specific, concrete objects. Classes often represent broad categories, like Car or Dog that share attributes. These classes define what attributes an instance of this type will have, like color, but not the value of those attributes for a specific object.

> Classes can also contain functions, called methods available only to objects of that type. These functions are defined within the class and perform some action helpful to that specific type of object.

## Defining Classes In Python

Classes can be defined in `Python` using the `class` keyword:

```py
class Person:
    pass
```

### Definining Constructors

Taking our `Person` class from above, if we wanted to provide certain attributes to our `Person` we need to define a constructor with the `__init__` method:

```py
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
```

The above is equivalent to:

```js
class Person {
  constructor(name, age) {
    this.name = name
    this.age = age
  }
}
```

You'll notice we're passing in an extra paremeter called `self`. `Self` is used to reference a specific `instance` of a class when we create a new `Person`. It keeps a reference to which `name` belongs to which `instance`.

### Creating An Instance

Let's create a new `instance` of the `Person` class:

```py
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age


my_person = Person('Bob', 16)
print(my_person.name)
```

Here's the equivalent in Javascript:

```js
class Person {
  constructor(name, age) {
    this.name = name
    this.age = age
  }
}

myPerson = new Person('Bob', 16)
```

By creating an `instance` we are creating new people utilizing a template that we defined as our `class Person`.

### Instance Methods

Let's add a method to our `Person` class and greet someone:

```py
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

   def greeting(self):
        print('Hello my name is {name} and I am {age} years old!'.format(
            name=self.name, age=self.age))

my_person = Person('Bob', 16)
my_person.greeting()
```

Here's the equivalent in Javascript:

```js
class Person {
  constructor(name, age) {
    this.name = name
    this.age = age
  }

  greeting() {
    console.log(`Hello my name is ${this.name} and I am ${this.age} years old!`)
  }
}

myPerson = new Person('Bob', 16)
myPerson.greeting()
```

You should see `Hello my name is Bob and I am 16 years old!` printed to the terminal.

Class methods are unique to each `instance` of a class. `Instance` is just a fancy word for copy!

## Inheritance

Inheritance is a prgramming pattern to define a parent-child relationship. A child can inherit a parent's methods and attributes.

```py
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def greeting(self):
        print('Hello my name is {name} and I am {age} years old!'.format(
            name=self.name, age=self.age))

class Student(Person):
    def __init__(self, name, age, grade):
        super().__init__(name, age)
        self.grade = grade

    def greet_class(self):
        print('Hi my name is {name} and I am in grade {grade}'.format(
            name=self.name, grade=self.grade))
```

Here's a javascript example:

```js
class Person {
  constructor(name, age) {
    this.name = name
    this.age = age
  }

  greeting() {
    console.log(`Hello my name is ${this.name} and I am ${this.age} years old!`)
  }
}

class Student extends Person {
  constructor(name, age, grade) {
    super(name, age)
    this.grade = grade
  }

  greetClass() {
    console.log(`Hello my name is ${this.name} and I am in grade ${this.grade}`)
  }
}

myPerson = new Person('Bob', 16)
myPerson.greeting()
```

To inherit from a parent you'll notice we pass the parent class as an argument to our `Student` in this example. We create a constructor for student which accepts a name,age and grade. In order to pass some of those attributes back to the parent we utilize the `super` method and invole the parents `__init__` or constructor and pass in the attributes from the student to person. The grade attribute should be only used in the Student class.

Let's see how the greetings behave:

```py
my_person = Person('Bob', 16, 6)
my_person.greeting()
my_person.greet_class()
```

You'll see two different messages printed to the terminal.

```
Hello my name is Bob and I am 16 years old!
Hi my name is Bob and I am in grade 6
```

## You Do

Follow the instructions in `main.py` to complete this exercise.

## Resources

- [Why Use Objects and Object Oriented Programming](https://levelup.gitconnected.com/why-learn-objects-oriented-programming-in-python-794cdccc4caa)
