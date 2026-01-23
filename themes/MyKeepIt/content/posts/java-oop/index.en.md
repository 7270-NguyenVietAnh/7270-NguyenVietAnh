---
weight: 3
title: "Lập trình Java Hướng Đối Tượng"
date: 2024-12-26T14:00:00+08:00
lastmod: 2024-12-26T14:00:00+08:00
draft: false
author: "ChatGPT"
authorLink: "https://chatgpt.com"
description: "Hướng dẫn về lập trình Java theo phong cách hướng đối tượng"
images: []
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["Java", "Lập Trình Hướng Đối Tượng"]
categories: ["Java"]

lightgallery: true
---

# Giới thiệu về Lập Trình Hướng Đối Tượng trong Java

Lập trình hướng đối tượng (OOP) là một phương pháp lập trình mạnh mẽ giúp tổ chức và xử lý dữ liệu trong các chương trình phức tạp. Java, với tính năng hỗ trợ đầy đủ OOP, là một trong những ngôn ngữ phổ biến nhất được sử dụng để phát triển ứng dụng lớn và mạnh mẽ.

## Các Khái Niệm Chính trong Lập Trình Hướng Đối Tượng

Lập trình hướng đối tượng bao gồm bốn nguyên lý cơ bản:

1. **Encapsulation (Đóng gói)**: Dữ liệu và phương thức được đóng gói thành các đối tượng. Điều này giúp bảo vệ dữ liệu và kiểm soát việc truy cập vào nó.
2. **Abstraction (Trừu tượng)**: Chỉ hiển thị các chi tiết cần thiết và ẩn các chi tiết không cần thiết, giúp giảm độ phức tạp của hệ thống.
3. **Inheritance (Kế thừa)**: Cho phép tạo các lớp con kế thừa các thuộc tính và phương thức từ lớp cha, giúp tái sử dụng mã nguồn.
4. **Polymorphism (Đa hình)**: Cho phép sử dụng một phương thức với các cách thực thi khác nhau, tùy thuộc vào đối tượng gọi nó.

## Cấu trúc của một lớp trong Java

Một lớp trong Java có thể chứa các trường (variables) và phương thức (methods). Dưới đây là ví dụ về một lớp đơn giản trong Java:

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
