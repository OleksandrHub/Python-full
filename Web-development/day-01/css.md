# Зміст:
- [CSS-ПОСІБНИК (частина 1)](#-css-посібник-частина-1)
- [РОЗДІЛ 1: ПІДКЛЮЧЕННЯ CSS](#-розділ-1-підключення-css)
- [РОЗДІЛ 2: СЕЛЕКТОРИ](#-розділ-2-селектори)
- [РОЗДІЛ 3: КОЛЬОРИ](#-розділ-3-кольори)
- [РОЗДІЛ 4: ТЕКСТ](#-розділ-4-текст)
- [РОЗДІЛ 5: ВІДСТУПИ](#-розділ-5-відступи)
- [РОЗДІЛ 6: РАМКИ (BORDER)](#-розділ-6-рамки-border)
- [РОЗДІЛ 7: BOX MODEL (модель коробки)](#-розділ-7-box-model-модель-коробки)
- [РОЗДІЛ 8: DISPLAY](#-розділ-8-display)
- [РОЗДІЛ 9: FLEXBOX](#-розділ-9-flexbox)
- [РОЗДІЛ 10: ПОЗИЦІЮВАННЯ](#-розділ-10-позиціювання)
- [РОЗДІЛ 11: MEDIA QUERIES (адаптивність)](#-розділ-11-media-queries-адаптивність)
- [РОЗДІЛ 12: ПСЕВДОКЛАСИ](#-розділ-12-псевдокласи)
- [РОЗДІЛ 13: ПСЕВДОЕЛЕМЕНТИ](#-розділ-13-псевдоелементи)
- [РОЗДІЛ 14: ПЕРЕХОДИ І АНІМАЦІЇ](#-розділ-14-переходи-і-анімації)
- [РОЗДІЛ 15: Z-INDEX (ШАРИ)](#-розділ-15-z-index-шари)
- [РОЗДІЛ 16: ПРАКТИКА — РЕЗЮМЕ ЗІ СТИЛЯМИ](#-розділ-16-практика-резюме-зі-стилями)

---


## 🎨 CSS-ПОСІБНИК (частина 1)

---

## 🧾 РОЗДІЛ 1: ПІДКЛЮЧЕННЯ CSS

### 🔹 Вбудований стиль

```html
<p style="color: red;">Червоний текст</p>
```

---

### 🔹 Всередині документа

```html
<head>
  <style>
    p {
      color: green;
    }
  </style>
</head>
```

---

### 🔹 Зовнішній файл

```html
<link rel="stylesheet" href="styles.css">
```

📁 `styles.css`:

```css
p {
  color: blue;
}
```

---

## 🎯 РОЗДІЛ 2: СЕЛЕКТОРИ

| Селектор              | Приклад   | Що вибирає              |
| --------------------- | --------- | ----------------------- |
| Універсальний         | `*`       | Всі елементи            |
| За тегом              | `p`       | Всі `<p>`               |
| За класом             | `.назва`  | `<div class="назва">`   |
| За ідентифікатором    | `#назва`  | `<div id="назва">`      |
| Комбінований          | `p.intro` | `<p class="intro">`     |
| Вкладений             | `div p`   | `<p>` всередині `<div>` |
| Безпосередній нащадок | `div > p` | `<p>` одразу в `<div>`  |

---

## 🎨 РОЗДІЛ 3: КОЛЬОРИ

```css
color: red;
color: #ff0000;
color: rgb(255, 0, 0);
color: rgba(255, 0, 0, 0.5); /* з прозорістю */
```

---

## 🖋️ РОЗДІЛ 4: ТЕКСТ

```css
color: navy;
font-size: 20px;
font-family: Arial, sans-serif;
font-weight: bold;
text-align: center;
text-transform: uppercase;
text-decoration: underline;
line-height: 1.5;
letter-spacing: 2px;
```

---

## 📏 РОЗДІЛ 5: ВІДСТУПИ

| Властивість | Опис               |
| ----------- | ------------------ |
| `margin`    | Зовнішній відступ  |
| `padding`   | Внутрішній відступ |

```css
p {
  margin: 20px;
  padding: 10px;
}

h1 {
  margin-top: 10px;
  margin-bottom: 15px;
  padding-left: 5px;
}
```

---

## 🧱 РОЗДІЛ 6: РАМКИ (BORDER)

```css
border: 2px solid black;

border-width: 3px;
border-style: dashed;
border-color: blue;

border-radius: 10px; /* скруглення кутів */
```



Чудово, продовжуємо! Це **частина 2 CSS-посібника українською мовою**, яка охоплює найважливіші концепції для верстки: **Box Model**, **Display**, **Flexbox**, **позиціювання**, а також **адаптивність**.

---

## 📦 РОЗДІЛ 7: BOX MODEL (модель коробки)

Кожен елемент у CSS — це прямокутна «коробка»:

```
+--------------------------+
|      margin              |
|  +--------------------+  |
|  |    border          |  |
|  |  +--------------+  |  |
|  |  |  padding     |  |  |
|  |  | +----------+ |  |  |
|  |  | | content  | |  |  |
|  |  | +----------+ |  |  |
|  |  +--------------+  |  |
|  +--------------------+  |
+--------------------------+
```

### 🔹 Приклад:

```css
div {
  width: 200px;
  padding: 10px;
  border: 2px solid black;
  margin: 20px;
}
```

🔸 Важливо: `width` — лише для `content`. Padding і border додаються зверху.

---

## 📐 РОЗДІЛ 8: DISPLAY

| Значення       | Опис                          |
| -------------- | ----------------------------- |
| `block`        | Блочний елемент (новий рядок) |
| `inline`       | Вбудований (усередині тексту) |
| `inline-block` | Як inline, але з розмірами    |
| `none`         | Прихований елемент            |
| `flex`         | Гнучкий контейнер             |

```css
p {
  display: inline;
}

div {
  display: none;
}
```

---

## 🧰 РОЗДІЛ 9: FLEXBOX

Використовується для **гнучкого розміщення елементів**.

### 🔹 Основний приклад:

```css
.container {
  display: flex;
  gap: 20px;
}

.item {
  flex: 1;
}
```

```html
<div class="container">
  <div class="item">1</div>
  <div class="item">2</div>
</div>
```

---

### 🔹 Напрямок (вісь)

```css
.container {
  flex-direction: row;       /* горизонтально */
  flex-direction: column;    /* вертикально */
}
```

---

### 🔹 Вирівнювання

```css
justify-content: center;     /* по головній осі */
align-items: center;         /* по перпендикулярній */
```

---

## 📍 РОЗДІЛ 10: ПОЗИЦІЮВАННЯ

| Значення   | Опис                               |
| ---------- | ---------------------------------- |
| `static`   | За замовчуванням                   |
| `relative` | Відносно нормального положення     |
| `absolute` | Відносно першого `relative` предка |
| `fixed`    | Відносно вікна браузера            |
| `sticky`   | Прилипає при скролі                |

```css
.box {
  position: absolute;
  top: 20px;
  left: 50px;
}
```

---

## 📱 РОЗДІЛ 11: MEDIA QUERIES (адаптивність)

```css
@media (max-width: 768px) {
  body {
    font-size: 14px;
  }

  .container {
    flex-direction: column;
  }
}
```

🔹 Використовується для **мобільної версії сайту**.

Супер, продовжуємо! Це **частина 3 CSS-посібника українською**, яка охоплює **псевдокласи**, **псевдоелементи**, **анімації**, **z-index** та практичні приклади.

---

## 🎯 РОЗДІЛ 12: ПСЕВДОКЛАСИ

Псевдокласи дозволяють стилізувати елементи залежно від їхнього стану.

| Селектор        | Опис                          |
| --------------- | ----------------------------- |
| `:hover`        | при наведенні миші            |
| `:active`       | при натисканні                |
| `:focus`        | при фокусі (наприклад, input) |
| `:first-child`  | перша дитина                  |
| `:last-child`   | остання дитина                |
| `:nth-child(n)` | n-та дитина                   |

### 🔹 Приклад:

```css
a:hover {
  color: red;
}

input:focus {
  border-color: green;
}

li:first-child {
  font-weight: bold;
}
```

---

## ✂️ РОЗДІЛ 13: ПСЕВДОЕЛЕМЕНТИ

Псевдоелементи — це **частини елемента**, які не існують у HTML.

| Селектор         | Опис                 |
| ---------------- | -------------------- |
| `::before`       | вставляє вміст перед |
| `::after`        | вставляє вміст після |
| `::first-line`   | перший рядок тексту  |
| `::first-letter` | перша літера         |

### 🔹 Приклад:

```css
p::first-line {
  font-weight: bold;
}

p::first-letter {
  font-size: 200%;
}

div::before {
  content: "➡ ";
  color: blue;
}
```

---

## 🎞️ РОЗДІЛ 14: ПЕРЕХОДИ І АНІМАЦІЇ

### 🔹 Переходи

```css
button {
  background-color: blue;
  transition: background-color 0.3s;
}

button:hover {
  background-color: green;
}
```

---

### 🔹 Анімації

```css
@keyframes slide {
  from {
    transform: translateX(0);
  }
  to {
    transform: translateX(100px);
  }
}

.box {
  animation: slide 2s infinite alternate;
}
```

---

## 🧱 РОЗДІЛ 15: Z-INDEX (ШАРИ)

`z-index` визначає порядок нашарування елементів.

```css
.box1 {
  position: absolute;
  z-index: 1;
}

.box2 {
  position: absolute;
  z-index: 2; /* поверх box1 */
}
```

---

## 🧪 РОЗДІЛ 16: ПРАКТИКА — РЕЗЮМЕ ЗІ СТИЛЯМИ

```css
body {
  font-family: Arial, sans-serif;
  background-color: #f0f0f0;
  margin: 40px;
}

.resume {
  max-width: 600px;
  margin: auto;
  background: white;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 0 10px gray;
}

.resume h1 {
  text-align: center;
  color: navy;
}

.resume h2 {
  color: darkgreen;
  border-bottom: 1px solid #ccc;
  padding-bottom: 5px;
}

.resume p, .resume li {
  line-height: 1.6;
}
```

---

🧩 У тебе вже повноцінний набір знань із CSS.

🔜 Хочеш продовжити до **повного HTML-посібника** (у стилі документації, як обіцяв раніше)?
