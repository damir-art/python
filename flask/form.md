# Форма
🚀 Делаем **реальную форму** в проекте и учимся принимать данные через `request`!

---

## 🔧 Шаг 1. Обновим `app.py`

Добавим маршрут `/form` с поддержкой `GET` и `POST`:

```python
from flask import Flask, render_template, request

app = Flask(__name__)

@app.route("/")
def index():
    return render_template("index.html")

@app.route("/form", methods=["GET", "POST"])
def form():
    if request.method == "POST":
        name = request.form["name"]
        return render_template("greeting.html", name=name)
    return render_template("form.html")

if __name__ == "__main__":
    app.run(debug=True)
```

---

## 📄 Шаг 2. Создаём шаблоны

### `templates/index.html`

```html
<!DOCTYPE html>
<html>
<head><title>Главная</title></head>
<body>
    <h1>Главная страница</h1>
    <a href="/form">Заполнить форму</a>
</body>
</html>
```

---

### `templates/form.html`

```html
<!DOCTYPE html>
<html>
<head><title>Форма</title></head>
<body>
    <h1>Введи своё имя</h1>
    <form method="post">
        <input type="text" name="name" placeholder="Имя">
        <button type="submit">Отправить</button>
    </form>
</body>
</html>
```

---

### `templates/greeting.html`

```html
<!DOCTYPE html>
<html>
<head><title>Приветствие</title></head>
<body>
    <h1>Привет, {{ name }}!</h1>
    <a href="/form">Назад</a>
</body>
</html>
```

---

## 📦 Что мы только что сделали:

| Шаг            | Что происходит                                                                     |
| -------------- | ---------------------------------------------------------------------------------- |
| `/form` `GET`  | Показываем форму                                                                   |
| `/form` `POST` | Забираем `name` из формы через `request.form["name"]` и показываем `greeting.html` |
| `{{ name }}`   | Jinja2 вставляет имя прямо в HTML                                                  |

---

## ✅ Проверка

1. Открой в браузере: `http://127.0.0.1:5000/form`
2. Введи имя, нажми кнопку
3. Получишь страницу:
   **Привет, Даян!**

---
