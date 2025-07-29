# SQLAlchemy

Вот это настрой! 🔥 Погнали делать взрослый проект с настоящей базой!
Начнём с самого простого и встроенного решения — **SQLite** через **Flask-SQLAlchemy**.

---

## 🧱 Что будем делать:

1. Установим SQLAlchemy
2. Создадим базу `blog.db`
3. Опишем модель `Post`
4. Перепишем логику добавления и отображения постов

---

## 🛠️ Шаг 1: Установка SQLAlchemy

В твоём виртуальном окружении выполни:

```bash
pip install flask_sqlalchemy
```

---

## 📦 Шаг 2: Настройка базы в `app.py`

В начало файла добавим настройки:

```python
from flask_sqlalchemy import SQLAlchemy

app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///blog.db'
app.config['SQLALCHEMY_TRACK_MODIFICATIONS'] = False

db = SQLAlchemy(app)
```

---

## 🧬 Шаг 3: Создаём модель поста

Под настройками базы:

```python
class Post(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    title = db.Column(db.String(100), nullable=False)
    content = db.Column(db.Text, nullable=False)

    def __repr__(self):
        return f"<Post {self.title}>"
```

---

## 🧱 Шаг 4: Инициализируем базу (один раз!)

В терминале запускаем Python:

```bash
python
```

А внутри:

```python
from app import db
db.create_all()
exit()
```

👆 Появится файл `blog.db` — это и есть база.

---

## 🔁 Шаг 5: Обновляем логику добавления и отображения

### ✅ Добавление поста:

```python
@app.route("/form", methods=["GET", "POST"])
def form():
    if request.method == "POST":
        title = request.form["title"]
        content = request.form["content"]
        new_post = Post(title=title, content=content)
        db.session.add(new_post)
        db.session.commit()
        return redirect("/blog")
    return render_template("form.html")
```

---

### 📤 Отображение постов:

```python
@app.route("/blog")
def blog():
    posts = Post.query.order_by(Post.id.desc()).all()
    return render_template("blog.html", posts=posts)
```

⚠️ В шаблоне `blog.html` менять ничего не нужно — переменная `posts` работает так же!

---

## 🏁 Готово!

Теперь все посты сохраняются в реальной базе `blog.db`, остаются после перезапуска и доступны через SQL-запросы.

---

## 🔥 Хочешь next level?

После этого можем:

* Добавить редактирование/удаление постов
* Перейти к `session`, `flash` и авторизации
* Подключить форму обратной связи и сообщения
* А потом сыграть в REST API — как и договаривались 😎

Скажи, как двигаемся дальше?
