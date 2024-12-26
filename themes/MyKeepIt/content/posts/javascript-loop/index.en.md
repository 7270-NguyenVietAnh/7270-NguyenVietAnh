---
weight: 7
title: "Chuyên sâu về Event Loop trong JavaScript"
date: 2024-12-26T18:00:00+08:00
lastmod: 2024-12-26T18:00:00+08:00
draft: false
author: "ChatGPT"
authorLink: "https://chatgpt.com"
description: "Khám phá cơ chế Event Loop trong JavaScript, giúp hiểu rõ cách xử lý bất đồng bộ và ưu tiên thực thi trong ngôn ngữ này."
images: []
resources:
- name: "featured-image"
  src: "featured-image.jpg"

tags: ["JavaScript", "Event Loop", "JavaScript Advanced"]
categories: ["JavaScript", "Advanced Concepts"]

lightgallery: true
---

# Chuyên sâu về Event Loop trong JavaScript

Event Loop là trái tim của JavaScript, giúp quản lý và điều phối các tác vụ bất đồng bộ. Hiểu rõ về Event Loop là chìa khóa để giải thích tại sao một số đoạn mã JavaScript lại hoạt động như vậy.

---

## Event Loop là gì?

JavaScript là một ngôn ngữ đơn luồng (**single-threaded**), nhưng nó có thể xử lý nhiều tác vụ bất đồng bộ nhờ cơ chế Event Loop. Event Loop chịu trách nhiệm:
- Lắng nghe các sự kiện từ hàng đợi (queue).
- Quản lý luồng chính (call stack).
- Đảm bảo các tác vụ bất đồng bộ thực thi đúng thứ tự.

---

## Các thành phần chính

1. **Call Stack**: Là nơi các lệnh JavaScript được thực thi tuần tự.
2. **Web APIs**: Cung cấp môi trường chạy các tác vụ bất đồng bộ như `setTimeout`, `fetch`, hoặc DOM events.
3. **Callback Queue**: Hàng đợi nơi các callback chờ được thực thi sau khi call stack rỗng.
4. **Event Loop**: Theo dõi call stack và callback queue để quyết định khi nào đưa một hàm từ queue vào stack.

---

## Cách hoạt động của Event Loop

### 1. Đồng bộ:
Các lệnh được thực thi trực tiếp trong **call stack**.

```javascript
console.log("Start");
console.log("End");
// Output:
// Start
// End
```

### 2. Bất đồng bộ:
Các tác vụ như `setTimeout`, `fetch` được chuyển sang **Web APIs** để xử lý. Khi hoàn thành, chúng đưa callback vào **callback queue** và đợi call stack rỗng để thực thi.

```javascript
console.log("Start");
setTimeout(() => {
    console.log("Timeout");
}, 1000);
console.log("End");
// Output:
// Start
// End
// Timeout
```

---

## Microtasks và Macrotasks

### Microtasks:
- Bao gồm: `Promise.then`, `MutationObserver`.
- Ưu tiên cao hơn macrotasks.

### Macrotasks:
- Bao gồm: `setTimeout`, `setInterval`, `setImmediate` (Node.js).

### Thứ tự thực thi:
1. Thực thi call stack.
2. Thực thi tất cả microtasks.
3. Thực thi một macrotask.
4. Quay lại bước 1.

Ví dụ minh họa:

```javascript
console.log("Start");

setTimeout(() => {
    console.log("Macrotask");
}, 0);

Promise.resolve().then(() => {
    console.log("Microtask");
});

console.log("End");
// Output:
// Start
// End
// Microtask
// Macrotask
```

---

## Ví dụ minh họa Event Loop

### 1. Hàng đợi callback:

```javascript
console.log("Start");

setTimeout(() => {
    console.log("Timeout 1");
}, 1000);

setTimeout(() => {
    console.log("Timeout 2");
}, 500);

console.log("End");
// Output:
// Start
// End
// Timeout 2
// Timeout 1
```

### 2. Kết hợp Microtasks và Macrotasks:

```javascript
console.log("Start");

setTimeout(() => {
    console.log("Macrotask 1");

    Promise.resolve().then(() => {
        console.log("Microtask 1 inside Macrotask 1");
    });
}, 0);

Promise.resolve().then(() => {
    console.log("Microtask 1");
});

setTimeout(() => {
    console.log("Macrotask 2");
}, 0);

console.log("End");
// Output:
// Start
// End
// Microtask 1
// Macrotask 1
// Microtask 1 inside Macrotask 1
// Macrotask 2
```

---

## Event Loop trong Node.js

Trong Node.js, Event Loop được chia thành các giai đoạn:
1. **Timers**: Xử lý các callback từ `setTimeout` và `setInterval`.
2. **Pending Callbacks**: Xử lý các callback bị trì hoãn.
3. **Idle, Prepare**: Sử dụng nội bộ.
4. **Poll**: Nhận các sự kiện mới và thực thi I/O callbacks.
5. **Check**: Xử lý `setImmediate` callbacks.
6. **Close Callbacks**: Đóng các callback như `socket.on('close')`.

---

## Ứng dụng thực tế

### 1. Tối ưu hóa hiệu suất:
Hiểu Event Loop giúp tránh chặn luồng chính, đặc biệt trong các ứng dụng giao diện người dùng hoặc xử lý I/O.

### 2. Xử lý tác vụ bất đồng bộ phức tạp:
Kết hợp microtasks và macrotasks để đảm bảo thứ tự thực thi đúng như mong đợi.

### 3. Debugging:
Hiểu cơ chế Event Loop giúp bạn dễ dàng phát hiện và sửa các vấn đề như race conditions hay deadlocks.

---

## Kết luận

Event Loop là một cơ chế quan trọng, giúp JavaScript mạnh mẽ trong việc xử lý bất đồng bộ. Hiểu rõ cách hoạt động của nó giúp bạn viết mã hiệu quả và tránh các lỗi phổ biến.
