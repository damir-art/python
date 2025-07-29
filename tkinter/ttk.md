# ttk
вкладочек, прогрессбаров и стильных комбобоксов.

---

## 💡 Так в чём разница между `tkinter` и `ttk`?

### `tkinter`:

* Классические компоненты
* Устаревший внешний вид (виндовс 98-style, ага)
* Прост и понятен

### `ttk` (`themed tk`):

* Более современный внешний вид (подтягивает стиль твоей ОС)
* Некоторые компоненты только тут: `Combobox`, `Progressbar`, `Notebook`, `Treeview`
* Используются почти те же команды, но нужно писать через `ttk`:

Пример различий:

```python
import tkinter as tk
from tkinter import ttk

root = tk.Tk()

# Старый стиль (tkinter)
tk.Label(root, text="Привет из tkinter").pack()

# Новый стиль (ttk)
ttk.Label(root, text="Привет из ttk").pack()

root.mainloop()
```

---

## 🧠 Запомни простое правило:

🔹 **tk.Label / tk.Entry / tk.Button** — это "олдскул"
🔹 **ttk.Label / ttk.Entry / ttk.Button** — это "моднявый стиль"

---

## 🔧 Хочешь, покажу версию того же примера, но уже через `ttk`?

Говори слово — и я переделаю всё красиво и современно ✨
Или можем сразу делать первый интерфейс на `ttk`. Вперёд?
Ну ты просто машина, Даян! 🤖🧠 Раз сказал — значит будет.

---

## 🔄 Переработанный пример: всё на `ttk`

```python
import tkinter as tk
from tkinter import ttk

root = tk.Tk()
root.title("Компоненты ttk")

# ttk Label
label = ttk.Label(root, text="Привет, Даян! Это TTK!")
label.pack(pady=5)

# ttk Entry
entry = ttk.Entry(root)
entry.pack(pady=5)

# ttk Button
def on_click():
    print("Ты нажал кнопку!")
button = ttk.Button(root, text="Нажми меня", command=on_click)
button.pack(pady=5)

# ttk Checkbutton
check_var = tk.BooleanVar()
check = ttk.Checkbutton(root, text="Я согласен", variable=check_var)
check.pack(pady=5)

# ttk Radiobuttons
radio_var = tk.StringVar()
radio1 = ttk.Radiobutton(root, text="Вариант 1", variable=radio_var, value="1")
radio2 = ttk.Radiobutton(root, text="Вариант 2", variable=radio_var, value="2")
radio1.pack()
radio2.pack()

# ttk Combobox (выпадающий список)
combo = ttk.Combobox(root, values=["Выбор 1", "Выбор 2", "Выбор 3"])
combo.pack(pady=5)

# ttk Progressbar
progress = ttk.Progressbar(root, orient="horizontal", length=200, mode="determinate")
progress.pack(pady=10)
progress["value"] = 50  # от 0 до 100

root.mainloop()
```

---

## 📋 Таблица компонентов `ttk`

Вот тебе таблица самых используемых компонентов из `ttk` — этих красавчиков:

| Компонент         | Описание                                      |
| ----------------- | --------------------------------------------- |
| `ttk.Label`       | Текстовая метка в современном стиле           |
| `ttk.Entry`       | Однострочное текстовое поле                   |
| `ttk.Button`      | Кнопка (современная альтернатива `tk.Button`) |
| `ttk.Checkbutton` | Чекбокс с новым стилем                        |
| `ttk.Radiobutton` | Радиокнопки                                   |
| `ttk.Combobox`    | Выпадающий список                             |
| `ttk.Progressbar` | Индикатор загрузки                            |
| `ttk.Scale`       | Ползунок                                      |
| `ttk.Separator`   | Горизонтальная/вертикальная линия             |
| `ttk.Frame`       | Контейнер для других виджетов                 |
| `ttk.LabelFrame`  | Контейнер с заголовком                        |
| `ttk.Notebook`    | Вкладки (табы)                                |
| `ttk.Treeview`    | Таблицы / списки со столбцами                 |
| `ttk.PanedWindow` | Разделитель между панелями                    |
| `ttk.Style`       | Управление внешним видом всех элементов       |

---

🎁 **Фишка на будущее:** хочешь сделать интерфейс реально красивым — изучи `ttk.Style`. С его помощью можно настраивать цвета, шрифты, анимации и вообще всё.

---

Ну что, готов сделать **своё первое реальное приложение** на `ttk`? Можем начать с:

* Калькулятора
* Списка задач
* Парсера HTML с кнопкой
* Или UI для твоего SEO-анализатора

Выбирай — и я превращу это в магию 👨‍💻✨
