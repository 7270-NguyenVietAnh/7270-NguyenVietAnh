---
weight: 6
title: "Chuyên sâu về Lập trình bất đồng bộ trong JavaScript"
date: 2024-12-26T17:00:00+08:00
lastmod: 2024-12-26T17:00:00+08:00
draft: false
author: "ChatGPT"
authorLink: "https://chatgpt.com"
description: "Tìm hiểu sâu về lập trình bất đồng bộ (asynchronous programming) trong JavaScript, bao gồm callbacks, promises và async/await."
images: []
resources:
- name: "featured-image"
  src: "featured-image.jpg"

tags: ["JavaScript", "Asynchronous Programming", "JavaScript Advanced"]
categories: ["JavaScript", "Advanced Concepts"]

lightgallery: true
---

# Chuyên sâu về Lập trình bất đồng bộ trong JavaScript

Lập trình bất đồng bộ là một phần quan trọng của JavaScript, đặc biệt trong việc xử lý các tác vụ như gọi API, đọc/ghi file, hoặc giao tiếp với cơ sở dữ liệu. Hiểu rõ cách thức hoạt động của bất đồng bộ sẽ giúp bạn viết mã hiệu quả và tránh các lỗi khó xử lý.

---

## Lập trình bất đồng bộ là gì?

Lập trình bất đồng bộ cho phép các tác vụ mất thời gian được thực thi mà không chặn luồng chính (main thread). Điều này giúp giao diện người dùng vẫn mượt mà trong khi các tác vụ nền đang chạy.

JavaScript sử dụng **event loop** để quản lý các tác vụ bất đồng bộ, với sự hỗ trợ từ **callbacks**, **promises**, và **async/await**.

---

## Callbacks

### Định nghĩa
> **Callback** là một hàm được truyền làm tham số cho hàm khác và được gọi lại sau khi một tác vụ hoàn thành.

### Ví dụ:

```javascript
function fetchData(callback) {
    setTimeout(() => {
        console.log("Dữ liệu đã được tải.");
        callback("Dữ liệu từ server");
    }, 2000);
}

fetchData((data) => {
    console.log("Callback nhận dữ liệu:", data);
});
```

### Nhược điểm:
- **Callback Hell**: Khi các callbacks lồng nhau quá nhiều, mã trở nên khó đọc và bảo trì.

```javascript
setTimeout(() => {
    console.log("Bước 1");
    setTimeout(() => {
        console.log("Bước 2");
        setTimeout(() => {
            console.log("Bước 3");
        }, 1000);
    }, 1000);
}, 1000);
```

---

## Promises

### Định nghĩa
> **Promise** đại diện cho một giá trị trong tương lai (khi một tác vụ bất đồng bộ hoàn thành).

### Các trạng thái của Promise:
- **Pending**: Đang chờ xử lý.
- **Fulfilled**: Thành công.
- **Rejected**: Thất bại.

### Cú pháp cơ bản:

```javascript
const fetchData = new Promise((resolve, reject) => {
    setTimeout(() => {
        const success = true;
        if (success) {
            resolve("Dữ liệu tải thành công!");
        } else {
            reject("Đã xảy ra lỗi khi tải dữ liệu.");
        }
    }, 2000);
});

fetchData
    .then((data) => {
        console.log("Promise Fulfilled:", data);
    })
    .catch((error) => {
        console.error("Promise Rejected:", error);
    });
```

### Xử lý chuỗi Promise:

```javascript
fetchData
    .then((data) => {
        console.log("Xử lý dữ liệu 1:", data);
        return data + " - bước 2";
    })
    .then((modifiedData) => {
        console.log("Xử lý dữ liệu 2:", modifiedData);
    })
    .catch((error) => {
        console.error("Lỗi xảy ra:", error);
    });
```

---

## Async/Await

### Định nghĩa
> **Async/Await** là cú pháp dựa trên Promise, giúp viết mã bất đồng bộ trông giống mã đồng bộ, dễ đọc hơn.

### Cú pháp cơ bản:

```javascript
async function fetchData() {
    try {
        const data = await new Promise((resolve, reject) => {
            setTimeout(() => resolve("Dữ liệu tải thành công!"), 2000);
        });
        console.log("Async/Await nhận dữ liệu:", data);
    } catch (error) {
        console.error("Lỗi xảy ra:", error);
    }
}

fetchData();
```

### Ưu điểm:
- Giảm thiểu callback hell.
- Dễ đọc và bảo trì hơn.

### Kết hợp nhiều `await`:

```javascript
async function fetchSequentialData() {
    try {
        const data1 = await new Promise((resolve) => setTimeout(() => resolve("Dữ liệu 1"), 1000));
        console.log(data1);

        const data2 = await new Promise((resolve) => setTimeout(() => resolve("Dữ liệu 2"), 1000));
        console.log(data2);

        const data3 = await new Promise((resolve) => setTimeout(() => resolve("Dữ liệu 3"), 1000));
        console.log(data3);
    } catch (error) {
        console.error("Lỗi xảy ra:", error);
    }
}

fetchSequentialData();
```

---

## Ứng dụng thực tế

1. **Gọi API**:

```javascript
async function fetchApiData() {
    try {
        const response = await fetch("https://jsonplaceholder.typicode.com/posts");
        const data = await response.json();
        console.log("Dữ liệu từ API:", data);
    } catch (error) {
        console.error("Lỗi khi gọi API:", error);
    }
}

fetchApiData();
```

2. **Xử lý song song với `Promise.all`**:

```javascript
async function fetchParallelData() {
    try {
        const [data1, data2] = await Promise.all([
            fetch("https://jsonplaceholder.typicode.com/posts/1").then(res => res.json()),
            fetch("https://jsonplaceholder.typicode.com/posts/2").then(res => res.json())
        ]);

        console.log("Dữ liệu 1:", data1);
        console.log("Dữ liệu 2:", data2);
    } catch (error) {
        console.error("Lỗi xảy ra:", error);
    }
}

fetchParallelData();
```

---

## Kết luận

Hiểu rõ về lập trình bất đồng bộ trong JavaScript giúp bạn xử lý các tác vụ phức tạp một cách dễ dàng và hiệu quả hơn. Từ callbacks, promises, đến async/await, mỗi công cụ đều có ưu và nhược điểm, phù hợp với từng tình huống cụ thể.
