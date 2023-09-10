---
title: "Object Oriented Thought Process"
date: 2023-09-02T20:24:38+03:00
draft: true
---

Object-oriented programming is a programming paradigm, or classification, that organizes a group of data attributes with functions or methods into a unit, known as an object. Typically, OOP languages are class-based, meaning a class defines the data attributes and functions as a blueprint for creating objects, which are instances of the class. One class may represent multiple independent objects, which interact with each other in complex ways.

## First Chapter: Introduction to OOP Concepts:
  
It is important to note that the title of this first chapter is "Introduction to Object-Oriented Concepts." The operative word here is "Concepts," not "technologies." Technologies change very quickly in the software industry, whereas concepts evolve.

#### Objects and Legacy systems
OOP and Structured Programming don't compete with each other, they are complementary.

## Procedural Programming vs OOP

In OO Design the attributes and behaviors are contained within a single in object, whereas in procedural or structured design the attributes and behaviors are normally separated.

![Object-Oriented Programming Concepts](https://devopedia.org/images/article/264/9332.1585228697.jpg)
![C++ Classes and Objects - GeeksforGeeks](https://media.geeksforgeeks.org/wp-content/cdn-uploads/Classes-and-Objects-in-C.png)

#### Data Hiding

by combining attributes & methods, which is encapsulation, we can control access to the data in the `Math` object. By defining these integers as off-limits, another unconnected function cannot manipulate the integers myInt1 and myInt2 - Only the `Math` object can.
https://www.youtube.com/watch?v=LodRm5BiVro
#### What Exactly Is an Object?
 Objects are the building blocks of an OO program. A program that uses OO technology is basically a collection of objects.
 
The behavior of an object is what the object can do. In procedural languages the behavior is defined by procedures, functions, and subroutines. In OO programming terminology these behaviors are contained in methods, and you invoke a method by sending a message to it. In our employee example, consider that one of the behaviors required of an employee object is to set and return the values of the various attributes. Thus, each attribute would have corresponding methods, such as `setGender()` and `getGender()`. In this case, when another object needs this information, it can send a message to an employee object and ask it what its gender is.
 
#### What Exactly Is a Class? 
In short, a class is a blueprint for an object. When you instantiate an object, you use a class as the basis for how the object is built. In fact, trying to explain classes and objects is really a chicken-and-egg dilemma. It is difficult to describe a class without using the term object and visa versa. For example, a specific individual bike is an object. However, someone had to have created the blueprints (that is, the class) to build the bike. In OO software, unlike the chicken-and-egg dilemma, we do know what comes first—the class.
An object cannot be instantiated without a class.

![OOP in JavaScript: Explained using games | by ALEXANDRU TAPIRDEA | Level Up  Coding](https://miro.medium.com/v2/resize:fit:717/0*ieq1DK9xP2q2Ztrv)
## Encapsulation 

In a good OOP design, an object should reveal only the interfaces other objects interact with. 
For example, consider this class:
```python
class Car:
def __init__(self,speed,color):
	__self.speed = speed
	__self.color = color

def set_speed(self,value): # setter
	__self.speed = value
def get_speed(self): # getter
	return __self.speed
```

```py
my_car = Car(60, "blue")
print(my_car.get_speed())  # Output: 60
my_car.set_speed(70)
print(my_car.get_speed())  # Output: 70

# Accessing __speed directly (discouraged)
print(my_car._Car__speed)  # Output: 70


```
-   Encapsulation is achieved by marking the `__speed` attribute as private using double underscores (`__`).
-   Getter and setter methods (`get_speed()` and `set_speed(value)`) provide a controlled interface for accessing and modifying the private `__speed` attribute.
-   Encapsulation allows you to hide the internal details of the `Car` class, enforce data validation and logic, and signal to other developers not to access private attributes directly.
-   While Python doesn't enforce strict access control, the naming convention of double underscores serves as a convention to encourage proper usage of encapsulated attributes.

## Inheritance
One of the major issues in OO is to factor out commonality of the various classes, inheritance enables a class to inherit the attributes and methods of another class.
![Inheritance in Object Oriented Programming (Java)](https://cdn-images-1.medium.com/max/1080/1*gRily1Y6mlrOETJeKRgvgw.png)

## Abstraction

Abstraction in Object-Oriented Programming (OOP) is a fundamental concept that involves simplifying complex systems by focusing on essential properties and behaviors while hiding unnecessary details. It allows programmers to create abstract classes or interfaces that define a blueprint for objects without specifying their specific implementation.
1.  Focuses on essential features: It identifies and defines the most important characteristics and behaviors of objects, ignoring less relevant details.
    
2.  Hides implementation details: Abstraction allows you to conceal the inner workings of an object, providing a high-level interface for interaction while keeping the underlying complexity hidden.
    
3.  Provides a blueprint: Abstract classes or interfaces serve as templates that other classes can inherit from, ensuring consistency and reusability in the code.
    
4.  Promotes code organization: Abstraction helps in organizing and structuring code by breaking it down into manageable and meaningful components.



#### Multiple Inheritance

  
Multiple inheritance is a feature in some object-oriented programming languages that allows a class to inherit attributes and behaviors from more than one parent class. However, multiple inheritance can lead to complexities and ambiguities, and not all programming languages support it.


![Multiple Inheritance in Python - Python Geeks](data:image/png;base64,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)

Code example in C++: 
```cpp
#include <iostream>

// Parent class 1: Bird
class Bird {
public:
    Bird() {
        can_fly = true;
    }

    void fly() {
        std::cout << "The bird can fly." << std::endl;
    }

private:
    bool can_fly;
};

// Parent class 2: Mammal
class Mammal {
public:
    Mammal() {
        has_hair = true;
    }

    void feedMilk() {
        std::cout << "The mammal can feed milk." << std::endl;
    }

private:
    bool has_hair;
};

// Child class inheriting from both Bird and Mammal
class Bat : public Bird, public Mammal {
public:
    Bat() {
        // Constructors of parent classes are called automatically
    }

    void displayInfo() {
        std::cout << "Bat can fly: " << can_fly << std::endl;
        std::cout << "Bat has hair: " << has_hair << std::endl;
    }
};

int main() {
    // Create an instance of the Bat class
    Bat bat;

    // Accessing attributes and methods from both parent classes
    bat.displayInfo();
    bat.fly();
    bat.feedMilk();

    return 0;
}

```

