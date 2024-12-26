---
weight: 1
title: "Java Cơ Bản"
date: 2024-12-26T12:00:00+08:00
lastmod: 2024-12-26T12:00:00+08:00
draft: false
author: "ChatGPT"
authorLink: "https://chatgpt.com"
description: "Java cơ bản"
images: []
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["Java"]
categories: ["Java"]

lightgallery: true
---

# Giới thiệu về Java

Java là một ngôn ngữ lập trình hướng đối tượng, được phát triển bởi Sun Microsystems vào năm 1995. Java là một trong những ngôn ngữ phổ biến nhất trên thế giới nhờ tính đơn giản, tính di động, và khả năng mở rộng.

## Đặc điểm của Java

1. **Hướng đối tượng**: Java hỗ trợ đầy đủ các khái niệm hướng đối tượng như kế thừa, đóng gói, đa hình và trừu tượng.
2. **Độc lập nền tảng**: Java sử dụng Java Virtual Machine (JVM) để chạy mã, do đó bạn chỉ cần viết mã một lần và có thể chạy trên nhiều nền tảng khác nhau.
3. **Bảo mật**: Java được thiết kế với các cơ chế bảo mật tích hợp, giúp bảo vệ ứng dụng khỏi các cuộc tấn công.
4. **Hiệu năng cao**: Mặc dù Java không nhanh như C++, JVM và các tối ưu hóa của Java đã giúp cải thiện hiệu suất đáng kể.
5. **Thư viện phong phú**: Java cung cấp rất nhiều thư viện và API hỗ trợ cho việc phát triển ứng dụng từ đơn giản đến phức tạp.

## Cấu trúc cơ bản của một chương trình Java

Dưới đây là ví dụ về một chương trình Java đơn giản:

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Xin chào thế giới!");
    }
}
```

### Giải thích:
- `public class HelloWorld`: Khai báo một lớp có tên là `HelloWorld`.
- `public static void main(String[] args)`: Đây là phương thức chính, nơi chương trình bắt đầu thực thi.
- `System.out.println`: In một dòng văn bản ra màn hình.

## Các kiểu dữ liệu trong Java

Java hỗ trợ nhiều kiểu dữ liệu khác nhau, bao gồm:

1. **Kiểu nguyên thủy**:
   - `int`: Số nguyên.
   - `float`: Số thực dấu phẩy động.
   - `char`: Ký tự.
   - `boolean`: Giá trị đúng/sai.
2. **Kiểu tham chiếu**:
   - Đối tượng (object).
   - Mảng (array).

Ví dụ:

```java
int age = 25;
float height = 1.75f;
char gender = 'M';
boolean isStudent = true;
```

## Các câu lệnh điều kiện

Java cung cấp các câu lệnh điều kiện để kiểm soát luồng thực thi của chương trình, chẳng hạn:

### If-Else:

```java
if (age > 18) {
    System.out.println("Bạn đã đủ tuổi.");
} else {
    System.out.println("Bạn chưa đủ tuổi.");
}
```

### Switch:

```java
switch (day) {
    case 1:
        System.out.println("Chủ nhật");
        break;
    case 2:
        System.out.println("Thứ hai");
        break;
    default:
        System.out.println("Không hợp lệ");
}
```

## Vòng lặp trong Java

Java hỗ trợ nhiều loại vòng lặp để lặp lại các thao tác:

### Vòng lặp For:

```java
for (int i = 0; i < 5; i++) {
    System.out.println("Lặp lần: " + i);
}
```

### Vòng lặp While:

```java
int i = 0;
while (i < 5) {
    System.out.println("Lặp lần: " + i);
    i++;
}
```

## Kết luận

Java là một ngôn ngữ mạnh mẽ, dễ học và phù hợp với nhiều loại ứng dụng, từ ứng dụng di động, web, đến các hệ thống lớn. Hiểu rõ các khái niệm cơ bản là bước đầu tiên để trở thành một lập trình viên Java chuyên nghiệp.
