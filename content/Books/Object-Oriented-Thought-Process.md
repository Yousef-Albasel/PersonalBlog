---
title: "Object Oriented Thought Process"
date: 2023-09-02T20:24:38+03:00
draft: true
---

Object-oriented programming is a programming paradigm, or classification, that organizes a group of data attributes with functions or methods into a unit, known as an object. Typically, OOP languages are class-based, meaning a class defines the data attributes and functions as a blueprint for creating objects, which are instances of the class. One class may represent multiple independent objects, which interact with each other in complex ways.

## First Chapter: Introduction to OOP Concepts:
  
It is important to note that the title of this first chapter is "Introduction to Object-Oriented Concepts." The operative word here is "Concepts," not "technologies." Technologies change very quickly in the software industry, whereas concepts evolve.

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


