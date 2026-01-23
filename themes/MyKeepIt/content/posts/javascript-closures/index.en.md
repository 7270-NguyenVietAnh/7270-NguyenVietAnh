---
weight: 4
title: "Hiểu sâu về Closures trong JavaScript"
date: 2024-12-26T15:00:00+08:00
lastmod: 2024-12-26T15:00:00+08:00
draft: false
author: "ChatGPT"
authorLink: "https://chatgpt.com"
description: "Tìm hiểu chuyên sâu về JavaScript Closures, một trong những khái niệm quan trọng trong lập trình JavaScript."
images: []
resources:
- name: "featured-image"
  src: "featured-image.png"

tags: ["JavaScript", "Closures", "Advanced JavaScript"]
categories: ["JavaScript", "Advanced Concepts"]

lightgallery: true
---

# Hiểu sâu về Closures trong JavaScript

**Closures** là một trong những khái niệm mạnh mẽ và thường gây nhầm lẫn trong JavaScript. Chúng ta sẽ tìm hiểu closures là gì, cách chúng hoạt động, và tại sao chúng rất quan trọng trong lập trình JavaScript.

---

## Closures là gì?

Closures xảy ra khi một hàm "nhớ" được phạm vi (scope) nơi nó được tạo ra, ngay cả khi hàm đó được gọi bên ngoài phạm vi đó.

### Định nghĩa:
> **Closure** là sự kết hợp giữa một hàm và phạm vi từ vựng (lexical environment) mà hàm được định nghĩa.

---

## Ví dụ cơ bản về Closures

Hãy cùng xem một ví dụ đơn giản để hiểu rõ hơn:

```javascript
function outerFunction() {
  let outerVariable = "I am from outer scope";

  function innerFunction() {
    console.log(outerVariable);
  }

  return innerFunction;
}

const closureFunction = outerFunction();
closureFunction(); // Output: "I am from outer scope"
