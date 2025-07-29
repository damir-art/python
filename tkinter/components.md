# 🧱 Основные компоненты (виджеты) в Tkinter

Вот список самых важных элементов, которые ты точно будешь использовать:

| Виджет                 | Назначение                                      |
| ---------------------- | ----------------------------------------------- |
| `Tk()`                 | Главное окно приложения                         |
| `Label`                | Текстовая метка (неизменяемая)                  |
| `Button`               | Кнопка, которая может что-то выполнять          |
| `Entry`                | Однострочное текстовое поле                     |
| `Text`                 | Многострочное текстовое поле                    |
| `Checkbutton`          | Чекбокс (галочка)                               |
| `Radiobutton`          | Радиокнопки (выбор одного из нескольких)        |
| `Listbox`              | Список с элементами                             |
| `Spinbox`              | Поле со стрелками для чисел                     |
| `Scale`                | Ползунок (слайдер)                              |
| `Scrollbar`            | Полоса прокрутки                                |
| `Canvas`               | Полотно для рисования фигур                     |
| `Frame`                | Контейнер для группировки других виджетов       |
| `Toplevel`             | Дополнительное окно                             |
| `Menu`                 | Меню (в верхней части окна)                     |
| `Message`              | Как `Label`, но поддерживает автоперенос текста |
| `PanedWindow`          | Разделённое окно, можно перетаскивать границы   |
| `LabelFrame`           | Рамка с заголовком для группировки виджетов     |
| `Combobox` (из ttk)    | Выпадающий список (нужно использовать `ttk`)    |
| `Notebook` (из ttk)    | Вкладки (табы)                                  |
| `Progressbar` (из ttk) | Прогрессбар (индикатор загрузки)                |

---

## 🗂 Модули: `tkinter` и `tkinter.ttk`

* `tkinter` — базовые компоненты (старый стиль)
* `tkinter.ttk` — те же компоненты, но в **современном стиле** (рекомендуется использовать где можно)

Пример подключения обоих:

```python
import tkinter as tk
from tkinter import ttk
```

---

## 📌 Пример — Мини-обзор в действии:

```python
import tkinter as tk
from tkinter import ttk

root = tk.Tk()
root.title("Компоненты Tkinter")

# Метка
label = tk.Label(root, text="Привет, Даян!")
label.pack()

# Поле ввода
entry = tk.Entry(root)
entry.pack()

# Кнопка
def on_click():
    print("Ты нажал кнопку!")
button = tk.Button(root, text="Нажми меня", command=on_click)
button.pack()

# Чекбокс
check = tk.Checkbutton(root, text="Я согласен")
check.pack()

# Радиокнопки
var = tk.StringVar()
radio1 = tk.Radiobutton(root, text="Вариант 1", variable=var, value="1")
radio2 = tk.Radiobutton(root, text="Вариант 2", variable=var, value="2")
radio1.pack()
radio2.pack()

# Список
listbox = tk.Listbox(root)
listbox.insert(1, "Пункт A")
listbox.insert(2, "Пункт B")
listbox.pack()

root.mainloop()
```

---

## 🚀 Дальше?

Можем идти по порядку:

1. Начнём делать мини-проект и по ходу изучать компоненты?
2. Или хочешь углубиться в каждый элемент по отдельности с примерами?

Ты выбираешь — я с тобой до конца! 😎
