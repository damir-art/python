# JSON в Python

**JSON** — это как универсальный язык обмена данными между программами, сайтами, API, скриптами и вообще всем, что может быть умным.

---

## 🧠 Что такое JSON?

**JSON** (JavaScript Object Notation) — это текстовый формат, похожий на словари Python:

```json
{
  "name": "Даян",
  "age": 30,
  "is_active": true
}
```

Это просто **строка**, но в понятной структуре.

---

## 🔹 Модуль `json` в Python

Он умеет:

* Преобразовывать Python-объекты → в JSON-строку (`dump`, `dumps`)
* Читать JSON-строку → в Python (`load`, `loads`)

---

## 🔸 `json.dumps()` — объект в строку

```python
import json

data = {"name": "Даян", "age": 30, "is_active": True}

json_str = json.dumps(data)
print(json_str)
# {"name": "Даян", "age": 30, "is_active": true}
```

📌 `dumps = dump string`

---

## 🔸 `json.loads()` — строка в объект

```python
json_str = '{"name": "Даян", "age": 30, "is_active": true}'

data = json.loads(json_str)
print(data["name"])  # Даян
```

📌 `loads = load string`

---

## 🔸 Работа с файлами

### Сохранить в файл (`dump`):

```python
data = {"name": "Даян", "lang": "Python"}

with open("data.json", "w", encoding="utf-8") as f:
    json.dump(data, f, ensure_ascii=False, indent=2)
```

### Прочитать из файла (`load`):

```python
with open("data.json", "r", encoding="utf-8") as f:
    loaded = json.load(f)
    print(loaded)
```

---

## 🔸 Красивый вывод (pretty print)

```python
print(json.dumps(data, indent=4, ensure_ascii=False))
```

* `indent=4` — отступы для читаемости
* `ensure_ascii=False` — сохраняем кириллицу нормально

---

## 🔸 Что можно конвертировать в JSON?

| Python          | JSON       |
| --------------- | ---------- |
| `dict`          | объект     |
| `list`, `tuple` | массив     |
| `str`           | строка     |
| `int`, `float`  | число      |
| `True`, `False` | true/false |
| `None`          | null       |

---

## 🔸 Ошибки при работе с JSON

Если попытаешься сериализовать что-то неподдерживаемое:

```python
import datetime
json.dumps({"now": datetime.datetime.now()})
```

❌ Выдаст ошибку:

```
TypeError: Object of type datetime is not JSON serializable
```

📌 Нужно преобразовать вручную или использовать `default=str`.

---

## 🔥 Пример из жизни: работа с API

```python
import requests

response = requests.get("https://jsonplaceholder.typicode.com/posts/1")
data = response.json()  # сразу парсит JSON!
print(data["title"])
```

1. Добавить пример использования `default=str` для сериализации нестандартных объектов.
2. Уточнить, что `json` не поддерживает сериализацию всех типов (например, set, bytes).
3. Добавить раздел про обработку ошибок при чтении/записи JSON (`try/except`).
4. Кратко пояснить разницу между `dump`/`dumps` и `load`/`loads`.
5. Добавить пример сериализации списка и вложенных структур.

Пример дополнения:

````python
# Пример с default=str
import datetime, json
data = {"now": datetime.datetime.now()}
json_str = json.dumps(data, default=str)
print(json_str)  # {"now": "2024-06-07 12:34:56.789123"}

# Обработка ошибок
try:
    with open("broken.json") as f:
        data = json.load(f)
except json.JSONDecodeError:
    print("Ошибка: некорректный JSON!")
````
