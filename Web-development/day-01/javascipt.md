# JS-ПОСІБНИК (частина 1)
# Зміст:
# - [Розділ 1: Вступ до JavaScript](#-розділ-1-вступ-до-javascript)
# - [Розділ 2: Змінні та типи даних](#-розділ-2-змінні-та-типи-даних)
# - [Розділ 3: Операції](#-розділ-3-операції)
# - [Розділ 4: Умови](#-розділ-4-умови)
# - [Розділ 5: Функції](#-розділ-5-функції)
# - [Розділ 6: Цикли](#-розділ-6-цикли)
# - [Розділ 7: Масиви](#-розділ-7-масиви)
# - [Розділ 8: Об’єкти](#-розділ-8-об’єкти)
# - [Розділ 9: Що таке DOM?](#-розділ-9-що-таке-dom)
# - [Розділ 10: Вибір елементів](#-розділ-10-вибір-елементів)
# - [Розділ 11: Зміна вмісту](#-розділ-11-зміна-вмісту)
# - [Розділ 12: Робота з атрибутами](#-розділ-12-робота-з-атрибутами)
# - [Розділ 13: Стилі та класи](#-розділ-13-стилі-та-класи)
# - [Розділ 14: Події](#-розділ-14-події)
# - [Розділ 15: Асинхронність у JavaScript](#-розділ-15-асинхронність-у-javascript)
# - [Розділ 16: Callback-функції](#-розділ-16-callback-функції)
# - [Розділ 17: Проміси (Promises)](#-розділ-17-проміси-promises)
# - [Розділ 18: Async/Await](#-розділ-18-async-await)
# - [Розділ 19: Fetch API — робота з HTTP-запитами](#-розділ-19-fetch-api-робота-з-http-запитами)  
# - [Розділ 20: Приклад — кнопка завантаження даних](#-розділ-20-приклад-кнопка-завантаження-даних)
# - [Розділ 21: Класи (Classes)](#-розділ-21-класи-classes) 
# - [Розділ 22: Модулі (Modules)](#-розділ-22-модулі-modules)
# - [Розділ 23: Регулярні вирази (RegExp)](#-розділ-23-регулярні-вимови-regexp)
# - [Розділ 24: LocalStorage](#-розділ-24-localstorage)
# - [Розділ 25: проглиблені проміси](#-розділ-25-проглиблені-проміси)
# - [Розділ 26: Генератори (Generators)](#-розділ-26-генератори-generators)
# - [Розділ 27: робота з формами](#-розділ-27-робота-з-формами)
# - [Розділ 28: події (Events)](#-розділ-28-події-events)


---

## 📌 РОЗДІЛ 1: ВСТУП ДО JAVASCRIPT

JavaScript (JS) — це мова програмування, що дозволяє робити веб-сторінки інтерактивними.

---

## 🔹 Як підключити JS

### Вбудований скрипт у HTML

```html
<script>
  alert('Привіт, світ!');
</script>
```

### Зовнішній файл

```html
<script src="script.js"></script>
```

---

## 📌 РОЗДІЛ 2: ЗМІННІ ТА ТИПИ ДАНИХ

### Оголошення змінних

```js
let ім’я_змінної = значення;  // змінна, можна змінювати
const ім’я_константи = значення;  // константа, не змінюється
var стара_змінна = значення;  // стара форма, уникай
```

---

### Типи даних

| Тип       | Приклад            |
| --------- | ------------------ |
| Number    | `42`, `3.14`       |
| String    | `'Привіт'`, `"JS"` |
| Boolean   | `true`, `false`    |
| Null      | `null`             |
| Undefined | `undefined`        |
| Object    | `{ name: 'Іван' }` |
| Array     | `[1, 2, 3]`        |

---

### Приклади

```js
let age = 25;              // число
let name = "Олексій";      // рядок
let isStudent = true;      // булевий
let job = null;            // нічого
let address;               // undefined
```

---

## 📌 РОЗДІЛ 3: ОПЕРАЦІЇ

### Арифметичні

```js
let sum = 5 + 3;       // 8
let diff = 10 - 7;     // 3
let mul = 4 * 2;       // 8
let div = 12 / 3;      // 4
let mod = 10 % 3;      // 1 (залишок)
```

---

### Строкові

```js
let str = "Привіт, " + "світ!"; // "Привіт, світ!"
```

---

### Логічні

```js
let a = true && false;   // false
let b = true || false;   // true
let c = !true;           // false
```

---

## 📌 РОЗДІЛ 4: УМОВИ

```js
let age = 18;

if (age >= 18) {
  console.log("Доступ дозволено");
} else {
  console.log("Доступ заборонено");
}
```

---

## 📌 РОЗДІЛ 5: ФУНКЦІЇ

### Оголошення

```js
function greet(name) {
  return "Привіт, " + name + "!";
}

console.log(greet("Олексій")); // Привіт, Олексій!
```

---

### Функції-стрілки (ES6)

```js
const greet = (name) => "Привіт, " + name + "!";

console.log(greet("Оля")); // Привіт, Оля!
```

---

Отже, продовжуємо з JavaScript — **частина 2**: цикли, масиви та об’єкти.

---

## 📌 РОЗДІЛ 6: ЦИКЛИ

Цикли дозволяють повторювати код багато разів.

### 🔹 Цикл `for`

```js
for (let i = 0; i < 5; i++) {
  console.log(i);
}
// Виведе числа 0, 1, 2, 3, 4
```

---

### 🔹 Цикл `while`

```js
let i = 0;
while (i < 5) {
  console.log(i);
  i++;
}
```

---

### 🔹 Цикл `do...while`

```js
let i = 0;
do {
  console.log(i);
  i++;
} while (i < 5);
```

---

## 📌 РОЗДІЛ 7: МАСИВИ

Масив — це список елементів.

```js
let fruits = ["яблуко", "банан", "вишня"];
console.log(fruits[0]); // "яблуко"
```

---

### Основні методи масивів

| Метод       | Опис                     |
| ----------- | ------------------------ |
| `push()`    | Додає елемент у кінець   |
| `pop()`     | Видаляє останній елемент |
| `shift()`   | Видаляє перший елемент   |
| `unshift()` | Додає елемент на початок |
| `length`    | Кількість елементів      |

```js
fruits.push("апельсин");   // ["яблуко", "банан", "вишня", "апельсин"]
fruits.pop();              // ["яблуко", "банан", "вишня"]
```

---

## 📌 РОЗДІЛ 8: ОБ’ЄКТИ

Об’єкти — це колекції пар «ключ-значення».

```js
let person = {
  name: "Олексій",
  age: 25,
  isStudent: true
};

console.log(person.name); // "Олексій"
```

---

### Додавання і зміна властивостей

```js
person.job = "програміст";
person.age = 26;
```

---

### Вкладені об’єкти і масиви

```js
let student = {
  name: "Ірина",
  grades: [90, 85, 92],
  address: {
    city: "Київ",
    street: "Хрещатик"
  }
};

console.log(student.grades[1]);        // 85
console.log(student.address.city);     // "Київ"
```

---

Чудово! Переходимо до наступної важливої теми — **DOM (Document Object Model) та події в JavaScript**.

---


## 📌 РОЗДІЛ 9: ЩО ТАКЕ DOM?

DOM — це об’єктна модель веб-сторінки, що дозволяє JavaScript керувати HTML-елементами.

* Кожен тег HTML — це **елемент** DOM.
* JS може змінювати текст, атрибути, стилі, додавати або видаляти елементи.

---

## 📌 РОЗДІЛ 10: ВИБІР ЕЛЕМЕНТІВ

### 🔹 `document.getElementById`

```js
let header = document.getElementById("myHeader");
header.style.color = "red";
```

---

### 🔹 `document.getElementsByClassName`

```js
let items = document.getElementsByClassName("item");
items[0].textContent = "Новий текст";
```

---

### 🔹 `document.querySelector`

Повертає перший елемент, що відповідає CSS-селектору:

```js
let firstItem = document.querySelector(".item");
firstItem.style.fontWeight = "bold";
```

---

### 🔹 `document.querySelectorAll`

Повертає всі елементи, що відповідають селектору:

```js
let allItems = document.querySelectorAll(".item");
allItems.forEach(el => el.style.color = "blue");
```

---

## 📌 РОЗДІЛ 11: ЗМІНА ВМІСТУ

### 🔹 Зміна тексту

```js
let p = document.querySelector("p");
p.textContent = "Новий текст у параграфі";
```

---

### 🔹 Зміна HTML

```js
let div = document.querySelector("#container");
div.innerHTML = "<strong>Жирний текст</strong>";
```

---

## 📌 РОЗДІЛ 12: РОБОТА З АТРИБУТАМИ

### 🔹 Отримання атрибуту

```js
let link = document.querySelector("a");
console.log(link.getAttribute("href"));
```

---

### 🔹 Встановлення атрибуту

```js
link.setAttribute("href", "https://example.com");
```

---

## 📌 РОЗДІЛ 13: СТИЛІ ТА КЛАСИ

### 🔹 Зміна стилів через JS

```js
let box = document.querySelector(".box");
box.style.backgroundColor = "yellow";
```

---

### 🔹 Робота з класами

```js
box.classList.add("active");
box.classList.remove("hidden");
box.classList.toggle("highlight");
```

---

## 📌 РОЗДІЛ 14: ПОДІЇ

Події — це дії користувача або браузера (натискання, наведення, завантаження сторінки).

### 🔹 Додавання обробника події

```js
let btn = document.querySelector("button");

btn.addEventListener("click", () => {
  alert("Кнопку натиснуто!");
});
```

---

### 🔹 Приклад: показати/сховати секцію

```html
<button id="toggleBtn">Показати/сховати досвід</button>
<div id="experience">
  <p>Мій досвід роботи...</p>
</div>
```

```js
let btn = document.getElementById("toggleBtn");
let exp = document.getElementById("experience");

btn.addEventListener("click", () => {
  if (exp.style.display === "none") {
    exp.style.display = "block";
  } else {
    exp.style.display = "none";
  }
});
```

---

Добре, йдемо далі! Продовжуємо з однією з найважливіших тем у JavaScript — **Асинхронність, проміси, async/await і робота з мережевими запитами (fetch)**.

---



## 📌 РОЗДІЛ 15: АСИНХРОННІСТЬ У JAVASCRIPT

JavaScript — однопотокова мова, але вона підтримує асинхронні операції, щоб не блокувати роботу програми.

Асинхронність — це коли код виконується не послідовно, а з очікуванням результату, наприклад, мережеві запити, таймери.

---

## 📌 РОЗДІЛ 16: CALLBACK-ФУНКЦІЇ

Функції, які передаються в інші функції для виконання пізніше.

```js
function greet(name, callback) {
  console.log("Привіт, " + name);
  callback();
}

greet("Олексій", () => {
  console.log("Це callback-функція!");
});
```

---

## 📌 РОЗДІЛ 17: ПРОМІСИ (Promises)

Проміс — це об’єкт, який представляє майбутній результат асинхронної операції.

---

### Створення промісу

```js
let promise = new Promise((resolve, reject) => {
  let success = true; // умова для прикладу

  if (success) {
    resolve("Все добре!");
  } else {
    reject("Сталася помилка!");
  }
});
```

---

### Використання `.then()` і `.catch()`

```js
promise
  .then(result => {
    console.log("Результат:", result);
  })
  .catch(error => {
    console.error("Помилка:", error);
  });
```

---

## 📌 РОЗДІЛ 18: ASYNC / AWAIT

Сучасний синтаксис для роботи з промісами.

```js
function wait(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}

async function run() {
  console.log("Чекаємо 2 секунди...");
  await wait(2000);
  console.log("2 секунди минуло");
}

run();
```

---

## 📌 РОЗДІЛ 19: FETCH API — робота з HTTP-запитами

`fetch()` використовується для отримання даних з мережі.

---

### Простий GET-запит

```js
fetch("https://jsonplaceholder.typicode.com/posts/1")
  .then(response => response.json())
  .then(data => console.log(data))
  .catch(error => console.error("Помилка:", error));
```

---

### Запит з async/await

```js
async function getPost() {
  try {
    let response = await fetch("https://jsonplaceholder.typicode.com/posts/1");
    let data = await response.json();
    console.log(data);
  } catch (error) {
    console.error("Помилка:", error);
  }
}

getPost();
```

---

## 📌 РОЗДІЛ 20: Приклад — кнопка завантаження даних

```html
<button id="loadBtn">Завантажити пост</button>
<div id="post"></div>
```

```js
let btn = document.getElementById("loadBtn");
let postDiv = document.getElementById("post");

btn.addEventListener("click", async () => {
  postDiv.textContent = "Завантаження...";
  try {
    let response = await fetch("https://jsonplaceholder.typicode.com/posts/1");
    let data = await response.json();
    postDiv.innerHTML = `<h3>${data.title}</h3><p>${data.body}</p>`;
  } catch (error) {
    postDiv.textContent = "Сталася помилка при завантаженні.";
  }
});
```

---

Добре, продовжуємо! Наступний великий блок — **класи, модулі, регулярні вирази та LocalStorage**.

---



## 📌 РОЗДІЛ 21: КЛАСИ (Classes)

Класи — це шаблони для створення об’єктів з певною структурою і поведінкою.

---

### Створення класу

```js
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  greet() {
    console.log(`Привіт, мене звати ${this.name} і мені ${this.age} років.`);
  }
}

let olx = new Person("Олексій", 25);
olx.greet();
// Виведе: Привіт, мене звати Олексій і мені 25 років.
```

---

### Наслідування класів

```js
class Student extends Person {
  constructor(name, age, university) {
    super(name, age);
    this.university = university;
  }

  study() {
    console.log(`${this.name} навчається в університеті ${this.university}.`);
  }
}

let iryna = new Student("Ірина", 21, "КНУ");
iryna.greet();
iryna.study();
```

---

## 📌 РОЗДІЛ 22: МОДУЛІ (Modules)

Модулі дозволяють розбивати код на файли та імпортувати їх.

---

### Експорт (export)

```js
// math.js
export function add(a, b) {
  return a + b;
}
export const PI = 3.14;
```

---

### Імпорт (import)

```js
// main.js
import { add, PI } from './math.js';

console.log(add(2, 3)); // 5
console.log(PI);        // 3.14
```

---

> **Важливо:** Для роботи з модулями в браузері `<script>` має атрибут `type="module"`:
>
> ```html
> <script type="module" src="main.js"></script>
> ```

---

## 📌 РОЗДІЛ 23: РЕГУЛЯРНІ ВИРАЗИ (RegExp)

Регулярні вирази — це потужний інструмент для пошуку і заміни тексту.

---

### Приклад: перевірка email

```js
const email = "test@example.com";
const regex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;

console.log(regex.test(email)); // true або false
```

---

### Основні символи

| Символ  | Опис                      |
| ------- | ------------------------- |
| `.`     | Будь-який символ          |
| `\d`    | Цифра (0-9)               |
| `\w`    | Літера або цифра або \_   |
| `+`     | Один або більше           |
| `*`     | Нуль або більше           |
| `?`     | Нуль або один             |
| `^`     | Початок рядка             |
| `$`     | Кінець рядка              |
| `[abc]` | Будь-який символ з набору |

---

## 📌 РОЗДІЛ 24: LOCALSTORAGE

`localStorage` — зберігає дані в браузері довго (поки користувач не очистить кеш).

---

### Запис у localStorage

```js
localStorage.setItem("name", "Олексій");
```

---

### Читання з localStorage

```js
let name = localStorage.getItem("name");
console.log(name); // "Олексій"
```

---

### Видалення з localStorage

```js
localStorage.removeItem("name");
```

---

### Приклад: збереження темної теми

```js
const btn = document.getElementById("themeBtn");

btn.addEventListener("click", () => {
  document.body.classList.toggle("dark");
  if(document.body.classList.contains("dark")) {
    localStorage.setItem("theme", "dark");
  } else {
    localStorage.setItem("theme", "light");
  }
});

// При завантаженні сторінки:
if(localStorage.getItem("theme") === "dark") {
  document.body.classList.add("dark");
}
```

---

Йдемо далі! Продовжуємо з кількома важливими темами — **проміси (поглиблено), генератори, робота з формами та подіями**.

---


## 📌 РОЗДІЛ 25: ПРОГЛИБЛЕНІ ПРОМІСИ

---

### Ланцюжки промісів

Проміси можна "ланцюжити", щоб виконувати послідовні асинхронні операції.

```js
new Promise((resolve, reject) => {
  setTimeout(() => resolve(1), 1000);
})
  .then(result => {
    console.log(result); // 1
    return result * 2;
  })
  .then(result => {
    console.log(result); // 2
    return result * 3;
  })
  .then(result => {
    console.log(result); // 6
  });
```

---

### Обробка кількох промісів

* `Promise.all()` — чекає на всі проміси і повертає масив результатів.

```js
Promise.all([
  fetch('/api/data1').then(res => res.json()),
  fetch('/api/data2').then(res => res.json())
]).then(results => {
  console.log(results[0]);
  console.log(results[1]);
});
```

* `Promise.race()` — повертає результат першого виконаного промісу.

---

## 📌 РОЗДІЛ 26: ГЕНЕРАТОРИ (Generators)

Генератори — функції, які можна призупиняти і відновлювати.

---

### Синтаксис

```js
function* gen() {
  yield 1;
  yield 2;
  yield 3;
}

const g = gen();

console.log(g.next()); // {value:1, done:false}
console.log(g.next()); // {value:2, done:false}
console.log(g.next()); // {value:3, done:false}
console.log(g.next()); // {value:undefined, done:true}
```

---

### Використання генераторів для ітерації

```js
function* idGenerator() {
  let id = 0;
  while(true) {
    yield ++id;
  }
}

const genId = idGenerator();
console.log(genId.next().value); // 1
console.log(genId.next().value); // 2
console.log(genId.next().value); // 3
```

---

## 📌 РОЗДІЛ 27: РОБОТА З ФОРМАМИ

---

### Отримання даних з форми

```html
<form id="myForm">
  <input type="text" name="username" />
  <input type="password" name="password" />
  <button type="submit">Відправити</button>
</form>
```

```js
const form = document.getElementById("myForm");

form.addEventListener("submit", (event) => {
  event.preventDefault(); // щоб не перезавантажувалась сторінка

  const formData = new FormData(form);
  const username = formData.get("username");
  const password = formData.get("password");

  console.log("Логін:", username);
  console.log("Пароль:", password);
});
```

---

### Валідація форми

```js
form.addEventListener("submit", (event) => {
  event.preventDefault();

  const formData = new FormData(form);
  const username = formData.get("username");

  if(username.length < 3) {
    alert("Ім'я має бути не менше 3 символів");
    return;
  }

  // Далі обробка
});
```

---

## 📌 РОЗДІЛ 28: ПОДІЇ (Events)

---

### Основні типи подій

* `click` — клік миші
* `input` — зміна в полі вводу
* `submit` — відправка форми
* `keydown`, `keyup` — натискання клавіш

---

### Делегування подій

```js
document.getElementById("list").addEventListener("click", (event) => {
  if(event.target && event.target.matches("li.item")) {
    console.log("Натиснуто на елемент:", event.target.textContent);
  }
});
```

---

---

Я
