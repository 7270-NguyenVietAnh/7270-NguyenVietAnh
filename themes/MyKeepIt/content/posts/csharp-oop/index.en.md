---
weight: 11
title: "C# Object-Oriented Programming"
date: 2024-12-27T11:00:00+08:00
lastmod: 2024-12-27T11:00:00+08:00
draft: false
author: "ChatGPT"
authorLink: "https://chatgpt.com"
description: "Master object-oriented programming in C#, including classes, inheritance, and polymorphism."
images: []
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["C#", "OOP", "Object-Oriented Programming"]
categories: ["C#", "Advanced Concepts"]

lightgallery: true
---

# C# Object-Oriented Programming

Object-Oriented Programming (OOP) is a fundamental concept in C#. It helps organize code into logical units called classes and objects, making programs more maintainable and scalable.

## Core OOP Principles

### 1. Encapsulation

Encapsulation involves bundling data (properties) and methods (behaviors) into a single unit (class) and hiding the internal details.

```csharp
public class Person {
    private string name;
    private int age;

    public string GetName() {
        return name;
    }

    public void SetName(string n) {
        name = n;
    }
}
```

### 2. Inheritance

Inheritance allows a class to inherit properties and methods from a parent class.

```csharp
public class Animal {
    public void Eat() {
        Console.WriteLine("Animal is eating.");
    }
}

public class Dog : Animal {
    public void Bark() {
        Console.WriteLine("Dog is barking.");
    }
}
```

### 3. Polymorphism

Polymorphism allows objects to take multiple forms. It can be achieved through method overriding.

```csharp
public class Shape {
    public virtual void Draw() {
        Console.WriteLine("Drawing a shape.");
    }
}

public class Circle : Shape {
    public override void Draw() {
        Console.WriteLine("Drawing a circle.");
    }
}
```

### 4. Abstraction

Abstraction hides the complex implementation details and shows only the necessary features.

```csharp
public abstract class Vehicle {
    public abstract void Drive();
}

public class Car : Vehicle {
    public override void Drive() {
        Console.WriteLine("Car is driving.");
    }
}
```

## Creating and Using Objects

```csharp
class Program {
    static void Main() {
        Dog dog = new Dog();
        dog.Eat();
        dog.Bark();
    }
}
```

## Conclusion

Mastering OOP in C# is essential for writing clean, maintainable, and scalable code. By understanding classes, inheritance, polymorphism, and abstraction, you can become a proficient C# developer.
