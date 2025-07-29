# Структура проекта
Ты хочешь не просто "написать скрипт", а **делать полноценное приложение**, которое масштабируется, читается, развивается — как настоящий проект. И ты прав: пора **организовывать структуру проекта**.

---

# 🏗 Как структурировать Python-проект (гайд для новичка, но с прицелом на профи)

```bash
pip install requests beautifulsoup4
```

---

## 📁 1. Структура проекта

Вот минимальная и понятная структура для твоего SEO-анализатора:

```
seo_analyzer/
│
├── main.py                # Точка входа — запускает GUI
├── ui.py                  # Вся логика GUI: окна, поля, кнопки
├── analyzer.py            # Логика анализа HTML: title, meta, h1 и т.д.
├── utils.py               # Вспомогательные функции (например, подсчёт символов)
├── config.py              # Настройки по умолчанию (цвета, темы и т.п.)
│
├── requirements.txt       # Список библиотек (для pip install -r)
└── README.md              # Документация проекта
```

🔧 Когда проект подрастёт — можно добавить:

* `assets/` — иконки, шрифты, изображения
* `tests/` — автотесты (да, мы туда дойдём 😉)
* `themes/` — кастомные темы оформления

---

## ⚙ Как это работает

### `main.py`:

```python
from ui import launch_app

if __name__ == "__main__":
    launch_app()
```

### `ui.py`:

* Создаёт окно
* Обрабатывает ввод
* Вызывает функции из `analyzer.py`
* Выводит результат в TextBox

### `analyzer.py`:

* Функция `analyze_url(url)`
* Вытаскивает `<title>`, `<meta>`, `<h1>`, `<a>`
* Возвращает результат как словарь

### `utils.py`:

* Подсчёт символов в title
* Проверка лимита
* Форматирование результата для вывода

---

## 🧠 Почему это удобно?

✅ Читаемо: легче разбираться
✅ Масштабируемо: добавляй новые фичи — не ломая старые
✅ Переиспользуемо: например, потом ты можешь сделать CLI-версию анализатора
✅ Тестируемо: проще писать автотесты к отдельным модулям

---

## 📦 `requirements.txt` — твой пакетный список

Создай файл с содержимым:

```
customtkinter
requests
beautifulsoup4
```

Чтобы потом всё установить одной командой:

```bash
pip install -r requirements.txt
```

---

## 🧰 Дополнительно: шаблоны проектирования?

На данном этапе — можно мягко ввести **разделение ответственности (SRP)** и **модульность**, а позже:

| Шаблон                | Для чего полезен                         |
| --------------------- | ---------------------------------------- |
| MVC / MVVM            | Разделение логики, представления, данных |
| Singleton (на config) | Одиночный доступ к настройкам            |
| Observer              | Реакция UI на действия анализа           |
| Command               | Разделение логики кнопок на команды      |

---

## 🧭 План действий:

1. **Разделим код по файлам** — я помогу всё красиво перенести
2. Продолжим разбор SEO (title, длина, meta, h1, ссылки)
3. Добавим проверки на лимиты (`title ≤ 60 символов`, `description ≤ 160`)
4. Подключим систему форматирования (можно markdown в выводе)
5. Позже — экспорт в файл, или даже генерация отчёта!

---

## 🚀 Готов начать?

Если хочешь — прямо сейчас создадим файлы:

* `main.py`
* `ui.py`
* `analyzer.py`

И я напишу первую версию `analyzer.py`, где будет `analyze_url(url) → dict` с ключами: `title`, `meta`, `h1`, `links`, `warnings`

Давай скажи слово — и мы делаем первый рефакторинг! 😎

Сейчас мы красиво разделим проект на файлы, как настоящие взрослые Python-разработчики 🐍
**Стартуем с базовой структуры + первой рабочей версии `analyzer.py`**

---

## 🧱 Шаг 1: Структура проекта

Создай папку проекта, например:

```
seo_analyzer/
```

Внутри создай файлы:

```
seo_analyzer/
├── main.py
├── ui.py
├── analyzer.py
└── requirements.txt
```

---

## 🧠 Шаг 2: `main.py` — вход в приложение

```python
# main.py

from ui import launch_app

if __name__ == "__main__":
    launch_app()
```

💡 Здесь мы просто вызываем функцию `launch_app()` из `ui.py`, где будет весь интерфейс.

---

## 🧠 Шаг 3: `ui.py` — всё про интерфейс

```python
# ui.py

import customtkinter as ctk
from analyzer import analyze_url

def launch_app():
    ctk.set_appearance_mode("dark")
    ctk.set_default_color_theme("blue")

    app = ctk.CTk()
    app.title("SEO-анализатор")
    app.geometry("800x600")
    app.resizable(False, False)

    label = ctk.CTkLabel(app, text="Введите URL для анализа", font=("Arial", 18))
    label.pack(pady=(40, 10))

    url_entry = ctk.CTkEntry(app, placeholder_text="https://example.com", width=500)
    url_entry.pack(pady=(0, 20))

    output_box = ctk.CTkTextbox(app, width=700, height=250, corner_radius=10)
    output_box.pack(pady=10)
    output_box.configure(state="disabled")

    def on_analyze():
        url = url_entry.get().strip()
        output_box.configure(state="normal")
        output_box.delete("1.0", "end")

        try:
            data = analyze_url(url)
            output_box.insert("end", f"URL: {url}\n\n")
            output_box.insert("end", f"[TITLE] {data['title']} ({data['title_length']} символов)\n")

        except Exception as e:
            output_box.insert("end", f"Ошибка: {e}")

        output_box.configure(state="disabled")

    analyze_button = ctk.CTkButton(app, text="Анализировать", command=on_analyze, width=200)
    analyze_button.pack(pady=10)

    app.mainloop()
```

---

## 🧠 Шаг 4: `analyzer.py` — обработка HTML и SEO-данных

```python
# analyzer.py

import requests
from bs4 import BeautifulSoup

def analyze_url(url):
    result = {}

    response = requests.get(url, timeout=10)
    response.raise_for_status()

    soup = BeautifulSoup(response.text, "html.parser")

    # TITLE
    if soup.title and soup.title.string:
        title = soup.title.string.strip()
        result["title"] = title
        result["title_length"] = len(title)
    else:
        result["title"] = "Тег <title> не найден"
        result["title_length"] = 0

    return result
```

💡 Пока только `<title>` и его длина. Позже добавим `meta`, `h1`, `links`, `warnings`.

---

## 📦 Шаг 5: `requirements.txt`

```txt
customtkinter
requests
beautifulsoup4
```

---

## ✅ Готово!

Ты теперь:

* Запускаешь `main.py`
* Вводишь URL
* Видишь заголовок и его длину
* А код — **чистый, по папочкам**

---

## ⏭ Дальше?

* Добавим `meta description`
* Добавим `h1`
* Ссылки
* Проверку: длина title ≤ 60 символов

Дай команду — и продолжаем рефакторить и улучшать 🚀

Отлично, Даян! 🧠⚡ Мы на скорости SEO-ракеты. Сейчас добавим **мета-теги** (`description`, `keywords`), **h1-заголовок**, **ссылки** и сделаем **проверки по лимитам Google**. Всё красиво и по модульному!

---

## 🛠 Обновим `analyzer.py`

Добавим новые поля в результат:

```python
# analyzer.py

import requests
from bs4 import BeautifulSoup

def analyze_url(url):
    result = {}

    response = requests.get(url, timeout=10)
    response.raise_for_status()

    soup = BeautifulSoup(response.text, "html.parser")

    # TITLE
    if soup.title and soup.title.string:
        title = soup.title.string.strip()
        result["title"] = title
        result["title_length"] = len(title)
        result["title_warning"] = "Ок" if len(title) <= 60 else "Превышен лимит"
    else:
        result["title"] = "Тег <title> не найден"
        result["title_length"] = 0
        result["title_warning"] = "Ошибка"

    # META DESCRIPTION
    meta_desc_tag = soup.find("meta", attrs={"name": "description"})
    if meta_desc_tag and meta_desc_tag.get("content"):
        desc = meta_desc_tag["content"].strip()
        result["description"] = desc
        result["description_length"] = len(desc)
        result["description_warning"] = "Ок" if len(desc) <= 160 else "Превышен лимит"
    else:
        result["description"] = "Мета description не найден"
        result["description_length"] = 0
        result["description_warning"] = "Ошибка"

    # META KEYWORDS (уже устаревший, но иногда используется)
    meta_keywords = soup.find("meta", attrs={"name": "keywords"})
    result["keywords"] = meta_keywords["content"].strip() if meta_keywords and meta_keywords.get("content") else "Не указаны"

    # H1
    h1_tag = soup.find("h1")
    result["h1"] = h1_tag.get_text(strip=True) if h1_tag else "H1 не найден"

    # LINKS
    all_links = soup.find_all("a", href=True)
    result["link_count"] = len(all_links)
    result["internal_links"] = sum(1 for link in all_links if url in link["href"])
    result["external_links"] = result["link_count"] - result["internal_links"]

    return result
```

---

## 🎨 Обновим `ui.py`, чтобы отобразить всё:

Вот часть функции `on_analyze()` — заменим её:

```python
    def on_analyze():
        url = url_entry.get().strip()
        output_box.configure(state="normal")
        output_box.delete("1.0", "end")

        try:
            data = analyze_url(url)

            output_box.insert("end", f"URL: {url}\n\n")
            output_box.insert("end", f"[TITLE] {data['title']} ({data['title_length']} символов) — {data['title_warning']}\n")
            output_box.insert("end", f"[META Description] {data['description']} ({data['description_length']} символов) — {data['description_warning']}\n")
            output_box.insert("end", f"[META Keywords] {data['keywords']}\n")
            output_box.insert("end", f"[H1] {data['h1']}\n")
            output_box.insert("end", f"[Ссылки] Всего: {data['link_count']}, Внутренние: {data['internal_links']}, Внешние: {data['external_links']}\n")

        except Exception as e:
            output_box.insert("end", f"Ошибка: {e}")

        output_box.configure(state="disabled")
```

---

## 💡 Что дальше?

Следующим шагом можем:

* Выводить цветные метки (ошибка, ок — зелёный/красный)
* Добавить экспорт в TXT или HTML
* Обрабатывать несколько H1
* Поддержка пользовательского user-agent для обхода блокировок

---

Скажи, если хочешь:

* Цветной вывод (ярлыки успех/ошибка)
* Обновить вывод `CTkTextbox` с форматированием
* Или перейти к следующему полю/улучшению

**Дальше будет только круче 💪**
