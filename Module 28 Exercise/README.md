<!-- 28-1 Internet, HTTP vs HTTPS, API

🧠 সহজ বোঝা

Internet = অনেক কম্পিউটার কানেক্টেড।
HTTP = নিয়ম যেটা দিয়ে browser server এর সাথে কথা বলে।
HTTPS = secure version (S মানে Secure)।
API = server থেকে data নেওয়ার দরজা।

✅ Exercise

১. Browser এ যেকোনো website খুলে URL দেখো।
২. দেখো http না https।
৩. Inspect → Network tab খুলে refresh দাও।

👉 কী দেখলে? কতগুলো request যাচ্ছে?

🎯 কেন practice?

Network না বুঝলে API বুঝবে না।

======================================================


🔵 28-2 API & JSON

🧠 সহজ বোঝা

API data দেয় JSON format এ।
JSON দেখতে object/array এর মতো।


✅ Exercise

এই link ব্রাউজারে দাও:
https://jsonplaceholder.typicode.com/users

কাজ:
•এটা array না object?
•প্রথম item এর name কী?

✅ Hint (খুব সহজ)

1.লিংকটা ওপেন করো

[ দিয়ে শুরু হলে → Array
{ দিয়ে শুরু হলে → Object
2.	Array হলে
প্রথম item মানে 0 নম্বর (index 0)
	3.	প্রথম item এর ভিতরে name প্রপার্টি খুঁজবে
ভাবো এমন: 0 নম্বর item → name
এভাবেই করলে নিজে নিজে উত্তর বের হয়ে যাবে।

🎯 কেন practice?

Data structure না বুঝলে coding ভেঙে যাবে।

======================================================


28-3 Fetch দিয়ে JSON Load

🧠 সহজ বোঝা

fetch = server থেকে data আনা।
✅ Exercise

Users API fetch করো।

ধাপ:
1.	fetch লিখো
2.	response.json() করো
3.	console.log(data) করো
UI না বানাও।


🎯 কেন practice?
API কাজ করছে কিনা আগে console এ দেখতে হবে

🧠 Briefly: কীভাবে করবে (একদম সহজ)
	•	fetch(url) দিয়ে সার্ভার থেকে ডাটা আনবে (এটা Promise দেয়)
	•	response.json() দিয়ে ডাটাকে JSON এ convert করবে
	•	তারপর console.log(data) দিয়ে Console এ দেখবে
	•	UI লাগবে না, শুধু Console output দেখাই লক্ষ্য

✅ Code Hint (Solve করার জন্য)

// 1) URL রাখো
const url = "https://jsonplaceholder.typicode.com/users";

// 2) fetch করো
fetch(url)
  .then((response) => response.json())   // 3) JSON বানাও
  .then((data) => console.log(data));    // 4) Console এ দেখাও

👉 চেক করার টিপস:
Console এ যদি Array(10) বা user list দেখো, তাহলে ঠিক আছে।

======================================================


🔵 28-4 Console Each Data

🧠 সহজ বোঝা

Array এ অনেক object থাকলে loop করতে হয়।

✅ Exercise

Users API থেকে:
	•	সব name console এ দেখাও
	•	সব email console এ দেখাও

forEach ব্যবহার করো।


// ✅ 1) API link: এখান থেকে users data আসবে
const url = "https://jsonplaceholder.typicode.com/users";

// ✅ 2) fetch মানে: server থেকে data আনো
fetch(url)
  // ✅ 3) res = raw response (এটা JS object না)
  // res.json() = JSON text কে JS array/object বানায়
  .then((res) => res.json())

  // ✅ 4) এখন users = আসল data (এটা একটি array)
  .then((users) => {
    console.log("✅ Full users data:", users); // পুরো array দেখার জন্য

    // ✅ 5) forEach fetch-এর ভেতরে না রেখে, আলাদা function এ পাঠালাম
    showNames(users);
    showEmails(users);
  });

/* ✅ Function 1: সব নাম console এ দেখাবে */
function showNames(users) {
  console.log("---- ✅ All Names ----"); // section header
  users.forEach((user) => {
    console.log(user.name);
  });
}

/* ✅ Function 2: সব email console এ দেখাবে */
function showEmails(users) {
  console.log("---- ✅ All Emails ----"); // section header
  users.forEach((user) => {
    console.log(user.email);
  });
}

🎯 কেন practice?

Loop না পারলে data handle করতে পারবে না

======================================================

28-5 Post Title UI তে দেখানো

API:
https://jsonplaceholder.typicode.com/posts


✅ Exercise

HTML এ একটা div বানাও।

কাজ:

•শুধু post এর title page এ দেখাও
•১০টা limit করো

🎯 কেন practice?

Console থেকে UI তে data নেওয়া শিখবে।
খুব সহজভাবে বুঝো 👇

🔵 Post Title UI তে দেখানো  মানে কী?

এতদিন তুমি কি করেছো?
👉 API থেকে data এনে console এ দেখিয়েছো।

এখন কী করতে হবে?
👉 সেই data ওয়েব পেজে (UI তে) দেখাতে হবে।

🧠 UI মানে কী?

UI = User Interface
মানে: যা user চোখে দেখে —
যেমন: div, text, button, card, ইত্যাদি।

এখন এই Exercise এ কী করতে হবে?
	1.	API থেকে posts আনবে
	2.	পুরো post না, শুধু title নেবে
	3.	সব না, শুধু প্রথম ১০টা নেবে
	4.	Console না, HTML এর div এর ভিতরে দেখাবে

🎯 “Console থেকে UI তে data নেওয়া শিখবে” — এর মানে

এতদিন:

console.log(post.title);

এখন:
div.innerText = post.title;

মানে:
•আগে শুধু ডাটা দেখছিলে
•এখন ডাটা দিয়ে page বানাতে শিখবে

সহজ ভাষায়

Console দেখা = নিজের জন্য
UI তে দেখানো = User এর জন্য

এটাই next level practice।

======================================================


🔵 28-6 Post Card + CSS

🧠 সহজ বোঝা

Data সুন্দরভাবে দেখাতে structure দরকার।

✅ Exercise

প্রতি post এর জন্য:
•Title
•Body
একটা simple card বানাও CSS দিয়ে।

নিচে 28-6 টা কি করতে হবে—একদম ডিটেইলে, কিন্তু beginner-friendly ভাবে দিলাম (কোড না গুলিয়ে, স্টেপ ধরে)।


✅ তোমার লক্ষ্য (Goal)

API থেকে posts আনবে, তারপর প্রতিটা post কে ওয়েবপেজে একটা করে card বানিয়ে দেখাবে।

একটা card এর ভিতরে থাকবে:
	•	Title (post.title)
	•	Body (post.body)

আর CSS দিয়ে card টা পরিস্কার/সুন্দর করে দেখাবে।


🧩 Step-by-step কী করবে

Step 1: HTML এ একটা container div বানাও
	•	এই div এর ভিতরে সব card বসবে
	•	উদাহরণ: id="postContainer"

Step 2: CSS এ card-এর ডিজাইন ঠিক করো

তুমি যেসব জিনিস দেবে:
	•	card এর চারপাশে border
	•	একটু padding (ভিতরের space)
	•	একটু margin/gap (card এর মধ্যে দূরত্ব)
	•	হালকা background
	•	হালকা shadow (optional)
	•	title বড় / bold

👉 লক্ষ্য: দেখলেই যেন “কার্ড” মনে হয়।

Step 3: JS দিয়ে API fetch করো
	•	fetch(url)
	•	.then(res => res.json())
	•	.then(posts => ...)

Step 4: ১০টা limit (optional কিন্তু ভাল)
	•	posts.slice(0, 10) দিয়ে প্রথম ১০টা নাও
(তোমার আগের মডিউলের মতো)

Step 5: আলাদা function বানাও (clean code)
	•	renderPosts(posts) নামে function করো
	•	fetch থেকে data পাওয়ার পর renderPosts(first10) পাঠিয়ে দাও

Step 6: renderPosts এর ভিতরে loop করে card বানাও

প্রতিটা post এর জন্য:
	1.	div বানাও (এইটাই card)
	2.	card এ একটা h3/h2 (title এর জন্য)
	3.	card এ একটা p (body এর জন্য)
	4.	card এ class দাও: class="post-card"
	5.	container এ append করো

👉 এখানে “structure দরকার” মানে:
title আলাদা element, body আলাদা element।
সব এক লাইনে লেখা না।

✅ কীভাবে বুঝবে কাজ ঠিক হয়েছে?

•পেজে অনেকগুলো card দেখাবে
•প্রতিটা card এ:
•উপরে title
•নিচে body
•card গুলো সুন্দর gap সহ থাকবে (CSS কাজ করবে)

সাধারণ ভুল (Avoid)
	•	container div না বানিয়ে body তে সব ঢুকানো
	•	innerHTML += দিয়ে সব একসাথে লিখে গুলিয়ে ফেলা
	•	CSS class না দিয়ে random style করা
	•	title/body আলাদা element না করা

যদি চাও, আমি 28-6 এর full HTML + CSS + JS template “গ্রুপে পোস্ট করার মতো” করে সাজিয়ে দিতে পারি (নাম, কমেন্ট, পরিষ্কার structure সহ)।
🎯 কেন practice?

Real project এ UI গুরুত্বপূর্ণ।

======================================================

🔵 28-7 Todo + Condition

API:
https://jsonplaceholder.typicode.com/todos


✅ Exercise
	•	প্রথম ২০টা todo দেখাও
	•	completed true হলে সবুজ লেখো
	•	false হলে লাল লেখো
🧠 কী করতে হবে (একদম সহজভাবে)

এই API থেকে todos আনবে:
https://jsonplaceholder.typicode.com/todos

তারপর—
	1.	প্রথম ২০টা todo নেবে (slice(0, 20))
	2.	UI তে প্রতিটা todo এর title দেখাবে
	3.	completed === true হলে লেখার রঙ সবুজ
	4.	completed === false হলে লেখার রঙ লাল

✅ HTML (একটা container)

<div id="todoList"></div>



✅ JS (fetch + ২০টা + condition)

const url = "https://jsonplaceholder.typicode.com/todos";

fetch(url)
  .then((res) => res.json())
  .then((todos) => {
    const first20 = todos.slice(0, 20);
    renderTodos(first20);
  });

// ✅ UI function (fetch থেকে আলাদা)
function renderTodos(todos) {
  const todoList = document.getElementById("todoList");
  todoList.innerHTML = "";

  todos.forEach((todo) => {
    const p = document.createElement("p");
    p.innerText = todo.title;

    // ✅ condition: completed true/false অনুযায়ী রঙ
    if (todo.completed === true) {
      p.style.color = "green";
    } else {
      p.style.color = "red";
    }

    todoList.appendChild(p);
  });
}


🔎 Hint মনে রাখো
	•	todo.completed শুধু true/false
	•	if/else = condition logic
	•	slice(0, 20) = প্রথম ২০টা item

🎯 কেন practice?

Condition না জানলে logic কাজ করবে না।

======================================================

🔵 28-8 GET, POST, PUT, DELETE

🧠 সহজ বোঝা

GET = data নেওয়া
POST = data পাঠানো
PUT = পুরো update
PATCH = আংশিক update
DELETE = data মুছা

✅ Exercise

POST এর একটা fetch structure লিখো যেখানে থাকবে:
	•	method
	•	headers
	•	body

কাজ করাতে হবে না।

চিন্তা করো না, একদম সহজভাবে বুঝাই 👇

🧠 POST মানে কী?

POST মানে:
👉 আমরা server কে নতুন data পাঠাচ্ছি

GET এ আমরা data নেই
POST এ আমরা data পাঠাই

সহজ উদাহরণ

ধরো তুমি একটা form পূরণ করলে:
	•	title লিখলে
	•	body লিখলে
	•	submit করলে

এই submit করার কাজটাই হলো POST


এবার কোডটা খুব সহজভাবে দেখি

const url = "https://jsonplaceholder.typicode.com/posts";

➡️ এখানে আমরা বলছি data কোথায় পাঠাবো।



const newPost = {
  title: "My title",
  body: "My post body",
  userId: 1,
};

➡️ এটা সেই data যেটা আমরা পাঠাতে চাই।
➡️ এটা এখন JavaScript object।


fetch(url, {

➡️ এবার fetch দিয়ে data পাঠানো শুরু করছি।

  method: "POST",

➡️ এখানে বলছি: এটা POST request।

  headers: {
    "Content-Type": "application/json",
  },

➡️ server কে বলছি:
“আমি JSON format এ data পাঠাচ্ছি”


  body: JSON.stringify(newPost),

➡️ খুব গুরুত্বপূর্ণ 👇
Server JavaScript object বোঝে না।
তাই JSON.stringify() দিয়ে object কে JSON string বানিয়ে পাঠাতে হয়।


এক লাইনে মনে রাখো
	•	method = কী কাজ (POST)
	•	headers = কেমন data পাঠাচ্ছি
	•	body = আসল data


সহজ analogy

GET = দোকান থেকে কিছু নেওয়া
POST = দোকানে কিছু দেওয়া


তুমি চাইলে আমি GET vs POST একদম table দিয়ে clear করে দিতে পারি।

🎯 কেন practice?

Backend এ গেলে লাগবে।

======================================================

🔵 28-9 Async Await + Debugger

🧠 সহজ বোঝা

Async/Await = cleaner way to fetch
Debugger = code থামিয়ে দেখা

✅ Exercise

১. fetch async/await দিয়ে লেখো
২. debugger ব্যবহার করো
৩. step by step দেখো
নিশ্চয়—এই কোডটা একদম সহজ বাংলায় বুঝিয়ে দিচ্ছি, লাইন বাই লাইন।

async function loadUsers() {
  const url = "https://jsonplaceholder.typicode.com/users";

  const res = await fetch(url);
  const data = await res.json();

  console.log(data);
}

loadUsers();

1) async function loadUsers() { ... }
	•	loadUsers নামে একটা function বানালাম।
	•	async মানে: এই function এর ভিতরে আমরা await ব্যবহার করতে পারবো।
	•	await ব্যবহার করলে কোডটা “লাইন ধরে” পড়া সহজ হয়।

2) const url = ".../users";
	•	API link টা url ভ্যারিয়েবলে রাখলাম।
	•	যাতে বারবার লিংক লিখতে না হয়।

3) const res = await fetch(url);
	•	fetch(url) মানে: এই URL থেকে data আনতে বললাম।
	•	await মানে: fetch শেষ না হওয়া পর্যন্ত অপেক্ষা করো।
	•	fetch শেষে যা আসে সেটা res (response) এ থাকে।
	•	res এর ভিতরে data “ready” আছে, কিন্তু এখনো JS array/object হয়নি।

4) const data = await res.json();
	•	res.json() মানে: response এর JSON ডাটাকে JavaScript এ ব্যবহারযোগ্য বানানো (array/object)।
	•	await মানে: JSON বানানো শেষ না হওয়া পর্যন্ত অপেক্ষা করো।
	•	শেষ হলে আসল data data ভ্যারিয়েবলে চলে আসে।

5) console.log(data);
	•	এখন data তে পুরো users list আছে।
	•	তাই console এ দেখালাম।

6) loadUsers();
	•	function টাকে কল না করলে কিছুই চলবে না।
	•	তাই শেষে কল করা হয়েছে।

মনে রাখার মতো (One line)

fetch ডাটা আনে → res.json() ডাটা JS এ usable করে → console.log দেখায়।
// ✅ Users data আনার function (async/await ব্যবহার করে)
async function loadUsers() {
  // 1) API link (কোথা থেকে data আনবো)
  const url = "https://jsonplaceholder.typicode.com/users";

  // 2) fetch = server থেকে data আনা
  // await = fetch শেষ না হওয়া পর্যন্ত অপেক্ষা করো
  const response = await fetch(url);

  // 3) response.json() = JSON text কে JavaScript array/object বানায়
  // await = convert শেষ না হওয়া পর্যন্ত অপেক্ষা করো
  const users = await response.json();

  // 4) এখন users হলো আসল data (array)
  console.log(users);

  // 5) চাইলে প্রথম user এর নামও দেখতে পারো (optional)
  // console.log(users[0].name);
}

// ✅ function চালু করা (call না করলে কিছু হবে না)
loadUsers();

একদম সহজ ব্যাখ্যা (Bangla)
	•	async দিলে await ব্যবহার করা যায়
	•	await fetch(url) = data আসা পর্যন্ত অপেক্ষা
	•	await response.json() = data কে JS array/object বানানো
	•	শেষে console.log(users) = data দেখানো
 -->
