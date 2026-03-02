# 📘 Module 28 – Internet, API, Fetch Practice Guide

---

# 🔵 28-1 Internet, HTTP vs HTTPS, API

## 🧠 সহজ বোঝা

- **Internet** = অনেক কম্পিউটার একসাথে কানেক্টেড
- **HTTP** = Browser আর Server এর মধ্যে কথা বলার নিয়ম
- **HTTPS** = Secure version (S = Secure)
- **API** = Server থেকে data নেওয়ার দরজা

---

## ✅ Exercise

1. Browser এ যেকোনো website খুলে URL দেখো
2. দেখো `http` না `https`
3. Inspect → Network tab খুলে refresh দাও

👉 কতগুলো request যাচ্ছে দেখো

---

## 🎯 কেন practice?

Network না বুঝলে API বুঝবে না।

---

# 🔵 28-2 API & JSON

## 🧠 সহজ বোঝা

API data দেয় **JSON format** এ  
JSON দেখতে object বা array এর মতো

---

## ✅ Exercise

এই link ব্রাউজারে দাও:

https://jsonplaceholder.typicode.com/users

### কাজ:

- এটা array না object?
- প্রথম item এর name কী?

---

## ✅ Hint

- `[` দিয়ে শুরু → Array
- `{` দিয়ে শুরু → Object

Array হলে:

- প্রথম item = index 0
- তারপর `name` প্রপার্টি খুঁজবে

ভাবো:

```
0 নম্বর item → name
```

---

## 🎯 কেন practice?

Data structure না বুঝলে coding ভেঙে যাবে।

---

# 🔵 28-3 Fetch দিয়ে JSON Load

## 🧠 সহজ বোঝা

`fetch` = server থেকে data আনা

---

## ✅ Code Practice

```js
const url = "https://jsonplaceholder.typicode.com/users";

fetch(url)
  .then((response) => response.json())
  .then((data) => console.log(data));
```

---

## 🎯 কেন practice?

API কাজ করছে কিনা আগে Console এ দেখতে হবে।

---

# 🔵 28-4 Console Each Data

## 🎯 Goal

- সব name console এ দেখাও
- সব email console এ দেখাও
- forEach ব্যবহার করো

---

## ✅ Code

```js
const url = "https://jsonplaceholder.typicode.com/users";

fetch(url)
  .then((res) => res.json())
  .then((users) => {
    showNames(users);
    showEmails(users);
  });

function showNames(users) {
  users.forEach((user) => {
    console.log(user.name);
  });
}

function showEmails(users) {
  users.forEach((user) => {
    console.log(user.email);
  });
}
```

---

# 🔵 28-5 Post Title UI তে দেখানো

API:
https://jsonplaceholder.typicode.com/posts

---

## 🎯 Goal

- শুধু post এর title দেখাও
- প্রথম ১০টা limit করো
- Console না, UI তে দেখাও

---

## 🧩 HTML

```html
<div id="postContainer"></div>
```

---

## 🧩 JS

```js
const url = "https://jsonplaceholder.typicode.com/posts";

fetch(url)
  .then((res) => res.json())
  .then((posts) => {
    const first10 = posts.slice(0, 10);
    renderPosts(first10);
  });

function renderPosts(posts) {
  const container = document.getElementById("postContainer");

  posts.forEach((post) => {
    const p = document.createElement("p");
    p.innerText = post.title;
    container.appendChild(p);
  });
}
```

---

# 🔵 28-6 Post Card + CSS

## 🎯 Goal

প্রতিটা post এর জন্য card বানাও:

- Title
- Body

---

## 🧩 HTML

```html
<div id="postContainer"></div>
```

---

## 🧩 CSS

```css
.post-card {
  border: 1px solid #ddd;
  padding: 15px;
  margin: 10px 0;
  background: #f9f9f9;
  border-radius: 6px;
}
```

---

## 🧩 JS

```js
const url = "https://jsonplaceholder.typicode.com/posts";

fetch(url)
  .then((res) => res.json())
  .then((posts) => {
    const first10 = posts.slice(0, 10);
    renderPosts(first10);
  });

function renderPosts(posts) {
  const container = document.getElementById("postContainer");

  posts.forEach((post) => {
    const card = document.createElement("div");
    card.classList.add("post-card");

    const title = document.createElement("h3");
    title.innerText = post.title;

    const body = document.createElement("p");
    body.innerText = post.body;

    card.appendChild(title);
    card.appendChild(body);
    container.appendChild(card);
  });
}
```

---

# 🔵 28-7 Todo + Condition

API:
https://jsonplaceholder.typicode.com/todos

---

## 🎯 Goal

- প্রথম ২০টা todo
- completed true = সবুজ
- false = লাল

---

## 🧩 HTML

```html
<div id="todoList"></div>
```

---

## 🧩 JS

```js
const url = "https://jsonplaceholder.typicode.com/todos";

fetch(url)
  .then((res) => res.json())
  .then((todos) => {
    const first20 = todos.slice(0, 20);
    renderTodos(first20);
  });

function renderTodos(todos) {
  const todoList = document.getElementById("todoList");

  todos.forEach((todo) => {
    const p = document.createElement("p");
    p.innerText = todo.title;

    if (todo.completed === true) {
      p.style.color = "green";
    } else {
      p.style.color = "red";
    }

    todoList.appendChild(p);
  });
}
```

---

# 🔵 28-8 GET, POST, PUT, DELETE

## 🧠 সহজ বোঝা

- GET = data নেওয়া
- POST = data পাঠানো
- PUT = পুরো update
- PATCH = আংশিক update
- DELETE = data মুছা

---

## ✅ POST Structure Example

```js
const url = "https://jsonplaceholder.typicode.com/posts";

const newPost = {
  title: "My title",
  body: "My post body",
  userId: 1,
};

fetch(url, {
  method: "POST",
  headers: {
    "Content-Type": "application/json",
  },
  body: JSON.stringify(newPost),
});
```

---

# 🔵 28-9 Async / Await

## 🧠 সহজ বোঝা

- async দিলে await ব্যবহার করা যায়
- await = কাজ শেষ না হওয়া পর্যন্ত অপেক্ষা

---

## ✅ Code

```js
async function loadUsers() {
  const url = "https://jsonplaceholder.typicode.com/users";

  const response = await fetch(url);
  const users = await response.json();

  console.log(users);
}

loadUsers();
```

---

# 🎯 Final Goal

✔ API বুঝা  
✔ JSON structure বুঝা  
✔ Console থেকে UI তে data দেখানো  
✔ Condition ব্যবহার করা  
✔ Async/Await বোঝা

---

🔥 Practice করলে Backend বুঝতে সহজ হবে।
