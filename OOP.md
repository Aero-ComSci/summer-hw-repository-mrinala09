# Python 3: Object-Oriented Programming 
Object Oriented Programming or OOP is at the forefront of any programming language and is a type of a coding "paradigm". The basis of OOP relies on the creation of objects and classes that said objects are part of.  

For example we would use pythons in-built function ` _ _ init _ _ `, with this and other logic we can create our own classes, methods within those classes, and objects. 

```python
class Dog:
  sound = "Woof"

  def __init__(self, name, age):
    self.name = name
    self.age = age

  def bark(self):
    print(Dog.sound)
```
Basic application of Object Oriented Programming

For the following guide we will use the example above as a basis, and then understand how we can use more complex methods within this coding paradigm to enhance our code. 
The four core pillars of OOP are
* Inheritance
* Polymorphism
* Abstraction
* Encapsulation

# Classes and Objects
First we have to define a class, and we can do so by using the keyword `class` and following it should be said class name

```python
class Employee:
  new_id = 1
```
`new_id` is a class variable, or a variable within the class

Then from there we can create an object(s) that is part of the class `Dog` by calling the class
```python
e1 = Employee()
e2 = Employee()
```
Each time we call the class, it creates a new object

Then from there we can decide to add methods and attributes within the class itself (this acts as what any given object in the class would do or function to output/initiate)

## Methods 
The most common/functional method in OOP is an `__init__` method
You can also create your own methods just as you would for creating any function

```python
def __init__(self):
    self.id = Employee.new_id
    Employee.new_id += 1
```
In the example above we create a self.id and set it equal to the class variable `new_id` the reason we do `Employee.new_id` and just `new_id` is to make sure we are using the class itself to initiate/call the object. 

## Adding attributes/parameters
Let's take the example of the `__init__` method
```python
def __init__(self, occupation, id):
  self.occupation = occupation
  self.id = id

  def clasify(self):
    x = f"{self.id} works as a {self.occupation}"
    return x
```
Here we added the attributes occupation and id, and it allowed us to further define the class and the parameters it accepts and returns

# Dunder Methods
Defining a class’s dunder methods is basically a simple way to overload the operator, or in simpler terms make a way to use common operations and customize them to your preference, 
It's a form of polymorphism as it deals with object types like `int`, `str`, `list`, `+`, `-`, `*`, `**`

```python
class Meeting:
  def __init__(self):
    self.attendees = []
  
  def __add__(self, employee):
    print("ID {} added.".format(employee.id))
    self.attendees.append(employee)

  def __len__(self):
    return len(self.attendees)
```

In the example above, we used the dunder method `__add__` to add an instance of `Employee` each time that it is called, this is useful as it would allow us to have a constant way of adding objects to a given list, and allows us to properly store it with each new instance. 

We then use the dunder method `__len__` which functions similarly to `len` but since it is a dunder method it can now be called anytime without having to retype len for every instance of a class.


# Inheritance
Inheritance is a key pillar of OOP which basically allows us to "transfer" the attributes of a parent class to a child class without having to reinstate each attribute, and these can easily be overrriden, and we can also use multiple inhertance.
We will see an example of this below
```python
class Employee():
  new_id = 1
  def __init__(self):
    self.id = Employee.new_id
    Employee.new_id += 1

  def say_id(self):
    print("My id is {}.".format(self.id))

class Admin(Employee):
  pass


e1 = Employee()
e2 = Employee()

e3 = Admin()
e3.say_id()
```
Here we have a parent class `Employee` and the child class is `Admin` it retains the same attributes of an Employee but is now more specific, this makes our lives a lot easier as it allows us to have a bunch of different job positions with the same attributes under the same parent class. 
## Multiple Inheritance
The first way we can do this is by having a class inherit members from its superclass and its super-superclass.
```python
class Animal:
  def __init__(self, name):
    self.name = name
 
  def say_hi(self):
    print("{} says, Hi!".format(self.name))

class Cat(Animal):
  pass

class Angry_Cat(Cat):
  pass

my_pet = Angry_Cat("Mr. Cranky")
my_pet.say_hi() # Mr. Cranky says, Hi!
```
`Angry_cat` inherits from `Cat` which inherits its attributes from `Animal`, thus superclass and super-superclass.

The second way we can do this is to have a child class inherit the attributes and methods of two classes. 
```python
class Employee():
  new_id = 1
  def __init__(self):
    self.id = Employee.new_id
    Employee.new_id += 1

  def say_id(self):
    print("My id is {}.".format(self.id))

class User:
  def __init__(self, username, role="Customer"):
    self.username = username
    self.role = role

  def say_user_info(self):
    print("My username is {}".format(self.username))
    print("My role is {}".format(self.role))

# Write your code below
class Admin(Employee, User):
  def __init__(self):
    super().__init__()
    User.__init__(self, self.id, "Admin")

  def say_id(self):
    super().say_id()
    print("I am an admin.")

e1 = Employee()
e2 = Employee()
e3 = Admin()
e3.say_user_info()
```
The  `Admin` class inherits from the `User` class and the `Employee` class allowing it to use the methods and inherit the attributes of both classes. 
This example is of the given problem which allows us to track members in a meeting and their occupations

# Polymorphism
Polymorphism in itself is the ability to be able to apply an operation onto any object (different types of objects). This is most often used when the objext type is unkown and we still want to apply the method.

The example below will basically call the method `.say_id()` onto three different objects or instances `Employee()`, `Admin()` and `Manager()`
```python
class Employee():
  new_id = 1
  def __init__(self):
    self.id = Employee.new_id
    Employee.new_id += 1

  def say_id(self):
    print("My id is {}.".format(self.id))

class Admin(Employee):
  def say_id(self):
    super().say_id()
    print("I am an admin.")

class Manager(Admin):
  def say_id(self):
    super().say_id()
    print("I am in charge!")

e1 = Employee()
a1 = Admin()
m1 = Manager()
meeting = [e1, a1, m1]
for i in meeting:
  i.say_id()
```
This is extremely important because now we can apply a method without having to know what type of object we are applying it to, and allows us to do it quickly without having to remake methods for each type of object. 

# Abstraction
Abstraction is extremely helpful as it defines different behaviors/methods to be implemented within a certain class, meaning we retain the functionality of each and every class as we reach super, super-super, and so-on classes. 
```python
from abc import ABC, abstractmethod

class AbstractEmployee(ABC):
  new_id = 1
  def __init__(self):
    self.id = AbstractEmployee.new_id
    AbstractEmployee.new_id += 1

  @abstractmethod
  def say_id(self):
    pass

# Write your code below
class Employee(AbstractEmployee):
    def say_id(self):
      print("My id is {}".format(self.id))

e1 = Employee()
e1.say_id()
```
The `@abstractmethod` decorator means that any class that inherits from the class `AbstractEmployee` has to use/initiate a `.say_id` method, this allows us to call certain methods from a super-super-superrrrrclass without losing any functionality. 

Meaning each instance or a class that inherits form its super-class must implement a certain method

# Encapsulation
Encapsulation allows us to make methods and data within classes, methods, etc. hidden within the object that they are being used in. 
Theres 3 types of modifiers that can be used when doing so
* Public
* Private
* Protected

Sadly there are no in-built methods in python for showing that something is public like there are for other things BUT!
We use a single underscore `_` to indicate that `x` member is protected
And a double underscore `__` to indicate a private member

While any of these members can still be accessed it is helpful as it allows other people working on the project to be careful when using or trying to extract this type of data is it might encrypted and proteced/private for a reason

```python
class Employee():
    def __init__(self):
        self.id = None
        # Write your code below
        self._id = None
        self.__id = None

e = Employee()
print(dir(e))
```
We can see how we used the different lengths of underscores for the `id`'s!


WOW OOP SURE DOES HAVE A LOT OF STUFF! NOW HAVE FUN!!!!!
  
