---
weight: 14
title: ".NET Basics"
date: 2024-12-27T14:00:00+08:00
lastmod: 2024-12-27T14:00:00+08:00
draft: false
author: "ChatGPT"
authorLink: "https://chatgpt.com"
description: "Learn the fundamentals of .NET, a powerful framework for building modern applications."
images: []
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: [".NET", "Framework"]
categories: [".NET"]

lightgallery: true
---

# Introduction to .NET

.NET is a free, open-source, cross-platform framework developed by Microsoft for building web, desktop, mobile, and cloud applications. It provides a unified platform for developing applications with C#, Visual Basic, or F#.

## What is .NET?

.NET is a runtime and library framework that enables developers to build applications that run on Windows, Linux, and macOS. It comes in several versions:
- **.NET Framework**: The original Windows-only framework.
- **.NET Core**: A cross-platform, open-source version.
- **.NET 5+**: The unified platform combining Core and Framework.

## Key Components

1. **Common Language Runtime (CLR)**: Manages code execution, memory, and exceptions.
2. **Base Class Library (BCL)**: Provides pre-built functionality for common tasks.
3. **Language Support**: C#, Visual Basic, F#, and others.

## Setting Up .NET Environment

### Installation

Download and install .NET SDK from [dotnet.microsoft.com](https://dotnet.microsoft.com)

### Create Your First Project

```bash
dotnet new console -n MyApp
cd MyApp
dotnet run
```

## Hello World in .NET

```csharp
using System;

class Program {
    static void Main() {
        Console.WriteLine("Hello, .NET!");
    }
}
```

## Project Structure

A typical .NET project includes:
- **Program.cs**: Entry point of the application
- **.csproj**: Project configuration file
- **bin/**: Compiled output folder
- **obj/**: Temporary build files

## .NET CLI Commands

```bash
dotnet new              # Create new project
dotnet build            # Compile the project
dotnet run              # Run the application
dotnet test             # Run unit tests
dotnet publish          # Publish for production
dotnet restore          # Restore dependencies
```

## Advantages of .NET

1. **Cross-Platform**: Run on Windows, Linux, and macOS.
2. **High Performance**: Optimized runtime and JIT compilation.
3. **Open Source**: Free and community-driven.
4. **Rich Ecosystem**: Extensive libraries and frameworks.
5. **Unified Platform**: Single framework for all application types.

## Conclusion

.NET is a modern, powerful framework that makes it easy to build scalable and maintainable applications. Understanding its fundamentals is essential for any developer targeting the .NET ecosystem.
