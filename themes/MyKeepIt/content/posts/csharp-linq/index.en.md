---
weight: 13
title: "LINQ in C#"
date: 2024-12-27T13:00:00+08:00
lastmod: 2024-12-27T13:00:00+08:00
draft: false
author: "ChatGPT"
authorLink: "https://chatgpt.com"
description: "Master Language Integrated Query (LINQ) in C# for efficient data querying and manipulation."
images: []
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["CSharp", "LINQ", "Data Query"]
categories: ["CSharp", "Advanced Concepts"]

lightgallery: true
---

# LINQ in C#

LINQ (Language Integrated Query) is a powerful feature in C# that allows you to query and manipulate data from various sources using a consistent syntax.

## What is LINQ?

LINQ provides a uniform way to query data from different sources such as arrays, lists, databases, and XML documents.

## LINQ Query Syntax

### Basic Query:

```csharp
using System;
using System.Linq;

int[] numbers = { 1, 2, 3, 4, 5 };

var result = from num in numbers
             where num > 2
             select num;

foreach (var item in result) {
    Console.WriteLine(item);
}
// Output: 3, 4, 5
```

## LINQ Method Syntax

Method syntax is more flexible and allows chaining of operations.

```csharp
var result = numbers
    .Where(num => num > 2)
    .Select(num => num * 2)
    .ToList();

foreach (var item in result) {
    Console.WriteLine(item);
}
// Output: 6, 8, 10
```

## Common LINQ Operations

### 1. Filtering with Where:

```csharp
var adults = people.Where(p => p.Age >= 18).ToList();
```

### 2. Transforming with Select:

```csharp
var names = people.Select(p => p.Name).ToList();
```

### 3. Sorting with OrderBy:

```csharp
var sorted = people.OrderBy(p => p.Age).ToList();
```

### 4. Grouping with GroupBy:

```csharp
var grouped = people.GroupBy(p => p.City);

foreach (var group in grouped) {
    Console.WriteLine($"City: {group.Key}");
    foreach (var person in group) {
        Console.WriteLine($"  {person.Name}");
    }
}
```

## LINQ with Databases

LINQ can query databases through Entity Framework:

```csharp
var users = dbContext.Users
    .Where(u => u.IsActive)
    .OrderBy(u => u.CreatedDate)
    .ToList();
```

## Advantages of LINQ

1. **Readable**: LINQ syntax is clean and easy to understand.
2. **Type-Safe**: Compile-time type checking prevents errors.
3. **Composable**: Operations can be chained together.
4. **Efficient**: LINQ optimizes queries for better performance.

## Conclusion

LINQ is an essential feature for C# developers that makes data querying and manipulation simpler and more expressive. Mastering LINQ will significantly improve your productivity and code quality.
