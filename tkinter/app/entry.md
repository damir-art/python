# Поле ввода
## 🔍 Сегодня в фокусе: `ctk.CTkEntry`

### 📦 Что это такое?

`CTkEntry` — это **однострочное поле для ввода текста**, заменитель `tk.Entry`, только стильный и с удобной настройкой.

---

## ⚙️ Основные параметры:

| Параметр           | Описание                                                |
| ------------------ | ------------------------------------------------------- |
| `master`           | Родитель (обычно `app` или `frame`)                     |
| `placeholder_text` | Текст-подсказка внутри поля (серым, исчезает при вводе) |
| `width` / `height` | Размеры поля                                            |
| `textvariable`     | Привязка к `StringVar()` (альтернатива `.get()`)        |
| `show="*"`         | Скрывает ввод (для паролей)                             |
| `state`            | `"normal"` или `"disabled"`                             |
| `corner_radius`    | Закругление углов (по умолчанию красиво)                |
| `fg_color`         | Цвет фона                                               |

---

## 💬 Методы:

| Метод                 | Описание                               |
| --------------------- | -------------------------------------- |
| `.get()`              | Получить введённый текст               |
| `.insert(0, "текст")` | Вставить текст в поле (позиция, текст) |
| `.delete(0, END)`     | Очистить поле                          |
| `.configure(...)`     | Изменить параметры на лету             |

---

## 🧪 Мини-пример:

```python
import customtkinter as ctk

app = ctk.CTk()
app.geometry("400x200")
app.title("CTkEntry пример")

entry = ctk.CTkEntry(app, placeholder_text="Введи URL", width=300)
entry.pack(pady=40)

def show_input():
    print("Ты ввёл:", entry.get())

btn = ctk.CTkButton(app, text="Показать", command=show_input)
btn.pack()

app.mainloop()
```

---

## 🤘 А теперь по-человечески и поэтапно

### Этап 1. Только `CTkEntry`

```python
import customtkinter as ctk

ctk.set_appearance_mode("dark")
ctk.set_default_color_theme("blue")

app = ctk.CTk()
app.title("SEO-анализатор")
app.geometry("800x600")
app.resizable(False, False)

# Поле для ввода URL
url_entry = ctk.CTkEntry(app, placeholder_text="https://example.com", width=500)
url_entry.pack(pady=40)

app.mainloop()
```

---

🧠 Видишь? Ничего лишнего. Только поле. Всё чисто и красиво.

Готов перейти ко второму кирпичику — `CTkLabel`, чтобы подписать это поле? Или хочешь поиграться с Entry (написать, получить, очистить)? Я с тобой! 💪
