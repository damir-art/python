# 🚀 Сейчас сделаем полноценное мини-приложение с двумя страницами:

* `/` — Главная страница
* `/about` — Страница «О проекте»

Они будут возвращать HTML с помощью шаблонизатора Jinja2 (встроен во Flask).

---

## 📁 Структура проекта

Сделаем стандартную структуру, как принято во Flask:

```
flask_project/
│
├── app.py
├── templates/
│   ├── index.html
│   └── about.html
```

---

## 📄 Шаг 1: `app.py`

```python
from flask import Flask, render_template

app = Flask(__name__)

@app.route("/")
def index():
    return render_template("index.html")  # шаблон для главной

@app.route("/about")
def about():
    return render_template("about.html")  # шаблон для страницы "О проекте"

if __name__ == "__main__":
    app.run(debug=True, port=5001)  # на всякий случай другой порт
```

---

## 📄 Шаг 2: шаблоны в папке `templates/`

### 🔸 `templates/index.html`

```html
<!DOCTYPE html>
<html>
<head>
    <title>Главная страница</title>
</head>
<body>
    <h1>Добро пожаловать!</h1>
    <p>Это главная страница нашего Flask-приложения.</p>
    <a href="/about">О проекте</a>
</body>
</html>
```

---

### 🔸 `templates/about.html`

```html
<!DOCTYPE html>
<html>
<head>
    <title>О проекте</title>
</head>
<body>
    <h1>О проекте</h1>
    <p>Этот проект создан для изучения Flask.</p>
    <a href="/">На главную</a>
</body>
</html>
```

---

## ✅ Как запустить

1. Убедись, что ты в папке с `app.py`.
2. Убедись, что в папке есть подпапка `templates/` и два файла `index.html`, `about.html`.
3. Запусти:

```bash
python app.py
```

Открой в браузере:

* [http://127.0.0.1:5001/](http://127.0.0.1:5001/) — главная
* [http://127.0.0.1:5001/about](http://127.0.0.1:5001/about) — о проекте

---

Готов к следующему шагу? Тогда берёмся за **блог**: список постов, вывод каждого, maybe admin-панель. Готов? 😏
