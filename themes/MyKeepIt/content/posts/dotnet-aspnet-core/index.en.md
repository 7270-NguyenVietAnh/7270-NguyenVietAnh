---
weight: 17
title: "ASP.NET Core Web Development"
date: 2024-12-27T17:00:00+08:00
lastmod: 2024-12-27T17:00:00+08:00
draft: false
author: "ChatGPT"
authorLink: "https://chatgpt.com"
description: "Master ASP.NET Core for building modern, scalable web applications."
images: []
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: [".NET", "ASP.NET Core", "Web Development"]
categories: [".NET", "Advanced Concepts"]

lightgallery: true
---

# ASP.NET Core Web Development

ASP.NET Core is a cross-platform, high-performance framework for building modern web applications, APIs, and real-time services. It is the latest evolution of ASP.NET and offers significant improvements over the traditional ASP.NET Framework.

## What is ASP.NET Core?

ASP.NET Core is a unified framework that combines ASP.NET MVC and ASP.NET Web API into a single platform. It supports building:
- Web applications
- REST APIs
- Real-time applications (SignalR)
- Microservices

## Creating an ASP.NET Core Project

```bash
dotnet new mvc -n MyWebApp
cd MyWebApp
dotnet run
```

## Project Structure

```
MyWebApp/
├── Controllers/      # Handle requests
├── Views/           # HTML templates
├── Models/          # Data models
├── wwwroot/         # Static files
├── Startup.cs       # Configuration
└── Program.cs       # Entry point
```

## MVC Pattern

### Model

```csharp
public class Product {
    public int Id { get; set; }
    public string Name { get; set; }
    public decimal Price { get; set; }
}
```

### View

```html
@model List<Product>

<h1>Products</h1>
<table>
    <tr>
        <th>Name</th>
        <th>Price</th>
    </tr>
    @foreach (var product in Model) {
        <tr>
            <td>@product.Name</td>
            <td>@product.Price</td>
        </tr>
    }
</table>
```

### Controller

```csharp
public class ProductController : Controller {
    private readonly IProductService _service;

    public ProductController(IProductService service) {
        _service = service;
    }

    public IActionResult Index() {
        var products = _service.GetAllProducts();
        return View(products);
    }

    public IActionResult Details(int id) {
        var product = _service.GetProductById(id);
        if (product == null) return NotFound();
        return View(product);
    }
}
```

## Creating REST APIs

```csharp
[ApiController]
[Route("api/[controller]")]
public class ApiProductController : ControllerBase {
    [HttpGet("{id}")]
    public ActionResult<Product> GetProduct(int id) {
        var product = db.Products.Find(id);
        if (product == null) return NotFound();
        return Ok(product);
    }

    [HttpPost]
    public ActionResult<Product> CreateProduct(Product product) {
        db.Products.Add(product);
        db.SaveChanges();
        return CreatedAtAction(nameof(GetProduct), new { id = product.Id }, product);
    }

    [HttpPut("{id}")]
    public IActionResult UpdateProduct(int id, Product product) {
        var existing = db.Products.Find(id);
        if (existing == null) return NotFound();
        
        existing.Name = product.Name;
        existing.Price = product.Price;
        db.SaveChanges();
        return NoContent();
    }

    [HttpDelete("{id}")]
    public IActionResult DeleteProduct(int id) {
        var product = db.Products.Find(id);
        if (product == null) return NotFound();
        
        db.Products.Remove(product);
        db.SaveChanges();
        return NoContent();
    }
}
```

## Middleware

Middleware components process HTTP requests and responses:

```csharp
public void Configure(IApplicationBuilder app) {
    app.UseRouting();
    
    app.UseEndpoints(endpoints => {
        endpoints.MapControllers();
    });
}
```

## Dependency Injection Integration

ASP.NET Core has built-in DI:

```csharp
public void ConfigureServices(IServiceCollection services) {
    services.AddScoped<IProductService, ProductService>();
    services.AddControllers();
}
```

## Key Features

1. **Cross-Platform**: Runs on Windows, Linux, and macOS.
2. **High Performance**: One of the fastest web frameworks.
3. **Built-in DI**: Dependency Injection out of the box.
4. **Unified Platform**: One framework for web and APIs.
5. **Microservices Ready**: Easy to build distributed systems.

## Conclusion

ASP.NET Core is a powerful and modern framework for building web applications and APIs. Its cross-platform nature, high performance, and rich feature set make it an excellent choice for building scalable web solutions.
