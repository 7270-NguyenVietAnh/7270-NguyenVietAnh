---
weight: 1
title: "Java Basics"
date: 2024-12-26T12:00:00+08:00
lastmod: 2024-12-26T12:00:00+08:00
draft: false
author: "ChatGPT"
authorLink: "https://chatgpt.com"
description: "Java Basics"
images: []
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["Java"]
categories: ["Java"]

lightgallery: true
---

# Introduction to Java

Java is an object-oriented programming language developed by Sun Microsystems in 1995. Java is one of the most popular programming languages in the world due to its simplicity, portability, and scalability.

## Java Features

1. **Object-Oriented**: Java fully supports object-oriented concepts such as inheritance, encapsulation, polymorphism, and abstraction.
2. **Platform Independent**: Java uses the Java Virtual Machine (JVM) to run code, so you only need to write the code once and can run it on multiple different platforms.
3. **Security**: Java is designed with built-in security mechanisms to protect applications from attacks.
4. **High Performance**: Although Java is not as fast as C++, the JVM and Java optimizations have significantly improved performance.
5. **Rich Libraries**: Java provides a wide range of libraries and APIs to support application development from simple to complex.

## Basic Structure of a Java Program

Below is an example of a simple Java program:

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello World!");
    }
}
```

### Explanation:
- `public class HelloWorld`: Declares a class named `HelloWorld`.
- `public static void main(String[] args)`: This is the main method where the program starts execution.
- `System.out.println`: Prints a line of text to the screen.

## Data Types in Java

Java supports many different data types, including:

1. **Primitive Types**:
   - `int`: Integer.
   - `float`: Floating point number.
   - `char`: Character.
   - `boolean`: True/false value.
2. **Reference Types**:
   - Object.
   - Array.

Example:

```java
int age = 25;
float height = 1.75f;
char gender = 'M';
boolean isStudent = true;
```

## Conditional Statements

Java provides conditional statements to control the execution flow of the program, such as:

### If-Else:

```java
if (age > 18) {
    System.out.println("You are old enough.");
} else {
    System.out.println("You are not old enough.");
}
```

### Switch:

```java
switch (day) {
    case 1:
        System.out.println("Sunday");
        break;
    case 2:
        System.out.println("Monday");
        break;
    default:
        System.out.println("Invalid");
}
```

## Loops in Java

Java supports many types of loops to repeat operations:

### For Loop:

```java
for (int i = 0; i < 5; i++) {
    System.out.println("Loop iteration: " + i);
}
```

### While Loop:

```java
int i = 0;
while (i < 5) {
    System.out.println("Loop iteration: " + i);
    i++;
}
```

## Conclusion

Java is a powerful, easy to learn language suitable for many types of applications, from mobile applications, web applications to large systems. Understanding the basic concepts is the first step to becoming a professional Java programmer.
