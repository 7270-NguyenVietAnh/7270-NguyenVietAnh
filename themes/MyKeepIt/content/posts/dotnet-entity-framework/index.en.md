---
weight: 16
title: "Entity Framework Core in .NET"
date: 2024-12-27T16:00:00+08:00
lastmod: 2024-12-27T16:00:00+08:00
draft: false
author: "ChatGPT"
authorLink: "https://chatgpt.com"
description: "Learn Entity Framework Core, a modern ORM for data access in .NET applications."
images: []
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: [".NET", "Entity Framework", "Database", "ORM"]
categories: [".NET", "Advanced Concepts"]

lightgallery: true
---

# Entity Framework Core in .NET

Entity Framework Core (EF Core) is a lightweight, extensible, and open-source Object-Relational Mapping (ORM) framework for .NET. It simplifies database operations by allowing you to work with database objects as .NET objects.

## What is Entity Framework Core?

EF Core enables developers to work with databases using C# objects instead of writing raw SQL queries. It supports multiple database providers including SQL Server, PostgreSQL, SQLite, and MySQL.

## Creating Models

Define your data models:

```csharp
public class User {
    public int Id { get; set; }
    public string Name { get; set; }
    public string Email { get; set; }
    public DateTime CreatedDate { get; set; }
}

public class Post {
    public int Id { get; set; }
    public string Title { get; set; }
    public string Content { get; set; }
    public int UserId { get; set; }
    public User User { get; set; }
}
```

## Database Context

Create a DbContext to manage database operations:

```csharp
public class AppDbContext : DbContext {
    public DbSet<User> Users { get; set; }
    public DbSet<Post> Posts { get; set; }

    protected override void OnConfiguring(DbContextOptionsBuilder options) {
        options.UseSqlServer("Server=localhost;Database=mydb;Trusted_Connection=true;");
    }
}
```

## Basic CRUD Operations

### Create

```csharp
using (var db = new AppDbContext()) {
    var user = new User { Name = "John", Email = "john@example.com" };
    db.Users.Add(user);
    db.SaveChanges();
}
```

### Read

```csharp
using (var db = new AppDbContext()) {
    var users = db.Users.ToList();
    var user = db.Users.FirstOrDefault(u => u.Id == 1);
}
```

### Update

```csharp
using (var db = new AppDbContext()) {
    var user = db.Users.Find(1);
    user.Name = "Jane";
    db.SaveChanges();
}
```

### Delete

```csharp
using (var db = new AppDbContext()) {
    var user = db.Users.Find(1);
    db.Users.Remove(user);
    db.SaveChanges();
}
```

## Relationships

### One-to-Many

```csharp
public class Author {
    public int Id { get; set; }
    public string Name { get; set; }
    public List<Book> Books { get; set; }
}

public class Book {
    public int Id { get; set; }
    public string Title { get; set; }
    public int AuthorId { get; set; }
    public Author Author { get; set; }
}
```

## Querying with LINQ

```csharp
var recentPosts = db.Posts
    .Where(p => p.CreatedDate > DateTime.Now.AddMonths(-1))
    .OrderByDescending(p => p.CreatedDate)
    .ToList();
```

## Migrations

Entity Framework provides migrations to manage database schema changes:

```bash
dotnet ef migrations add InitialCreate
dotnet ef database update
```

## Key Advantages

1. **Type-Safe**: Compile-time checking of database queries.
2. **Productivity**: Less boilerplate code compared to raw SQL.
3. **Flexibility**: Works with multiple database providers.
4. **Relationships**: Automatic handling of foreign keys and relationships.

## Conclusion

Entity Framework Core is an essential tool for .NET developers working with databases. It provides a clean, abstracted way to interact with data, making applications more maintainable and testable.
