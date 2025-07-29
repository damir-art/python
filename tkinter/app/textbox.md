# Текстовое поле
Сначала — **чистый, изолированный пример `CTkTextbox`**, чтобы ты его спокойно проверил, без кнопок, без ввода, просто посмотреть, как он работает.

---

## 🧪 Простой пример `CTkTextbox` в действии:

```python
import customtkinter as ctk

# Настройка внешнего вида
ctk.set_appearance_mode("dark")
ctk.set_default_color_theme("blue")

# Окно
app = ctk.CTk()
app.title("Тест TextBox")
app.geometry("600x400")

# TextBox
textbox = ctk.CTkTextbox(app, width=500, height=250, corner_radius=10)
textbox.pack(pady=30)

# Вставим текст
textbox.insert("0.0", "Привет, Даян!\n\nЭто тест CTkTextbox.\nТы можешь писать сюда сколько угодно текста.")
textbox.insert("end", "\n\n...и он автоматически переносится, если ты включишь wrap!")

# Делает текстбокс только для чтения (необязательно)
# textbox.configure(state="disabled")

app.mainloop()
```

---

## 📝 Что ты увидишь:

* Окошко
* Большой текстбокс
* В нём сразу написано приветствие
* Можно редактировать — если не заблокировал `state="disabled"`

---

## 💡 Хочешь поиграться?

Можешь добавить:

```python
textbox.delete("1.0", "end")  # Очистить всё
```

или получить текст:

```python
print(textbox.get("1.0", "end"))
```

---

## 📜 Сегодня в фокусе — `ctk.CTkTextbox`

### Что это?

Это **многострочное текстовое поле** — аналог `tk.Text`, но:

* стильное
* тёмное (если тема темная)
* с поддержкой прокрутки
* можно вставлять, удалять, выделять текст
* может быть доступным или только для чтения

---

## ⚙️ Основные параметры:

| Параметр          | Описание                                                   |
| ----------------- | ---------------------------------------------------------- |
| `master`          | Родитель (например, `app`)                                 |
| `width`, `height` | Размеры (в пикселях)                                       |
| `corner_radius`   | Скруглённость углов                                        |
| `state`           | `"normal"` (можно писать) или `"disabled"` (только чтение) |
| `font`            | Шрифт текста внутри                                        |
| `text_color`      | Цвет текста                                                |
| `fg_color`        | Цвет фона поля                                             |
| `wrap`            | Перенос строк (`"word"` или `"char"`)                      |

---

## ✍️ Методы:

| Метод                   | Что делает                             |
| ----------------------- | -------------------------------------- |
| `.insert("end", text)`  | Вставить текст в конец                 |
| `.delete("1.0", "end")` | Удалить всё                            |
| `.get("1.0", "end")`    | Получить текст                         |
| `.configure(state=...)` | Изменить доступность (normal/disabled) |

> ⚠️ Важно: `TextBox` использует координаты в стиле `"1.0"` — строка 1, символ 0.

---

## 🎯 Что мы хотим:

* Текстбокс под кнопкой
* При нажатии на кнопку — туда добавляется `“Анализируем URL”`
* Пока текстбокс будет **только для чтения**

---

## 🚧 Обновим интерфейс — поэтапно:

### 📦 Добавим `CTkTextbox` и вставим текст:

```python
import customtkinter as ctk

# Настройка темы
ctk.set_appearance_mode("dark")
ctk.set_default_color_theme("blue")

app = ctk.CTk()
app.title("SEO-анализатор")
app.geometry("800x600")
app.resizable(False, False)

# Метка
label = ctk.CTkLabel(app, text="Введите URL для анализа", font=("Arial", 18))
label.pack(pady=(40, 10))

# Поле ввода
url_entry = ctk.CTkEntry(app, placeholder_text="https://example.com", width=500)
url_entry.pack(pady=(0, 20))

# Текстбокс для вывода
output_box = ctk.CTkTextbox(app, width=700, height=250, corner_radius=10)
output_box.pack(pady=10)
output_box.configure(state="disabled")  # делаем только для чтения

# Кнопка
def analyze():
    url = url_entry.get()
    
    # Делаем поле доступным, вставляем текст, снова блокируем
    output_box.configure(state="normal")
    output_box.delete("1.0", "end")
    output_box.insert("end", f"Анализируем URL: {url}")
    output_box.configure(state="disabled")

analyze_button = ctk.CTkButton(app, text="Анализировать", command=analyze, width=200)
analyze_button.pack(pady=10)

app.mainloop()
```

---

## 🔥 И вуаля!

* Поле для URL
* Кнопка
* Стильный тёмный `TextBox`, в который попадает текст по нажатию
* Всё по центру, чисто, красиво

---

Готов двигаться дальше?
Варианты:

1. Реально парсить HTML (`requests + BeautifulSoup`)
2. Добавить кнопку “Очистить”
3. Сделать прокрутку, если текста много
4. Настроить вывод заголовка и мета-тегов

Как скажешь, командир SEO-интерфейсов 😎
