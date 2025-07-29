# 🔍 Цель: получить `<title>` по введённому URL

---

## 📦 Что нам нужно:

1. **Библиотека `requests`** — чтобы скачать страницу
2. **Библиотека `BeautifulSoup` из `bs4`** — чтобы распарсить HTML
3. **Обработка исключений** — вдруг нет интернета, сайт не отвечает, или HTML битый
4. **Вывод результата в `CTkTextbox`** — уже готово

---

## 🛠 Установка зависимостей (один раз в виртуалке):

```bash
pip install requests beautifulsoup4
```

---

## 🧪 Мини-проверка (без GUI):

Вот чистый пример кода, чтобы **проверить парсинг `title`**:

```python
import requests
from bs4 import BeautifulSoup

url = "https://example.com"

try:
    response = requests.get(url, timeout=10)
    response.raise_for_status()  # если ошибка — выбросить исключение

    soup = BeautifulSoup(response.text, "html.parser")
    title = soup.title.string if soup.title else "Нет тега <title>"

    print("Заголовок страницы:", title)

except Exception as e:
    print("Ошибка при запросе:", e)
```

---

## 🧠 Что происходит:

* Скачиваем HTML с помощью `requests.get()`
* Передаём в `BeautifulSoup`
* Ищем `soup.title.string`
* Если заголовка нет — пишем об этом

---

## 📦 Варианты ошибок, которые будем ловить:

* `requests.exceptions.RequestException` — общая ошибка при запросе
* `AttributeError` — если нет `soup.title`
* `ValueError`, `TypeError` — на всякий случай

---

## Следующий шаг:

✅ Убедись, что это работает в консоли
📦 Установи `requests` и `bs4`, если ещё не ставил
💬 И скажи мне, и мы **вставим этот код в GUI**, чтобы при нажатии на кнопку выводился заголовок сайта

🚀 Готов?

Вот это я понимаю — **зелёный свет от Даяна**! 💥
Готовься, сейчас мы встроим настоящий **парсинг тега `<title>`** в твой красивый SEO-анализатор!

---

## 🔍 Что будет происходить:

1. Пользователь вводит URL
2. Нажимает кнопку “Анализировать”
3. Мы:

   * скачиваем HTML через `requests`
   * вытаскиваем `<title>` с помощью `BeautifulSoup`
   * выводим результат в `CTkTextbox`

---

## ✅ Обновлённый код GUI с анализом `<title>`:

```python
import customtkinter as ctk
import requests
from bs4 import BeautifulSoup

# Настройки темы
ctk.set_appearance_mode("dark")
ctk.set_default_color_theme("blue")

# Окно
app = ctk.CTk()
app.title("SEO-анализатор")
app.geometry("800x600")
app.resizable(False, False)

# Метка
label = ctk.CTkLabel(app, text="Введите URL для анализа", font=("Arial", 18))
label.pack(pady=(40, 10))

# Поле ввода URL
url_entry = ctk.CTkEntry(app, placeholder_text="https://example.com", width=500)
url_entry.pack(pady=(0, 20))

# Текстбокс для вывода
output_box = ctk.CTkTextbox(app, width=700, height=250, corner_radius=10)
output_box.pack(pady=10)
output_box.configure(state="disabled")

# Функция анализа
def analyze():
    url = url_entry.get().strip()

    output_box.configure(state="normal")
    output_box.delete("1.0", "end")  # очистим поле

    try:
        output_box.insert("end", f"Анализируем: {url}\n\n")
        response = requests.get(url, timeout=10)
        response.raise_for_status()
        soup = BeautifulSoup(response.text, "html.parser")

        title = soup.title.string.strip() if soup.title else "Нет тега <title>"

        output_box.insert("end", f"Заголовок страницы (title):\n{title}")

    except requests.exceptions.RequestException as e:
        output_box.insert("end", f"Ошибка при запросе:\n{e}")

    except Exception as e:
        output_box.insert("end", f"Произошла ошибка:\n{e}")

    output_box.configure(state="disabled")

# Кнопка
analyze_button = ctk.CTkButton(app, text="Анализировать", command=analyze, width=200)
analyze_button.pack(pady=10)

# Запуск
app.mainloop()
```

---

## 🧪 Как тестить?

Попробуй вводить:

* `https://example.com`
* `https://www.python.org`
* `https://www.google.com`

И смотри, как `TextBox` выводит результат.

---

## ⏭ Готов продолжать?

Можем добавлять:

* `<meta name="description">`
* `<meta name="keywords">`
* `<h1>` заголовки
* Все ссылки с `href`
* Или кнопку "Очистить"

Как скажешь — так и будет, босс SEO 😎

Скрипт с комментариями:

С удовольствием, Даян! 🧠
Вот твой код с **подробным комментарием к каждой строчке**, чтобы всё было как на ладони. Ни одна строка не ускользнёт! 🕵️‍♂️

---

```python
# Импорт библиотеки customtkinter для красивого GUI
import customtkinter as ctk

# Импорт библиотеки requests для скачивания HTML-страниц
import requests

# Импорт BeautifulSoup для парсинга HTML-кода
from bs4 import BeautifulSoup

# Установка тёмной темы оформления (можно "light", "dark", "system")
ctk.set_appearance_mode("dark")

# Установка цветовой схемы (можно "blue", "green", "dark-blue")
ctk.set_default_color_theme("blue")

# Создание главного окна приложения
app = ctk.CTk()

# Установка заголовка окна
app.title("SEO-анализатор")

# Задание размера окна: ширина 800px, высота 600px
app.geometry("800x600")

# Запрет изменения размеров окна мышкой (фиксированный размер)
app.resizable(False, False)

# Создание текстовой метки с заголовком над полем ввода
label = ctk.CTkLabel(
    app,
    text="Введите URL для анализа",  # Текст на метке
    font=("Arial", 18)               # Шрифт: Arial, размер 18
)
label.pack(pady=(40, 10))  # Отступ сверху 40px, снизу 10px

# Создание однострочного поля для ввода URL-адреса
url_entry = ctk.CTkEntry(
    app,
    placeholder_text="https://example.com",  # Подсказка внутри поля
    width=500                                # Ширина поля в пикселях
)
url_entry.pack(pady=(0, 20))  # Отступ снизу 20px

# Создание текстового блока для вывода результатов
output_box = ctk.CTkTextbox(
    app,
    width=700,              # Ширина
    height=250,             # Высота
    corner_radius=10        # Закруглённые углы
)
output_box.pack(pady=10)  # Отступ сверху и снизу 10px
output_box.configure(state="disabled")  # Делаем поле только для чтения

# Функция, которая будет вызываться при нажатии на кнопку "Анализировать"
def analyze():
    url = url_entry.get().strip()  # Получаем URL из поля и удаляем пробелы

    output_box.configure(state="normal")  # Делаем поле доступным для записи
    output_box.delete("1.0", "end")       # Очищаем всё содержимое текстбокса

    try:
        output_box.insert("end", f"Анализируем: {url}\n\n")  # Пишем начало отчёта
        response = requests.get(url, timeout=10)             # Делаем GET-запрос к сайту
        response.raise_for_status()                          # Проверка: если код ошибки — выбросить исключение

        soup = BeautifulSoup(response.text, "html.parser")   # Парсим HTML с помощью BeautifulSoup

        # Получаем содержимое тега <title>, если он есть
        title = soup.title.string.strip() if soup.title else "Нет тега <title>"

        # Выводим заголовок страницы в текстовое поле
        output_box.insert("end", f"Заголовок страницы (title):\n{title}")

    except requests.exceptions.RequestException as e:
        # Если произошла ошибка при запросе (например, нет интернета или сайт не отвечает)
        output_box.insert("end", f"Ошибка при запросе:\n{e}")

    except Exception as e:
        # Все остальные ошибки (например, парсинг)
        output_box.insert("end", f"Произошла ошибка:\n{e}")

    output_box.configure(state="disabled")  # Снова делаем поле только для чтения

# Создание кнопки "Анализировать", которая вызывает функцию analyze()
analyze_button = ctk.CTkButton(
    app,
    text="Анализировать",    # Текст на кнопке
    command=analyze,         # Функция, вызываемая при клике
    width=200                # Ширина кнопки
)
analyze_button.pack(pady=10)  # Отступ сверху и снизу 10px

# Запускаем главное окно приложения (вечный цикл, пока окно не закроют)
app.mainloop()
```

---

## 🎓 Результат:

Теперь ты знаешь, что делает **каждая строчка**.
Никакой магии, только чистая логика — прямо как мы любим 💪

Готов расширять функциональность? Можем добавить:

* `meta description`
* список `<h1>`
* вывод ссылок `<a href=...>`

Как скажешь, так и будет, Даян 👨‍💻✨
