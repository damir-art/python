# CTkLabel

## 🧾 Что такое `CTkLabel`

Это просто **текстовая метка**, как заголовок или подпись к полю.
В обычном Tkinter она называлась `Label`, а здесь — `CTkLabel`, с поддержкой:

* Темной темы 🖤
* Кастомных шрифтов и размеров
* Цветов и выравнивания

---

## ⚙️ Основные параметры:

| Параметр     | Описание                              |
| ------------ | ------------------------------------- |
| `text`       | Что будет написано                    |
| `font`       | Кортеж: (шрифт, размер, \[жирность])  |
| `text_color` | Цвет текста (можно hex или `"white"`) |
| `anchor`     | Выравнивание текста                   |

---

## 🧪 Пример метки над полем:

```python
import customtkinter as ctk

ctk.set_appearance_mode("dark")
ctk.set_default_color_theme("blue")

app = ctk.CTk()
app.geometry("800x600")
app.title("SEO-анализатор")

# Метка
label = ctk.CTkLabel(app, text="Введите URL для анализа", font=("Arial", 18))
label.pack(pady=(40, 10))

# Поле
url_entry = ctk.CTkEntry(app, placeholder_text="https://example.com", width=500)
url_entry.pack(pady=(0, 10))

app.mainloop()
```

📌 `pady=(40, 10)` — отступ сверху 40, снизу 10
📌 `font=("Arial", 18)` — шрифт Arial, размер 18 пикселей

---

### 😎 Дальше — кнопка? Или добавим анимацию или шрифт посовременнее?

Ты капитан — куда рулить, туда и плывём 🛶
