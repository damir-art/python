# Курс по фласк
- README.md - установка фласк
- page.md - создание страниц
- route.md - маршруты
- jinja2.md - шаблонизатор
- get-post.md - GET / POST во Flask
- form.md - форма
- data-storage.md - где хранятся данные во Flask
- memory-list.md - список памяти
- JSON, Сессии, Флэш, авторизация - пока нет по ним уроков
- sqlalchemy.md - SQLAlchemy работаем с базой данных

Когда изучаешь **Flask с нуля**, главное — не нырять сразу в глубины базы данных и форм с валидацией, а **выстроить логичный маршрут от простого к сложному**.

Фреймворк — это как большой дом: сначала нужно понять, где дверь, как в него войти, а потом уже думать о ремонте и мебели.

---

## 🔑 Первые шаги: Понять фундамент Flask

Вот в каком порядке лучше изучать Flask, чтобы не перегореть и не запутаться:

---

### 1. 🧭 **Маршруты (Routing)**

Это основа. Flask — это веб-фреймворк, а значит всё крутится вокруг **маршрутов**.

```python
@app.route('/')
def home():
    return 'Главная страница'
```

🔹 На этом этапе важно понять:

* Что такое `@app.route`
* Как делать URL-параметры (`/user/<name>`)
* Как возвращать HTML или JSON

---

### 2. 🖼️ **Шаблоны (Jinja2)**

Дальше ты не просто будешь возвращать текст, а начнёшь использовать **HTML-шаблоны**.

```python
from flask import render_template

@app.route('/')
def home():
    return render_template('index.html', name='Даян')
```

🔹 Изучи:

* Папку `templates/`
* Как передавать переменные в шаблон
* Как использовать циклы и условия в Jinja2

---

### 3. 🔀 **Передача данных: GET и POST**

Понимание разницы между **GET** и **POST** запросами — ключ к взаимодействию с формами и фронтендом.

```python
@app.route('/form', methods=['GET', 'POST'])
def form():
    if request.method == 'POST':
        data = request.form['username']
        return f'Привет, {data}!'
    return render_template('form.html')
```

---

### 4. 🧾 **Формы и `request`**

Работа с формами — следующий этап.

🔹 Изучи:

* Как обрабатывать `request.form`
* Как проверять `request.method`
* Как получать `request.args` (GET параметры)

---

### 5. 🗃️ **Статические файлы**

Фронтенд требует CSS, картинок и JS. Flask даёт для этого папку `static/`.

```html
<link rel="stylesheet" href="{{ url_for('static', filename='styles.css') }}">
```

---

### 6. 🧠 **Передача и хранение данных: `session`, `flash`**

Когда захочешь что-то временно сохранять между запросами — пригодится `session`.

```python
session['username'] = 'Даян'
```

Также `flash()` помогает показывать уведомления.

---

### 7. 🗄️ **Базы данных**

Когда уже умеешь показывать страницы, обрабатывать формы — можно двигаться к **базам данных**.

🔹 Стартуй с:

* SQLite (встроен)
* SQLAlchemy (ORM, объектно-реляционное отображение)
* Flask-Migrate (миграции)

Пример:

```python
from flask_sqlalchemy import SQLAlchemy
db = SQLAlchemy(app)

class User(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(80))
```

---

### 8. 🧱 **Структура проекта**

Когда у тебя уже не один файл, а много — начни изучать **структуру Flask-проекта**:

```
myapp/
├── app.py
├── templates/
├── static/
├── models.py
├── routes.py
├── forms.py
```

---

### 9. 🛡️ **Form Validation с WTForms**

Когда устанешь валидировать руками — подключи WTForms:

```python
from flask_wtf import FlaskForm
class MyForm(FlaskForm):
    username = StringField('Имя', validators=[DataRequired()])
```

---

### 10. 🧩 **Blueprints и расширения**

Когда проект становится большим — дели его на **blueprints** (модули):

```python
from flask import Blueprint
admin = Blueprint('admin', __name__)
```

---

## 🧭 Краткий маршрут обучения

| Этап | Что учить  | Пример                         |
| ---- | ---------- | ------------------------------ |
| 1    | Routing    | `@app.route()`                 |
| 2    | Шаблоны    | `render_template()` + Jinja2   |
| 3    | GET/POST   | `request.form`, `request.args` |
| 4    | Формы      | HTML + Flask                   |
| 5    | Статика    | `url_for('static', ...)`       |
| 6    | Session    | `session[]`, `flash()`         |
| 7    | БД         | SQLite + SQLAlchemy            |
| 8    | Структура  | Разбиение по файлам            |
| 9    | WTForms    | Валидация форм                 |
| 10   | Blueprints | Модульность                    |

---

Если хочешь, я могу составить **план обучения Flask на 7 дней**, как мы делали для Python — с ежедневными мини-проектами и фокусом на практику. Хочешь?
