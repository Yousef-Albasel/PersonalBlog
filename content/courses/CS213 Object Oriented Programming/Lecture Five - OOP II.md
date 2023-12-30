---
title: "Lecture Five - OOP II (Inheritance, Polymorphism and Constructors)"
date: 2023-12-30T01:03:40+02:00
draft: false
series: ['OOP Course Notes Series']
---

First let's Discuss **Inheritance** in C++.

####Inheritance: 

**Is to create child classes from a parent class, inheriting all it's features and more!**

Derived classes **absorb** all features of existing classes including their data and functions. Also **enhance** them by **adding** their own new features in form of new data members and new member functions

Inheritance provides us a mechanism of **software reusability** which is one of the most important principles of software engineering
![](https://cdn-images-1.medium.com/max/1080/1*gRily1Y6mlrOETJeKRgvgw.png)

####Visibility:

In C++ and other OOP languages, you need to write an access modifier when inheriting from a base class, that's what we call it visibility mode.

![](https://media.geeksforgeeks.org/wp-content/uploads/20200304134750/Visibility-Modes-in-C.jpg)

When you create private members in a class, you can't access it anywhere outside the class, you can inherit it, but not use it.
Consider this example
```cpp
class A
{
public:
    int x;

protected:
    int y;

private:
    int z;
};

```
**If you inherit using the public mode:**

- Public members stay public in the derived class, and you can access them.

- Protected members become public in the derived class, and you can access them.

- Private members remain private and are not directly accessible in the derived class.

```cpp
class B : public A
{

    void print_data()
    {
        cout << x << endl;
        cout << y << endl;
        cout << z << endl; // member "A::z" (declared at line 13) is inaccessible C/C++(265)
    }
};
```

**If you inherit using the protected mode:**

- Public members become protected in the derived class, and you can access them within the derived class (but not from outside).

- Protected members stay protected in the derived class, and you can access them within the derived class (but not from outside).

- Private members remain private and are not directly accessible in the derived class.

```cpp
class C : protected A
{

    void print_data()
    {
        cout << x << endl;
        cout << y << endl;
        cout << z << endl; // member "A::z" (declared at line 13) is inaccessible C/C++(265)
    }
};

```
**If you inherit using the private mode:**
- Public members become private in the derived class, and you can't access them directly.

- Protected members become private in the derived class, and you can't access them directly.

- Private members remain private and are not directly accessible in the derived class.

```cpp
#include <iostream>

using namespace std;

// Base class A
class A {
public:
    int x; // Public member

protected:
    int y; // Protected member

private:
    int z; // Private member
};

// Derived class D with private inheritance
class D : private A {
public:
    void print_data() {
        cout << x << endl; // Accessible (private)
        cout << y << endl; // Accessible (private)
        // cout << z << endl; // Inaccessible (private)
    }
};

int main() {
    D object_d;

    // Accessing members of D through public member functions
    object_d.print_data(); // Accessible (public)

    // Accessing members directly from main is not allowed
    // cout << object_d.x; // Inaccessible (private)
    // cout << object_d.y; // Inaccessible (private)
    // cout << object_d.z; // Inaccessible (private)

    return 0;
}
```

------------

#### Constructors
> Constructor in C++ is a special method that is invoked automatically at the time of object creation. It is used to initialize the data members of new objects generally. The constructor in C++ has the same name as the class or structure. It constructs the values i.e. provides data for the object which is why it is known as constructor. -GeekForGeeks

By default, each class has member functions:
constructor   		Date();
destructor    		~Date();
copy constructor 	Date(const Date& other);
assignment operator   Date& operator=(const Date& other);

##### Constructor:

You can make a constructor using this syntax
`class-name (args) {implement};`

This will be called to initialize an object every time you create a new one.
```cpp
class A
{
public:
    int x;

    A(int numX, int numY, int numZ)
    {
        x = numX;
        y = numY;
        z = numZ;
    };
}
```

or you can use this syntax if you are a psychopath.

`class-name (args) : member-data(argument data), member-data2(argument-data2), ... {};`
```cpp
class A
{
public:
    int x;

    A(int numX, int numY, int numZ) : x(numX), y(numY), z(numZ){};


protected:
    int y;

private:
    int z;
};

```
You can create a constructor to a derived class by creating a constructor and assigning values to the base class.
{{< rawhtml >}}
<div class="warning-container" style="background-color: #ffebee; border-left: 6px solid #f44336; padding: 10px; font-weight:bold;">Constructors should be defined for each derived class. 
  </div>
{{< /rawhtml >}}

**If there is no constructor in a derived class, a default zero-parameter  constructor will be generated which in turn calls the zero-parameter constructor in the base class to initialize the inherited members**


```cpp
class B : public A
{
protected:
    int v, w;

public:
    B(int numV, int numW, int numX, int numY, int numZ) : A(numX, numY, numZ) // or directly assign values eg : B(..):A(1,2,3){};
    {
        // assign it to the data
        numV = v;
        numW = w;
        numX = x;
        // ...
    };

}
```
| Derived Class Inherits | Derived Class doesn't inherit   |
| ------------ | ------------ |
| Every data member defined in the parent class   | The base class's constructors and destructor |
|Every ordinary member function of the parent class |The base class's assignment operator |
|The same initial data layout as the base class|The base class's friends|

