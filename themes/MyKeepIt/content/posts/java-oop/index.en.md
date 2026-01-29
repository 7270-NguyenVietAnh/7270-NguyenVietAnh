---
weight: 3
title: "Java Object-Oriented Programming"
date: 2024-12-26T14:00:00+08:00
lastmod: 2024-12-26T14:00:00+08:00
draft: false
author: "ChatGPT"
authorLink: "https://chatgpt.com"
description: "Guide to Java programming using object-oriented style"
images: []
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["Java", "Object-Oriented Programming"]
categories: ["Java"]

lightgallery: true
---

# Introduction to Object-Oriented Programming in Java

Object-Oriented Programming (OOP) is a powerful programming paradigm that helps organize and process data in complex programs. Java, with its full support for OOP features, is one of the most popular languages used to develop large and powerful applications.

## Key Concepts in Object-Oriented Programming

Object-Oriented Programming includes four fundamental principles:

1. **Encapsulation**: Data and methods are encapsulated into objects. This helps protect data and control access to it.
2. **Abstraction**: Only display necessary details and hide unnecessary details, helping reduce system complexity.
3. **Inheritance**: Allows creating subclasses that inherit attributes and methods from a parent class, helping reuse source code.
4. **Polymorphism**: Allows using a method in different ways of execution, depending on the object calling it.

## Structure of a Class in Java

A class in Java can contain fields (variables) and methods. Below is an example of a simple class in Java:

```java
public class Animal {
    private String name;

    public Animal(String name) {
        this.name = name;
    }

    public void speak() {
        System.out.println(name + " says hello!");
    }
}
