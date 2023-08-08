## Basic
```python
class ClassName:
    # Constructor for when the object is instantiated
    def __init__(self, value): # self is the current instance
        # Access Modifications
        # By default they are public (can be accessed outside the class: object.method(), object.property)
        self.instance_variable = value
        self._protected_variable = "Only meant to be accessible from subclasses and self(convention)" # Protected
        self.__private_variable = "Only accessible from self(copnvention)" # Private, will throw AttributeError because of name mangling
    # Destructor for when object is deleted
    def __del__(self):
        pass
```

## Inheritance
```python
class Parent:
    pass
class Child(Parent): # Derived class from parent
    def __init__(self, new_info):
        # Do something with new info
        self.value = new_info
        Parent.__init__(self) # Parent class init in own init
```
- Overriding methods from parent class can be done by defining the method again.
```python
class Cat(Animal):
     def __init__(self, name):
         super().__init__(name, "Meow!")
```

- ==super()== is used to access parent class and can be used to call something that may have been overwritten.

### Multiple inheritance

```python
class Dog:
    pass

class Wolf:
    pass

class Hybrid(Dog, Wolf): 
    pass
```
- Calling super() will call the first listed parent (Dog).
- To call Wolf methods we would use the class name: Wolf.method(self). ==Self must be used to specify the hybrid instance==.

## [[Polymorphism]]
```python
class A:
    def say(): print(0)
class B:
    def say(): print(1)
```

## Decorators
- ==@property==: Immutable property, can be retrieved as attribute without parentheses.
- ==@radius\.setter==: Setter with extra checks, can be assigned as if it was an attribute.
- ==@classmethod==: Is not bound to an instance of the class, often used as factory methods to create specific instances.
- ==@staticmethod==: Not dependent on the class, except that it's part of its namespace.
```python
class Circle:
    def __init__(self, radius):
        self._radius = radius

    @property
    def radius(self): # c.radius  returns the radius
        """Get value of radius"""
        return self._radius

    @radius.setter
    def radius(self, value): # c.radius = 2  changes the radius to 2
        """Set radius, raise error if negative"""
        if value >= 0:
            self._radius = value
        else:
            raise ValueError("Radius must be positive")

    @property # since it doesn't have a setter, it's immutable
    def area(self): # c.area = 100 returns AttributeError: can't set attribute
        """Calculate area inside circle"""
        return self.pi() * self.radius**2

    def cylinder_volume(self, height):
        """Calculate volume of cylinder with circle as base"""
        return self.area * height

    @classmethod
    def unit_circle(cls): # unit = Circle.unit_circle() returns a circle instance with radius 1
        """Factory method creating a circle with radius 1"""
        return cls(1)

    @staticmethod 
    def pi(): # can also be called directly on the class: Circle.pi()
        """Value of π, could use math.pi instead though"""
        return 3.1415926535
```

## Abstraction

- Abstract classes cannot be instantiated and abstract methods have to be defined on a child class.

```python
from abc import ABC

class MyAbstractClass(ABC):
    pass
```

- An abstract method will need to be defined in any of the classes inheriting it.

- If an abstract method is not instantiated, the child class will also be considered abstract and cannot be instantiated.


## Dunder (Double UNDERscore) Methods

- Using the same operator is a form of polymorphism called operator overloading.
- Defining a class' dunder methods is a way to perform operator overloading.
- There are many dunder methods possible: *\_\_len\_\_ *for example.

```python
class Animal:
    def __init__(self, name):
        self.name = name

    def __repr__(self): # string representation of the class (for printing)
        return self.name

    def __add__(self, another_animal): # behaviour of the + operator on the class
        return Animal(self.name + another_animal.name)
```
