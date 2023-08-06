---
title: "Math and Computersci"
date: 2023-08-01T12:19:41+03:00
draft: true
---

I never was a fan of **Mathematics**. Maybe it's the way I learned it in my early days. Why do we CS students study it? Aren't we supposed to create some C++ programs instead? Well, actually, math is crucial for programmers: those who just need to create web pages, and those who build AI models.

 **For web developers** , math plays a crucial role in the process of creating both front and back ends. It is necessary for performing algorithm optimizations, designing responsive layouts, analyzing user behavior, implementing encryption and security measures, as well as handling tasks like data processing, database queries, and financial calculations. Math comes in handy no doubt.

**Both machine learning and data science** heavily rely on linear algebra, calculus, statistics, and probability. Both fields are built upon mathematical prerequisites, as these concepts are essential for optimization, understanding data distributions, and constructing the actual algorithms!
### How computers do math
Let's take a walk on how computers do math, the responsible part for math is the **Arithmetic Logic Unit (ALU)**. All that it does is math. Next to it is the **Floating Point Unit (FPU)** to handle more precise numbers. Everything else that the computer does from the instruction set perspective is to control which **mathematical** instructions are operated when and to actually move data around so that it's in the right place for the next bit of math.

Arithmetic Logic Unit design:
![](https://zipcpu.com/img/alu-simple.svg)

And it uses the binary representation to perform any math-related operations, as it can't read base 10 numbers directly. From a high-level perspective, we teach computers to perform more complex operations using algorithms.
### Motivation
One application that i find really interesting is the donut math projection.

![](https://hackaday.com/wp-content/uploads/2020/07/spinning-donut-thumb.gif?w=600&h=600)

at it's core,it's a circle that rotates around Y - Axis to construct donut shape, the code uses 3D perspective projection to convert 3D coordinates (x, y, z) into 2D screen coordinates (x', y'). It projects points onto a plane located at a fixed distance (z') from the viewer.
using this equation : (x', y') =** (K1 * x / (z + K2), K1 * y / (z + K2))**

![](https://www.a1k0n.net/img/perspective.png)

That's all I really know for now. You can view all the information [here.](http://https://www.a1k0n.net/2011/07/20/donut-math.html "here")
another application that i really like and i plan to write about it more is the Perlin Noise Algorithm.
![](https://user-images.githubusercontent.com/111648493/253647549-0e46589f-a1f7-4d7d-a3ed-18f24f4e3a84.png)

 **Perlin noise** is a type of procedural noise used in computer graphics and simulations to create natural-looking textures, patterns, and animations. It was developed by **Ken Perlin** in 1983, it uses simple linear algebra concepts to create a grid of pixels with gray scale values between(0-255) that are smoothly varying across the grid, simulating natural patterns such as mountains, clouds, or textures. These grayscale values represent different levels of intensity or elevation.

and i already created a [repo](https://github.com/Yousef-Albasel/Perlin-Noise-Generator "repo") that has the implemention in details.
also check out : [this](https://rtouti.github.io/graphics/perlin-noise-algorithm "this") and [this](https://iq.opengenus.org/perlin-noise/ "this").

I hope that was enough reason for why do computer science students need to study math.