# Работа с файлами
**Работа с файлами** в Python — открыть, читать, записать, перезаписать, удалить. Это важная и очень прикладная часть: почти любое приложение рано или поздно будет читать или писать файл.

---

## 🔹 Как открыть файл

Используем встроенную функцию `open()`:

```python
file = open("example.txt", "r")  # r — режим чтения
```

### 🔸 Режимы открытия:

| Режим | Описание                                |
| ----- | --------------------------------------- |
| `"r"` | Чтение (ошибка, если файла нет)         |
| `"w"` | Запись (создаёт новый, стирает старый!) |
| `"a"` | Добавление в конец                      |
| `"x"` | Создание (ошибка, если уже есть)        |
| `"b"` | Двоичный режим (`rb`, `wb`)             |

---

## 🔸 Чтение файла

```python
with open("data.txt", "r") as f:
    content = f.read()
    print(content)
```

📌 `with` — контекстный менеджер: сам закроет файл после использования (очень важно!).

Можно читать построчно:

```python
with open("data.txt", "r") as f:
    for line in f:
        print(line.strip())
```

---

## 🔸 Запись в файл

```python
with open("output.txt", "w") as f:
    f.write("Привет, Даян!\n")
    f.write("Второй заход.\n")
```

Если файл уже был — **сотрётся**.

---

## 🔸 Добавление в файл

```python
with open("output.txt", "a") as f:
    f.write("И ещё строка...\n")
```

---

## 🔸 Чтение как список строк

```python
with open("data.txt") as f:
    lines = f.readlines()
    print(lines)
```

---

## 🔸 Запись из списка

```python
lines = ["строка 1\n", "строка 2\n"]

with open("output.txt", "w") as f:
    f.writelines(lines)
```

---

## 🔸 Проверка существования файла

```python
import os

if os.path.exists("myfile.txt"):
    print("Файл есть!")
else:
    print("Файла нет :(")
```

---

## 🔸 Удаление файла

```python
import os
os.remove("myfile.txt")
```

---

## 🔸 Пример: копирование файла

```python
with open("source.txt", "r") as src, open("copy.txt", "w") as dst:
    for line in src:
        dst.write(line)
```

---

## 🔸 Двоичные файлы (например, изображения)

```python
with open("photo.jpg", "rb") as f:
    content = f.read()

with open("copy.jpg", "wb") as f:
    f.write(content)
```

---

## 🔥 Бонус: работа с путями

```python
from pathlib import Path

path = Path("data.txt")
if path.exists():
    print("Файл найден!")
```

---

1. **Рекомендуется всегда использовать `with open(...)`** для открытия файлов, чтобы избежать утечек ресурсов.
2. **Добавить обработку ошибок** при работе с файлами через `try/except`.
3. **Пояснить кодировку**: для текстовых файлов часто стоит явно указывать `encoding="utf-8"`.
4. **Добавить пример чтения/записи JSON** — часто используется.
5. **Пояснить разницу между текстовым и двоичным режимом**.
6. **Добавить пример получения размера файла**.
7. **Добавить предупреждение о перезаписи файла в режиме `"w"`**.

Пример дополнения:

```python
# ...existing code...

# Пример обработки ошибок и явной кодировки
try:
    with open("data.txt", "r", encoding="utf-8") as f:
        print(f.read())
except FileNotFoundError:
    print("Файл не найден!")

# Пример работы с JSON
import json
data = {"name": "Даян", "age": 30}
with open("user.json", "w", encoding="utf-8") as f:
    json.dump(data, f, ensure_ascii=False, indent=2)

# Получение размера файла
import os
size = os.path.getsize("data.txt")
print(f"Размер файла: {size} байт")
```

Рекомендую добавить эти примеры и пояснения для полноты.
