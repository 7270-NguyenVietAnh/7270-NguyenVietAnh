---
weight: 5
title: "Deep Understanding of Java Stream API"
date: 2024-12-26T16:00:00+08:00
lastmod: 2024-12-26T16:00:00+08:00
draft: false
author: "ChatGPT"
authorLink: "https://chatgpt.com"
description: "In-depth understanding of Stream API in Java 8, a powerful feature that helps process data more efficiently and concisely."
images: []
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["Java", "Stream API", "Java 8"]
categories: ["Java", "Advanced Concepts"]

lightgallery: true
---

# Deep Understanding of Java Stream API

**Java Stream API** is a powerful feature introduced from Java 8, helping to process collections of data easily, efficiently, and more concisely. Stream API helps programmers focus on **what to do** rather than **how to do it**.

---

## What is Stream API?

### Definition:
> **Stream API** is a tool that supports data processing in a declarative way by providing operations such as filtering, sorting, and transformation on data sets.

---

## Characteristics of Stream

- **No Storage**: Stream does not store data; they operate on data sources (collections, arrays).
- **Immutable**: Each operation on Stream returns a new Stream without changing the original Stream.
- **Lazy Evaluation**: Operations are only executed when necessary (when there is a terminal operation).
- **Parallelizable**: Stream supports parallel data processing, optimizing performance.

---

## Stream Operations

Stream API provides 3 main types of operations:

### 1. **Stream Creation**

Stream can be created from many sources such as collections, arrays, or files.

```java
import java.util.*;
import java.util.stream.*;

public class StreamCreationExample {
    public static void main(String[] args) {
        // Create Stream from a list
        List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
        Stream<String> streamFromList = names.stream();

        // Create Stream from an array
        int[] numbers = {1, 2, 3, 4};
        IntStream streamFromArray = Arrays.stream(numbers);

        // Create Stream from a string
        Stream<String> streamFromString = Stream.of("A", "B", "C");

        // Create infinite Stream
        Stream<Integer> infiniteStream = Stream.iterate(0, n -> n + 2);
        infiniteStream.limit(5).forEach(System.out::println); // Output: 0, 2, 4, 6, 8
    }
}
```

---

### 2. **Intermediate Operations**

Intermediate operations perform data transformation and return a new Stream. They do not execute immediately but wait until there is a terminal operation.

- **`filter`**: Filters elements that satisfy a condition.
- **`map`**: Transforms elements from one type to another.
- **`sorted`**: Sorts elements in natural order or by comparator.
- **`distinct`**: Removes duplicate elements.

Example:

```java
import java.util.*;
import java.util.stream.*;

public class IntermediateOperationsExample {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("Alice", "Bob", "Charlie", "Alice");

        names.stream()
            .filter(name -> name.startsWith("A"))
            .distinct()
            .sorted()
            .forEach(System.out::println); // Output: Alice
    }
}
```

---

### 3. **Terminal Operations**

Terminal operations execute a chain of intermediate operations and return the final result.

- **`forEach`**: Iterates through each element and performs an action.
- **`collect`**: Collects results into a collection or other data type.
- **`reduce`**: Combines elements into a single value.
- **`count`**: Counts the number of elements.

Example:

```java
import java.util.*;
import java.util.stream.*;

public class TerminalOperationsExample {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);

        int sum = numbers.stream()
            .reduce(0, Integer::sum);

        System.out.println("Sum: " + sum); // Output: Sum: 15

        List<Integer> squaredNumbers = numbers.stream()
            .map(n -> n * n)
            .collect(Collectors.toList());

        System.out.println("Squared Numbers: " + squaredNumbers); // Output: Squared Numbers: [1, 4, 9, 16, 25]
    }
}
```

---

## Real-World Applications of Stream API

1. **Complex Data Processing**: Stream API helps write more readable code when processing large or complex data sets.
2. **Improved Performance**: With parallel processing capability, Stream API reduces data processing time for large data.
3. **Easy Maintenance**: Code using Stream API is easy to extend and maintain thanks to clear declarative syntax.

Example application:

```java
import java.util.*;
import java.util.stream.*;

public class RealWorldExample {
    public static void main(String[] args) {
        List<Employee> employees = Arrays.asList(
            new Employee("Alice", 3000),
            new Employee("Bob", 4000),
            new Employee("Charlie", 5000),
            new Employee("David", 2000)
        );

        // Filter employees with salary above 3000 and get their names
        List<String> highEarners = employees.stream()
            .filter(emp -> emp.getSalary() > 3000)
            .map(Employee::getName)
            .collect(Collectors.toList());

        System.out.println("High Earners: " + highEarners); // Output: High Earners: [Bob, Charlie]
    }
}

class Employee {
    private String name;
    private int salary;

    public Employee(String name, int salary) {
        this.name = name;
        this.salary = salary;
    }

    public String getName() {
        return name;
    }

    public int getSalary() {
        return salary;
    }
}
```

---

## Conclusion

Stream API is a powerful tool that helps simplify data processing in Java. With clear syntax and parallel processing capability, it becomes an indispensable part for modern Java programmers.
