---
weight: 15
title: "Dependency Injection in .NET"
date: 2024-12-27T15:00:00+08:00
lastmod: 2024-12-27T15:00:00+08:00
draft: false
author: "ChatGPT"
authorLink: "https://chatgpt.com"
description: "Master Dependency Injection (DI) in .NET for building loosely coupled and testable applications."
images: []
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: [".NET", "Dependency Injection", "Design Pattern"]
categories: [".NET", "Advanced Concepts"]

lightgallery: true
---

# Dependency Injection in .NET

Dependency Injection (DI) is a design pattern that helps create loosely coupled, maintainable, and testable code. .NET has built-in support for DI through the `IServiceProvider` interface.

## What is Dependency Injection?

Dependency Injection is a technique where objects declare their dependencies rather than creating them internally. This promotes loose coupling and makes code more flexible and testable.

## Traditional Approach (Without DI)

```csharp
public class UserService {
    private DatabaseConnection _db;

    public UserService() {
        _db = new DatabaseConnection();  // Hard dependency
    }
}
```

## DI Approach

```csharp
public interface IDatabaseConnection {
    void Connect();
}

public class DatabaseConnection : IDatabaseConnection {
    public void Connect() {
        Console.WriteLine("Database connected");
    }
}

public class UserService {
    private IDatabaseConnection _db;

    public UserService(IDatabaseConnection db) {
        _db = db;  // Injected dependency
    }
}
```

## Configuring DI in .NET

In ASP.NET Core, configure DI in `Startup.cs` or `Program.cs`:

```csharp
public class Startup {
    public void ConfigureServices(IServiceCollection services) {
        // Register services
        services.AddScoped<IDatabaseConnection, DatabaseConnection>();
        services.AddScoped<IUserService, UserService>();
    }
}
```

## Service Lifetimes

1. **Transient**: New instance created every time
   ```csharp
   services.AddTransient<IService, Service>();
   ```

2. **Scoped**: One instance per HTTP request
   ```csharp
   services.AddScoped<IService, Service>();
   ```

3. **Singleton**: One instance for the entire application
   ```csharp
   services.AddSingleton<IService, Service>();
   ```

## Using Injected Dependencies

```csharp
public class UserController {
    private readonly IUserService _userService;

    public UserController(IUserService userService) {
        _userService = userService;
    }

    public void GetUser(int id) {
        var user = _userService.GetUser(id);
    }
}
```

## Benefits of Dependency Injection

1. **Loose Coupling**: Classes don't depend on concrete implementations.
2. **Testability**: Easy to mock dependencies in unit tests.
3. **Maintainability**: Changes to implementations don't affect consumer code.
4. **Flexibility**: Easy to swap implementations.

## Dependency Injection Example

```csharp
public interface ILogger {
    void Log(string message);
}

public class ConsoleLogger : ILogger {
    public void Log(string message) {
        Console.WriteLine(message);
    }
}

public class FileLogger : ILogger {
    public void Log(string message) {
        System.IO.File.AppendAllText("log.txt", message);
    }
}

// Register in DI container
services.AddScoped<ILogger, ConsoleLogger>();

// Usage
public class Application {
    private readonly ILogger _logger;

    public Application(ILogger logger) {
        _logger = logger;
    }

    public void Run() {
        _logger.Log("Application started");
    }
}
```

## Conclusion

Dependency Injection is a fundamental pattern in .NET that improves code quality, testability, and maintainability. Mastering DI is essential for writing professional .NET applications.
