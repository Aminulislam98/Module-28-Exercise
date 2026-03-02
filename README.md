# Module 28 Practice (Beginner Friendly)

> 📌 এই এক্সারসাইজগুলো সম্পূর্ণ **Module 28** এর উপর ভিত্তি করে (Internet, HTTP/HTTPS, API, JSON, fetch, UI rendering, conditional rendering, CRUD, async/await, debugger)  
> ✅ **Rule:** আগে নিজে চেষ্টা করবে। না পারলে hint দেখবে। Copy-পaste না।

---

## 28-1 Internet, HTTP vs HTTPS, API

### 🧠 সহজ বোঝা

- **Internet** = অনেক কম্পিউটার কানেক্টেড
- **HTTP** = browser ↔ server কথা বলার নিয়ম
- **HTTPS** = secure version (S = Secure)
- **API** = server থেকে data নেওয়ার দরজা

### ✅ Exercise

1. Browser এ যেকোনো website খুলে URL দেখো
2. দেখো **http** না **https**
3. Inspect → **Network tab** খুলে refresh দাও
4. কতগুলো request যাচ্ছে? কোনটা document, কোনটা image/script?

### 🎯 কেন practice?

Network না বুঝলে API বুঝবে না।

---

## 28-2 API & JSON

### 🧠 সহজ বোঝা

- API সাধারণত **JSON format** এ data দেয়
- JSON দেখতে **object/array** এর মতো

### ✅ Exercise

এই লিংক ব্রাউজারে দাও:  
https://jsonplaceholder.typicode.com/users

কাজ:

- এটা **array** না **object**?
- প্রথম item এর **name** কী?

### ✅ Hint (খুব সহজ)

- `[` দিয়ে শুরু হলে → **Array**
- `{` দিয়ে শুরু হলে → **Object**
- Array হলে প্রথম item = **index 0**
- 0 নম্বর item এর ভেতরে `name` খুঁজবে

### 🎯 কেন practice?

Data structure না বুঝলে coding ভেঙে যাবে।

---

## 28-3 Fetch দিয়ে JSON Load

### 🧠 সহজ বোঝা

- `fetch()` = server থেকে data আনা

### ✅ Exercise

Users API fetch করো (UI না, শুধু console):

- fetch করো
- response কে json করো
- console.log করো

### ✅ Code Hint

```js
const url = "https://jsonplaceholder.typicode.com/users";

fetch(url)
  .then((response) => response.json())
  .then((data) => console.log(data));
```
