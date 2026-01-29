---
weight: 10
title: "C# Basics"
date: 2024-12-27T10:00:00+08:00
lastmod: 2024-12-27T10:00:00+08:00
draft: false
author: "ChatGPT"
authorLink: "https://chatgpt.com"
description: "Learn the fundamentals of C#, a powerful and modern programming language."
images: []
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["CSharp", "Programming"]
categories: ["CSharp"]

lightgallery: true
---

# Introduction to C#

C# is a modern, powerful, and object-oriented programming language developed by Microsoft. It is widely used for developing desktop applications, web applications, games, and cloud services.

## Features of C#

1. **Object-Oriented**: C# fully supports object-oriented programming with classes, inheritance, polymorphism, and encapsulation.
2. **Type-Safe**: C# is a strongly typed language, preventing many common programming errors.
3. **Garbage Collection**: Automatic memory management through garbage collection.
4. **Rich Framework**: .NET Framework provides extensive libraries for various development tasks.
5. **Cross-Platform**: With .NET Core and .NET 5+, C# can run on Windows, Linux, and macOS.

## Basic Structure of a C# Program

Below is a simple C# program:

```csharp
using System;

class Program {
    static void Main() {
        Console.WriteLine("Hello World!");
    }
}
```

### Explanation:
- `using System;` - Import the System namespace.
- `class Program` - Define a class named Program.
- `static void Main()` - The main entry point of the program.
- `Console.WriteLine()` - Print text to the console.

## Data Types in C#

C# supports various data types:

```csharp
int age = 25;
float height = 1.75f;
string name = "John";
bool isStudent = true;
```

## Control Structures

### If-Else:

```csharp
if (age > 18) {
    Console.WriteLine("You are an adult.");
} else {
    Console.WriteLine("You are a minor.");
}
```

### Loops:

```csharp
for (int i = 0; i < 5; i++) {
    Console.WriteLine("Iteration: " + i);
}
```

## Conclusion

C# is a powerful language suitable for various types of applications. Understanding its fundamentals is the first step to becoming a proficient C# developer.
