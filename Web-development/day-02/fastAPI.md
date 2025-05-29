# 📘 FastAPI: Від нуля до професіонала

## Зміст

1. [Глава 1: Вступ у FastAPI](#-глава-1-вступ-у-fastapi)
2. [Глава 2: Встановлення та перший проєкт FastAPI](#-глава-2-встановлення-та-перший-проєкт-fastapi)
3. [Глава 3: Основи FastAPI — маршрути, параметри, відповіді](#-глава-3-основи-fastapi--маршрути-параметри-відповіді)
4. [Глава 4: Типізація, Pydantic і перевірка даних](#-глава-4-типізація-pydantic-і-перевірка-даних)
5. [Глава 5: Шаблони (Jinja2) та HTML-інтерфейс у FastAPI](#-глава-5-шаблони-jinja2-та-html-інтерфейс-у-fastapi)
6. [Глава 6: Робота з формами та обробка POST-запитів](#-глава-6-робота-з-формами-та-обробка-post-запитів)
7. [Глава 7: Робота з базою даних (SQLite + SQLModel)](#-глава-7-робота-з-базою-даних-sqlite--sqlmodel)
8. [Глава 8: Асинхронність, Background Tasks та WebSocket у FastAPI](#-глава-8-асинхронність-background-tasks-та-websocket-у-fastapi)
9. [Глава 9: Аутентифікація і безпека (OAuth2 + JWT)](#-глава-9-аутентифікація-і-безпека-oauth2--jwt)
10. [Глава 10: Тестування FastAPI додатків](#-глава-10-тестування-fastapi-додатків)
11. [Глава 11: Розгортання FastAPI додатків (Docker, Heroku, AWS)](#-глава-11-розгортання-fastapi-додатків-docker-heroku-aws)
12. [Глава 12: Поради та ресурси для вивчення FastAPI](#-глава-12-поради-та-ресурси-для-вивчення-fastapi)

---

## 🔹 Глава 1: Вступ у FastAPI

### Що таке FastAPI?

**FastAPI** — це сучасний, швидкий (високопродуктивний) веб-фреймворк для створення API з Python 3.7+ на основі **стандарту OpenAPI** та **типізації**.

* Побудований на **Starlette** (асинхронний фреймворк) і **Pydantic** (перевірка та серіалізація даних).
* Основна перевага — підтримка **async/await**, **автоматична документація**, **перевірка типів**, та **висока швидкість**.

### Переваги FastAPI:

* 🚀 Швидкий, як Node.js або Go.
* 🧠 Автоматичні підказки у редакторі (завдяки типізації).
* 📄 Генерує Swagger і ReDoc автоматично.
* ⚙️ Простий у використанні, але потужний.

### Де застосовується FastAPI?

* API для мобільних додатків та фронтенду
* Сервіси з машинним навчанням
* Telegram-боти
* Backend для SPA (Vue, React)
* Мікросервіси

---

## 🔧 Що треба знати перед початком

FastAPI — це про Python + веб. Тож для зручного старту бажано мати знання:

* Python: змінні, функції, словники, списки
* Основи HTTP (GET, POST, статуси)
* Розуміння JSON-структури

## 🔹 Глава 2: Встановлення та перший проєкт FastAPI

### 🛠️ Встановлення

Для початку потрібно встановити FastAPI та сервер запуску **Uvicorn**.

> 🔔 Рекомендовано працювати у віртуальному середовищі (virtualenv або venv)

#### 1. Створи новий проєкт:

```bash
mkdir fastapi_project
cd fastapi_project
python -m venv venv
source venv/bin/activate  # або venv\Scripts\activate на Windows
```

#### 2. Встанови FastAPI та Uvicorn:

```bash
pip install fastapi uvicorn
```

> FastAPI — це фреймворк
> Uvicorn — ASGI-сервер, який запускає додаток

---

### 📝 Створи перший файл `main.py`

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"message": "Привіт, FastAPI!"}
```

* `@app.get("/")` — означає: відповідай на GET-запити до кореневого шляху `/`.
* `read_root()` — функція-обробник.
* `return` — відповідає JSON-словником.

---

### 🚀 Запуск застосунку

```bash
uvicorn main:app --reload
```

* `main` — назва Python-файлу (`main.py`)
* `app` — ім’я об’єкта FastAPI
* `--reload` — автоматичне перезавантаження при зміні коду

---

### 🔍 Перевірка в браузері

* Відкрий: [http://127.0.0.1:8000](http://127.0.0.1:8000) → побачиш: `{"message": "Привіт, FastAPI!"}`
* Документація:

  * Swagger UI: [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)
  * ReDoc: [http://127.0.0.1:8000/redoc](http://127.0.0.1:8000/redoc)

---

### ✅ Підсумок

* FastAPI дуже легко запускається.
* Документація генерується автоматично.
* Все працює асинхронно та швидко.

Окей, рушаємо далі!

---

## 🔹 Глава 3: Основи FastAPI — маршрути, параметри, відповіді

FastAPI дозволяє дуже гнучко працювати з маршрутами (routes), параметрами, запитами й відповідями.

---

### 📍 1. Маршрути (Routes)

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def home():
    return {"msg": "Головна сторінка"}

@app.get("/about")
def about():
    return {"msg": "Про сайт"}
```
### Маршрути визначають, як обробляти запити до різних URL.

* `@app.get(...)` — **GET-запит**  
  Використовується для отримання даних (читання). Не змінює стан сервера.  
  _Наприклад: отримати список користувачів._

* `@app.post(...)` — **POST-запит**  
  Використовується для створення нових даних.  
  _Наприклад: додати нового користувача._

* `@app.put(...)` — **PUT-запит**  
  Використовується для повного оновлення існуючих даних.  
  _Наприклад: повністю оновити профіль користувача._

* `@app.delete(...)` — **DELETE-запит**  
  Використовується для видалення даних.  
  _Наприклад: видалити користувача._

* `@app.patch(...)` — **PATCH-запит**  
  Використовується для часткового оновлення даних.  
  _Наприклад: змінити лише email користувача._

* `@app.options(...)` — **OPTIONS-запит**  
  Повертає інформацію про підтримувані сервером методи для певного ресурсу.

* `@app.head(...)` — **HEAD-запит**  
  Як GET, але повертає лише заголовки відповіді без тіла.

> Найчастіше використовуються: **GET**, **POST**, **PUT**, **DELETE**, **PATCH**.

---

### 🔢 2. Параметри в URL (Path Parameters)
**Для чого:**  
Параметри в URL (path parameters) використовуються, коли потрібно звернутися до конкретного ресурсу за його ідентифікатором або унікальним значенням.  
_Наприклад: отримати користувача з певним user_id._

```python
@app.get("/user/{user_id}")
def get_user(user_id: int):
    return {"user_id": user_id}
```

* `{user_id}` — змінна в URL
* `user_id: int` — автоматична перевірка типу

> Якщо передати `/user/abc`, буде 422 Unprocessable Entity.

---

### ❓ 3. Параметри запиту (Query Parameters)
**Для чого:**  
Параметри запиту (query parameters) використовуються для фільтрації, пошуку, пагінації або передачі додаткових опцій у запиті. Вони не є частиною шляху, а передаються після знаку `?` у URL.

```python
@app.get("/search")
def search(q: str = ""):
    return {"query": q}
```

* `/search?q=hello` → `{"query": "hello"}`

Можна додати кілька:

```python
@app.get("/filter")
def filter_items(skip: int = 0, limit: int = 10):
    return {"skip": skip, "limit": limit}
```

→ `/filter?skip=5&limit=20`

---

### ✅ 4. Коди відповіді та Response

**Для чого:**  
Код відповіді HTTP (наприклад, 200, 201, 404) показує клієнту, як завершився запит: успішно, з помилкою чи з іншим результатом.  
FastAPI дозволяє явно вказати код відповіді для кожного маршруту, щоб зробити API зрозумілішим і коректно обробляти різні ситуації.

**Як використати:**  
У декораторі маршруту можна додати параметр `status_code`. Наприклад, для створення нового ресурсу зазвичай повертають код 201 (Created):

```python
from fastapi import status

@app.post("/create", status_code=status.HTTP_201_CREATED)
def create_item():
    return {"message": "Створено!"}
```
* `status_code=status.HTTP_201_CREATED` — явно вказує, що при успішному створенні повертається код 201.
* Можна використовувати й інші коди: 200 (OK), 204 (No Content), 400 (Bad Request), 404 (Not Found) тощо.

**Переваги:**
- Клієнт (наприклад, фронтенд) може легко зрозуміти результат запиту по коду відповіді.
- Це підвищує стандартизацію та передбачуваність API.
- Всі коди можна знайти у модулі `fastapi.status`.

---

### 💡 5. Документація автоматично генерується

FastAPI сам читає сигнатури функцій, типи параметрів і генерує документацію.

**Що це означає:**  
- Всі ваші маршрути, параметри, типи та коди відповідей автоматично відображаються у Swagger UI (`/docs`) та ReDoc (`/redoc`).
- Це дуже зручно для тестування та інтеграції — не потрібно писати документацію вручну.
- Документація оновлюється автоматично при зміні коду.

> **Порада:** Завжди вказуйте коди відповідей для важливих маршрутів — це допоможе і вам, і користувачам API!

### 🧪 6. практика

1. Додай маршрут `/hello/{name}`, який повертатиме `Привіт, {name}`.
2. Створи маршрут `/calc?a=1&b=2`, який повертатиме суму `a + b`.
3. Зроби POST-запит `/submit` з кодом 201.

Чудово! Переходимо до найпотужнішої фішки FastAPI — **Pydantic**.

---

## 🔹 Глава 4: Типізація, Pydantic і перевірка даних

### 📦 Що таке Pydantic?

**Pydantic** — це бібліотека для перевірки даних та серіалізації, яку використовує FastAPI. Вона дозволяє:

* автоматично перевіряти типи;
* працювати зі складними структурами (вкладеними словниками, списками);
* створювати документацію на льоту.

---

### 🧱 1. Створення Pydantic-моделі

```python
from pydantic import BaseModel

class Item(BaseModel):
    name: str
    price: float
    in_stock: bool = True
```

> Кожне поле: `назва: тип = [за замовчуванням]`

---

### 📬 2. Використання моделі в POST-запитах

```python
from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI()

class Item(BaseModel):
    name: str
    price: float
    in_stock: bool = True

@app.post("/items/")
def create_item(item: Item):
    return {"item": item}
```

Запит:

```json
POST /items/
{
  "name": "Ноутбук",
  "price": 19999.99,
  "in_stock": false
}
```

Відповідь:

```json
{
  "item": {
    "name": "Ноутбук",
    "price": 19999.99,
    "in_stock": false
  }
}
```

---

### 🚫 3. Автоматична валідація

* Якщо вказати неправильний тип (`price: "abc"`), FastAPI автоматично поверне 422 з описом помилки.

---

### 🧩 4. Вкладені моделі

```python
class User(BaseModel):
    username: str
    email: str

class Order(BaseModel):
    item: Item
    buyer: User
```

---

### 📤 5. Відповіді з моделями

```python
@app.get("/item", response_model=Item)
def get_item():
    return {"name": "Мишка", "price": 499.0, "in_stock": True}
```

> `response_model` дозволяє автоматично серіалізувати і фільтрувати поля відповіді.

---

### 📋 6. Упражнення

1. Створи модель `Book` з полями: `title: str`, `author: str`, `pages: int`, `published: bool = False`
2. Додай POST-роут `/books/` для прийому книжки.
3. Додай GET-роут `/book` з `response_model=Book`.

Прекрасно! Настав час зробити наш API більш візуальним 🌐

---

## 🔹 Глава 5: Шаблони (Jinja2) та HTML-інтерфейс у FastAPI

FastAPI в основному — це API-фреймворк, але його легко розширити для відображення HTML-сторінок, використовуючи шаблонізатор **Jinja2**.

---

### 📦 1. Встановлення Jinja2

```bash
pip install jinja2
```

> Також додатково встановимо `aiofiles` для асинхронної роботи з файлами:

```bash
pip install aiofiles
```

---

### 🗂️ 2. Структура проєкту з шаблонами

```
fastapi_project/
│
├── main.py
└── templates/
    └── home.html
```

---

### ⚙️ 3. Підключення шаблонів у FastAPI

```python
from fastapi import FastAPI, Request
from fastapi.responses import HTMLResponse
from fastapi.templating import Jinja2Templates

app = FastAPI()
templates = Jinja2Templates(directory="templates")

@app.get("/", response_class=HTMLResponse)
async def home(request: Request):
    return templates.TemplateResponse("home.html", {"request": request, "title": "FastAPI сайт"})
```

---

### 📝 4. Приклад шаблону `templates/home.html`

```html
<!DOCTYPE html>
<html>
<head>
    <title>{{ title }}</title>
</head>
<body>
    <h1>Ласкаво просимо до FastAPI!</h1>
    <p>Це HTML-сторінка, згенерована Jinja2.</p>
</body>
</html>
```

> Обов’язково передавати об’єкт `request` у шаблон, навіть якщо не використовуєш його безпосередньо.

---

### 🧠 5. Передача змінних у шаблон

```python
@app.get("/hello/{name}", response_class=HTMLResponse)
async def greet_user(request: Request, name: str):
    return templates.TemplateResponse("home.html", {
        "request": request,
        "title": f"Привіт, {name}",
        "user_name": name
    })
```

У шаблоні:

```html
<h2>Привіт, {{ user_name }}!</h2>
```

---

### 📋 6. Упражнення

1. Створи шаблон `user.html`, який приймає ім’я та виводить “Вітаємо, {ім’я}”.
2. Створи маршрут `/user/{username}`.
3. Передай змінні в шаблон і відобрази в HTML.

Чудово! Тепер додамо інтерактивність — вчимося працювати з **HTML-формами та обробкою POST-запитів** 📝

---

## 🔹 Глава 6: Робота з формами та обробка POST-запитів

FastAPI дозволяє легко обробляти дані, які приходять із HTML-форм, через тип `Form`.

---

### 📦 1. Імпортуємо потрібні компоненти

```python
from fastapi import Form
```

---

### 📄 2. HTML-форма у шаблоні

```html
<!-- templates/form.html -->
<!DOCTYPE html>
<html>
<head>
    <title>Форма</title>
</head>
<body>
    <h2>Заповніть форму</h2>
    <form action="/submit" method="post">
        <label for="name">Ім'я:</label>
        <input type="text" id="name" name="name">
        <br>
        <label for="age">Вік:</label>
        <input type="number" id="age" name="age">
        <br>
        <button type="submit">Надіслати</button>
    </form>
</body>
</html>
```

---

### ⚙️ 3. GET-запит для показу форми

```python
from fastapi import Request
from fastapi.templating import Jinja2Templates
from fastapi.responses import HTMLResponse

templates = Jinja2Templates(directory="templates")

@app.get("/form", response_class=HTMLResponse)
async def show_form(request: Request):
    return templates.TemplateResponse("form.html", {"request": request})
```

---

### 📬 4. Обробка POST-даних

```python
from fastapi import Form

@app.post("/submit")
async def handle_form(name: str = Form(...), age: int = Form(...)):
    return {"Ім'я": name, "Вік": age}
```

> `Form(...)` означає, що поле є обов’язковим.

---

### 📄 5. Альтернатива — повертати HTML

Можна повернути шаблон як відповідь:

```python
@app.post("/submit", response_class=HTMLResponse)
async def handle_form(request: Request, name: str = Form(...), age: int = Form(...)):
    return templates.TemplateResponse("result.html", {
        "request": request,
        "name": name,
        "age": age
    })
```

`templates/result.html`:

```html
<h1>Результат</h1>
<p>Ваше ім’я: {{ name }}</p>
<p>Ваш вік: {{ age }}</p>
```

---

### 🧪 Упражнення

1. Створи сторінку `/feedback`, де є форма з полем `message`.
2. При надсиланні покажи повідомлення “Дякуємо за ваш відгук: {message}”.
3. Додай перевірку, щоб поле не було порожнім (через `Form(...)`).

Чудово! Переходимо до **збереження даних у базі даних** — створимо справжній бекенд 💾

---

## 🔹 Глава 7: Робота з базою даних (SQLite + SQLModel)

### 🔧 Що таке SQLModel?

**SQLModel** — це бібліотека від автора FastAPI, яка об’єднує:

* простоту **Pydantic**,
* силу **SQLAlchemy**.

> Вона дозволяє описати модель **один раз** і використовувати її для перевірки, створення таблиць і запитів.

---

### 📦 1. Встановлення SQLModel

```bash
pip install sqlmodel
```

---

### 🗂️ 2. Структура проєкту з БД

```
fastapi_project/
│
├── main.py
└── database.db  ← буде створена автоматично
```

---

### 🧱 3. Створення моделі

```python
from sqlmodel import SQLModel, Field
from typing import Optional

class User(SQLModel, table=True):
    id: Optional[int] = Field(default=None, primary_key=True)
    name: str
    age: int
```

> `table=True` — це вказівка, що це таблиця БД.
> `id` — автогенерується.

---

### ⚙️ 4. Підключення до SQLite

```python
from sqlmodel import create_engine, Session

sqlite_file_name = "database.db"
sqlite_url = f"sqlite:///{sqlite_file_name}"

engine = create_engine(sqlite_url, echo=True)  # echo=True = лог запитів
```

---

### 🏗️ 5. Ініціалізація таблиць

```python
def create_db():
    SQLModel.metadata.create_all(engine)
```

> Викличи `create_db()` один раз при старті застосунку.

---

### ➕ 6. Додавання даних

```python
@app.post("/users/")
def create_user(name: str = Form(...), age: int = Form(...)):
    user = User(name=name, age=age)
    with Session(engine) as session:
        session.add(user)
        session.commit()
        session.refresh(user)
    return user
```

---

### 📋 7. Отримання всіх користувачів

```python
from typing import List
from sqlmodel import select

@app.get("/users/", response_model=List[User])
def get_users():
    with Session(engine) as session:
        users = session.exec(select(User)).all()
        return users
```

---

### 🧪 Упражнення

1. Створи модель `Book` з полями `id`, `title`, `author`, `pages`.
2. Створи маршрут POST `/books/`, який додає книжку.
3. Створи GET `/books/` для перегляду всіх книжок.

Отже, готуємося зануритися у світ асинхронності! ⚡

---

## 🔹 Глава 8: Асинхронність, Background Tasks та WebSocket у FastAPI

---

### 🌀 1. Асинхронні функції в FastAPI

FastAPI підтримує і синхронні, і асинхронні обробники.

```python
@app.get("/async")
async def async_endpoint():
    return {"message": "Це асинхронний маршрут"}
```

Асинхронність дозволяє не блокувати сервер під час очікування довгих операцій (наприклад, запитів до бази чи зовнішніх API).

---

### ⏳ 2. Background Tasks (Фонові завдання)

Це завдання, які запускаються після відповіді користувачу, не блокуючи його.

```python
from fastapi import BackgroundTasks

def write_log(message: str):
    with open("log.txt", "a") as f:
        f.write(message + "\n")

@app.post("/send/")
async def send_message(background_tasks: BackgroundTasks, message: str):
    background_tasks.add_task(write_log, message)
    return {"msg": "Повідомлення отримано"}
```

---

### 🔄 3. WebSocket — двонаправлене спілкування в реальному часі

WebSocket дозволяє створювати чат, онлайн-гру тощо.

```python
from fastapi import WebSocket

@app.websocket("/ws")
async def websocket_endpoint(websocket: WebSocket):
    await websocket.accept()
    while True:
        data = await websocket.receive_text()
        await websocket.send_text(f"Повідомлення отримано: {data}")
```

---

### 🧪 Упражнення

1. Створи асинхронний маршрут `/wait`, який імітує очікування 5 секунд (`await asyncio.sleep(5)`).
2. Додай Background Task, який записує час виклику в лог.
3. Напиши простий WebSocket чат, який приймає і повертає повідомлення.

Чудово, перейдемо до одного з найважливіших аспектів — **безпека і аутентифікація** у FastAPI 🔐

---

## 🔹 Глава 9: Аутентифікація і безпека (OAuth2 + JWT)

---

### 1. Основи аутентифікації

* **OAuth2** — протокол авторизації, який дозволяє отримати токен доступу.
* **JWT (JSON Web Token)** — формат токена, що містить закодовану інформацію про користувача.

---

### 2. Встановлення бібліотек

```bash
pip install python-jose[cryptography] passlib[bcrypt]
```

* `python-jose` — для генерації і валідації JWT.
* `passlib[bcrypt]` — для хешування паролів.

---

### 3. Основні кроки:

#### а) Модель користувача

```python
from pydantic import BaseModel

class User(BaseModel):
    username: str
    hashed_password: str
```

#### б) Хешування пароля

```python
from passlib.context import CryptContext

pwd_context = CryptContext(schemes=["bcrypt"], deprecated="auto")

def hash_password(password: str):
    return pwd_context.hash(password)

def verify_password(plain_password, hashed_password):
    return pwd_context.verify(plain_password, hashed_password)
```

#### в) Створення JWT токена

```python
from datetime import datetime, timedelta
from jose import jwt

SECRET_KEY = "your_secret_key_here"
ALGORITHM = "HS256"
ACCESS_TOKEN_EXPIRE_MINUTES = 30

def create_access_token(data: dict):
    to_encode = data.copy()
    expire = datetime.utcnow() + timedelta(minutes=ACCESS_TOKEN_EXPIRE_MINUTES)
    to_encode.update({"exp": expire})
    encoded_jwt = jwt.encode(to_encode, SECRET_KEY, algorithm=ALGORITHM)
    return encoded_jwt
```

---

### 4. OAuth2PasswordBearer (FastAPI)

```python
from fastapi.security import OAuth2PasswordBearer, OAuth2PasswordRequestForm

oauth2_scheme = OAuth2PasswordBearer(tokenUrl="token")

@app.post("/token")
async def login(form_data: OAuth2PasswordRequestForm = Depends()):
    user_dict = fake_users_db.get(form_data.username)
    if not user_dict:
        raise HTTPException(status_code=400, detail="Невірний логін")
    user = User(**user_dict)
    if not verify_password(form_data.password, user.hashed_password):
        raise HTTPException(status_code=400, detail="Невірний пароль")
    access_token = create_access_token(data={"sub": user.username})
    return {"access_token": access_token, "token_type": "bearer"}
```

---

### 5. Захищені маршрути

```python
from fastapi import Depends

async def get_current_user(token: str = Depends(oauth2_scheme)):
    try:
        payload = jwt.decode(token, SECRET_KEY, algorithms=[ALGORITHM])
        username = payload.get("sub")
        if username is None:
            raise HTTPException(status_code=401, detail="Невірний токен")
        return username
    except jwt.JWTError:
        raise HTTPException(status_code=401, detail="Невірний токен")

@app.get("/users/me")
async def read_users_me(current_user: str = Depends(get_current_user)):
    return {"username": current_user}
```

---

### 🧪 Упражнення

1. Реалізуй базу користувачів (fake\_users\_db) у вигляді словника.
2. Створи реєстрацію нового користувача з хешуванням пароля.
3. Захисти будь-який маршрут за допомогою токена.

Добре, перейдемо до тестування FastAPI додатків — це важлива складова професійної розробки! 🧪

---

## 🔹 Глава 10: Тестування FastAPI додатків

---

### 1. Встановлення pytest та httpx

```bash
pip install pytest httpx
```

* **pytest** — популярний фреймворк для тестування Python.
* **httpx** — клієнт для асинхронних HTTP-запитів.

---

### 2. Створення тестового клієнта

FastAPI надає `TestClient` на основі `requests`, щоб легко тестувати API.

```python
from fastapi.testclient import TestClient
from main import app  # імпортуємо ваш FastAPI додаток

client = TestClient(app)
```

---

### 3. Приклад тесту для GET-запиту

```python
def test_read_main():
    response = client.get("/")
    assert response.status_code == 200
    assert response.json() == {"message": "Hello World"}
```

---

### 4. Тестування POST-запиту з формою

```python
def test_create_user():
    response = client.post(
        "/users/",
        data={"name": "Alice", "age": 30}
    )
    assert response.status_code == 200
    data = response.json()
    assert data["name"] == "Alice"
    assert data["age"] == 30
    assert "id" in data
```

---

### 5. Тестування захищених маршрутів (з токеном)

```python
def test_get_current_user():
    # Спочатку отримуємо токен
    response = client.post(
        "/token",
        data={"username": "testuser", "password": "testpass"}
    )
    token = response.json()["access_token"]

    headers = {"Authorization": f"Bearer {token}"}
    response = client.get("/users/me", headers=headers)
    assert response.status_code == 200
    assert response.json()["username"] == "testuser"
```

---

### 6. Запуск тестів

Запускаємо всі тести командою у терміналі:

```bash
pytest
```

---

### 🧪 Упражнення

1. Напиши тест для маршруту `/books/` (створення та отримання списку).
2. Напиши тест на випадок невірного логіна (401).
3. Створи тест, що перевіряє, що поле `age` обов’язкове і має бути числом.

Гарно, тепер розглянемо, як розгортати FastAPI в продакшн — це важливий крок для справжніх проєктів! 🚀

---

## 🔹 Глава 11: Розгортання FastAPI додатків (Docker, Heroku, AWS)

---

### 1. Розгортання з Docker

---

#### а) Dockerfile — описує, як збирати образ

```dockerfile
# Візьмемо офіційний Python образ
FROM python:3.11-slim

# Встановлюємо робочу директорію
WORKDIR /app

# Копіюємо файли в контейнер
COPY requirements.txt .

# Встановлюємо залежності
RUN pip install --no-cache-dir -r requirements.txt

# Копіюємо весь код
COPY . .

# Запускаємо Uvicorn сервер
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
```

---

#### б) Створення requirements.txt

```bash
pip freeze > requirements.txt
```

---

#### в) Команди для збірки та запуску

```bash
docker build -t fastapi-app .
docker run -d -p 8000:8000 fastapi-app
```

---

### 2. Розгортання на Heroku

---

#### а) Створіть файл Procfile

```text
web: uvicorn main:app --host=0.0.0.0 --port=${PORT:-5000}
```

---

#### б) Команди для деплою

```bash
heroku create your-app-name
git push heroku main
heroku ps:scale web=1
heroku open
```

---

### 3. Розгортання на AWS (Elastic Beanstalk)

---

* Створіть `Dockerrun.aws.json` або використайте EB CLI.
* Завантажте ваш Docker образ або код.
* Elastic Beanstalk автоматично розгорне додаток.

---

### 4. Налаштування HTTPS і CORS

* Для HTTPS використовуйте Nginx або сертифікати Let's Encrypt.
* Для Cross-Origin Resource Sharing (CORS):

```python
from fastapi.middleware.cors import CORSMiddleware

app.add_middleware(
    CORSMiddleware,
    allow_origins=["*"],  # змініть на конкретні домени в продакшн
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)
```

---

### 🧪 Упражнення

1. Створи Docker контейнер для свого FastAPI додатку.
2. Розгорни додаток на Heroku.
3. Налаштуй CORS для свого API.

Окей, тепер поговоримо про те, як оптимізувати та масштабувати FastAPI додатки, щоб вони справлялися з великим навантаженням і працювали максимально ефективно. ⚙️🚀

---

## 🔹 Глава 12: Оптимізація і масштабування FastAPI

---

### 1. Використання Uvicorn із Workers (gunicorn)

FastAPI працює на Uvicorn, але для кращої продуктивності в продакшні часто запускають кілька воркерів через Gunicorn.

**Команда запуску:**

```bash
gunicorn -k uvicorn.workers.UvicornWorker main:app --workers 4 --bind 0.0.0.0:8000
```

* `--workers 4` — кількість процесів, що обробляють запити.

---

### 2. Кешування

* Використовуйте кешування результатів запитів, наприклад, Redis.
* Можна кешувати обчислення, часті відповіді, або сесії.

```python
import aioredis

redis = await aioredis.create_redis_pool("redis://localhost")

@app.get("/data")
async def get_data():
    data = await redis.get("key")
    if not data:
        data = compute_expensive_data()
        await redis.set("key", data)
    return data
```

---

### 3. Використання CDN

* Для статики (картинки, JS, CSS) використовуйте Content Delivery Network (CDN) — це зменшить навантаження на сервер.

---

### 4. Горизонтальне масштабування

* Розгортайте кілька екземплярів додатку за допомогою Docker Swarm, Kubernetes або в хмарі.
* Використовуйте балансувальник навантаження (Load Balancer).

---

### 5. Моніторинг і логування

* Інтегруйте сервіси моніторингу (Prometheus, Grafana, Sentry).
* Логи записуйте у файл або зовнішній сервіс.

---

### 6. Оптимізація коду

* Уникайте блокуючих операцій у асинхронних функціях.
* Використовуйте ефективні алгоритми та структури даних.
* Профілюйте додаток (cProfile, py-spy).

---

### 🧪 Упражнення

1. Запусти FastAPI з Gunicorn і кількома воркерами.
2. Реалізуй кешування з Redis.
3. Налаштуй базове логування в додатку.

