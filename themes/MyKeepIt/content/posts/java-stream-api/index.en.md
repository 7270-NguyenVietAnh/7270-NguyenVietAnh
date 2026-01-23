---
weight: 5
title: "Hiểu sâu về Java Stream API"
date: 2024-12-26T16:00:00+08:00
lastmod: 2024-12-26T16:00:00+08:00
draft: false
author: "ChatGPT"
authorLink: "https://chatgpt.com"
description: "Tìm hiểu chuyên sâu về Stream API trong Java 8, một tính năng mạnh mẽ giúp xử lý dữ liệu hiệu quả và ngắn gọn hơn."
images: []
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["Java", "Stream API", "Java 8"]
categories: ["Java", "Advanced Concepts"]

lightgallery: true
---

# Hiểu sâu về Java Stream API

**Java Stream API** là một tính năng mạnh mẽ được giới thiệu từ Java 8, giúp xử lý các bộ sưu tập dữ liệu (collections) dễ dàng, hiệu quả và ngắn gọn hơn. Stream API giúp lập trình viên tập trung vào **cái cần làm** (what to do) thay vì **cách làm** (how to do).

---

## Stream API là gì?

### Định nghĩa:
> **Stream API** là một công cụ hỗ trợ xử lý dữ liệu theo cách khai báo (declarative) bằng cách cung cấp các thao tác như lọc, sắp xếp và chuyển đổi trên các bộ dữ liệu.

---

## Đặc điểm của Stream

- **Không lưu trữ (No Storage)**: Stream không lưu trữ dữ liệu; chúng hoạt động trên các nguồn dữ liệu (collections, arrays).
- **Bất biến (Immutable)**: Mỗi thao tác trên Stream trả về một Stream mới mà không thay đổi Stream ban đầu.
- **Lười biếng (Lazy Evaluation)**: Các thao tác chỉ được thực thi khi cần thiết (khi có thao tác terminal).
- **Song song hóa dễ dàng (Parallelizable)**: Stream hỗ trợ xử lý dữ liệu song song, tối ưu hóa hiệu suất.

---

## Các thao tác trên Stream

Stream API cung cấp 3 loại thao tác chính:

### 1. **Tạo Stream (Stream Creation)**

Stream có thể được tạo từ nhiều nguồn như collections, arrays, hoặc files.

```java
import java.util.*;
import java.util.stream.*;

public class StreamCreationExample {
    public static void main(String[] args) {
        // Tạo Stream từ một danh sách
        List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
        Stream<String> streamFromList = names.stream();

        // Tạo Stream từ một mảng
        int[] numbers = {1, 2, 3, 4};
        IntStream streamFromArray = Arrays.stream(numbers);

        // Tạo Stream từ một chuỗi
        Stream<String> streamFromString = Stream.of("A", "B", "C");

        // Tạo Stream vô hạn
        Stream<Integer> infiniteStream = Stream.iterate(0, n -> n + 2);
        infiniteStream.limit(5).forEach(System.out::println); // Output: 0, 2, 4, 6, 8
    }
}
```

---

### 2. **Thao tác trung gian (Intermediate Operations)**

Thao tác trung gian thực hiện biến đổi dữ liệu và trả về một Stream mới. Chúng không thực thi ngay mà đợi đến khi có thao tác kết thúc.

- **`filter`**: Lọc các phần tử thỏa mãn điều kiện.
- **`map`**: Chuyển đổi các phần tử từ kiểu này sang kiểu khác.
- **`sorted`**: Sắp xếp các phần tử theo thứ tự tự nhiên hoặc theo comparator.
- **`distinct`**: Loại bỏ các phần tử trùng lặp.

Ví dụ:

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

### 3. **Thao tác kết thúc (Terminal Operations)**

Thao tác kết thúc thực thi chuỗi các thao tác trung gian và trả về kết quả cuối cùng.

- **`forEach`**: Duyệt qua từng phần tử và thực hiện một hành động.
- **`collect`**: Thu thập kết quả thành một collection hoặc kiểu dữ liệu khác.
- **`reduce`**: Gộp các phần tử lại thành một giá trị duy nhất.
- **`count`**: Đếm số lượng phần tử.

Ví dụ:

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

## Ứng dụng thực tế của Stream API

1. **Xử lý dữ liệu phức tạp**: Stream API giúp viết mã dễ đọc hơn khi xử lý các bộ dữ liệu lớn hoặc phức tạp.
2. **Cải thiện hiệu suất**: Với khả năng xử lý song song, Stream API giảm thời gian xử lý dữ liệu lớn.
3. **Dễ dàng bảo trì**: Code sử dụng Stream API dễ dàng mở rộng và bảo trì nhờ cú pháp khai báo rõ ràng.

Ví dụ ứng dụng:

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

        // Lọc những nhân viên có lương trên 3000 và lấy tên của họ
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

## Kết luận

Stream API là một công cụ mạnh mẽ giúp đơn giản hóa việc xử lý dữ liệu trong Java. Với cú pháp rõ ràng và khả năng xử lý song song, nó trở thành một phần không thể thiếu cho các lập trình viên Java hiện đại.
