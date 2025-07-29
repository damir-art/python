# customtkinter

```bash
pip install customtkinter
```

Ооо да, Даян, **customtkinter — это как Tkinter на стероидах** 💪
Там почти те же компоненты, **но они выглядят как в современных приложениях**, с тёмной темой, закруглёнными кнопками, анимацией и даже встроенным выбором темы!

---

## 🧱 Компоненты в `customtkinter`

Вот таблица сопоставления: что было в Tkinter и как это в customtkinter называется:

| Tkinter / ttk     | customtkinter (замена)   | Описание                                     |
| ----------------- | ------------------------ | -------------------------------------------- |
| `tk.Label`        | `ctk.CTkLabel`           | Метка (текст)                                |
| `tk.Button`       | `ctk.CTkButton`          | Кнопка (стильная, с цветами и hover'ом)      |
| `tk.Entry`        | `ctk.CTkEntry`           | Поле ввода                                   |
| `tk.Checkbutton`  | `ctk.CTkCheckBox`        | Чекбокс                                      |
| `tk.Radiobutton`  | `ctk.CTkRadioButton`     | Радиокнопка                                  |
| `ttk.Combobox`    | `ctk.CTkComboBox`        | Выпадающий список                            |
| `tk.Text`         | `ctk.CTkTextbox`         | Многострочное текстовое поле                 |
| —                 | `ctk.CTkSwitch`          | Переключатель (тумблер!)                     |
| `ttk.Progressbar` | `ctk.CTkProgressBar`     | Индикатор загрузки                           |
| `tk.Scale`        | `ctk.CTkSlider`          | Ползунок                                     |
| `tk.Frame`        | `ctk.CTkFrame`           | Контейнер для других элементов               |
| —                 | `ctk.CTkScrollableFrame` | Фрейм с полосой прокрутки                    |
| —                 | `ctk.CTkTabview`         | Вкладки                                      |
| —                 | `ctk.CTkOptionMenu`      | Альтернатива выпадающему меню (как ComboBox) |

---

## ⚙️ Минимальный пример:

Вот тебе первое красивое приложение:

```python
import customtkinter as ctk

ctk.set_appearance_mode("dark")  # можно "light", "dark", или "system"
ctk.set_default_color_theme("blue")  # цвета: blue, green, dark-blue

app = ctk.CTk()
app.title("Привет из customtkinter")
app.geometry("400x300")

label = ctk.CTkLabel(app, text="Добро пожаловать!", font=("Arial", 18))
label.pack(pady=10)

entry = ctk.CTkEntry(app, placeholder_text="Введи своё имя")
entry.pack(pady=10)

def on_click():
    name = entry.get()
    label.configure(text=f"Привет, {name}!")

button = ctk.CTkButton(app, text="Сказать привет", command=on_click)
button.pack(pady=10)

checkbox = ctk.CTkCheckBox(app, text="Согласен с правилами")
checkbox.pack(pady=10)

switch = ctk.CTkSwitch(app, text="Тёмная тема")
switch.pack(pady=10)

app.mainloop()
```

---

## 🧪 Установи библиотеку, если ещё не:

```bash
pip install customtkinter
```

---

## 💭 Идеи на будущее:

* Калькулятор (на `CTkEntry`, `CTkButton`)
* Менеджер задач с прокруткой (`CTkScrollableFrame`)
* Парсер сайта с кнопкой “Анализировать”
* Темы и светлая/тёмная кнопка-переключатель!

---

Ты только скажи — и мы делаем прямо сейчас интерфейс под твой будущий SEO-анализатор или любое приложение, что хочешь 😎
