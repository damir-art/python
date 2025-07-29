# Список памяти
Храним посты в списке памяти.

🔥 Поехали, командир! Делаем мини-блог на Flask, где посты будут храниться в **списке в памяти** — всё быстро, просто и наглядно!

---

## ✅ Цель:

* Сделать форму добавления поста
* Хранить посты в списке `posts`
* Отображать все посты на странице

---

## 📁 Структура проекта:

```
project/
├── app.py
└── templates/
    ├── index.html
    ├── form.html
    └── blog.html
```

---

## 📌 Шаг 1: `app.py`

```python
from flask import Flask, render_template, request, redirect

app = Flask(__name__)

# Тут будут храниться посты
posts = []

@app.route("/")
def index():
    return render_template("index.html")

@app.route("/form", methods=["GET", "POST"])
def form():
    if request.method == "POST":
        title = request.form["title"]
        content = request.form["content"]
        # Добавим новый пост в список
        posts.append({"title": title, "content": content})
        return redirect("/blog")
    return render_template("form.html")

@app.route("/blog")
def blog():
    return render_template("blog.html", posts=posts)

if __name__ == "__main__":
    app.run(debug=True)
```

---

## 🧾 Шаг 2: `templates/index.html`

```html
<!DOCTYPE html>
<html>
<head><title>Главная</title></head>
<body>
    <h1>Добро пожаловать</h1>
    <a href="/form">Создать пост</a> | <a href="/blog">Смотреть блог</a>
</body>
</html>
```

---

## 📝 Шаг 3: `templates/form.html`

```html
<!DOCTYPE html>
<html>
<head><title>Создать пост</title></head>
<body>
    <h1>Новый пост</h1>
    <form method="post">
        <p><input type="text" name="title" placeholder="Заголовок" required></p>
        <p><textarea name="content" placeholder="Содержание" rows="5" cols="30" required></textarea></p>
        <p><button type="submit">Опубликовать</button></p>
    </form>
</body>
</html>
```

---

## 📃 Шаг 4: `templates/blog.html`

```html
<!DOCTYPE html>
<html>
<head><title>Блог</title></head>
<body>
    <h1>Блог-посты</h1>
    {% for post in posts %}
        <hr>
        <h2>{{ post.title }}</h2>
        <p>{{ post.content }}</p>
    {% else %}
        <p>Нет постов пока что.</p>
    {% endfor %}
    <a href="/">Назад</a>
</body>
</html>
```

---

## 🧪 Как протестировать:

1. Зайди на `http://127.0.0.1:5000/`
2. Нажми “Создать пост”
3. Заполни и отправь форму
4. Откроется `/blog` со списком всех постов

---

Готово! 🎉 У нас живой блог — пока в оперативной памяти.
Следующий шаг — хочешь сразу перейти на JSON-хранение или поиграем ещё с этой версией (удаление, сортировка, количество символов в заголовке и т.д.)?
