# 🔹 Что такое исключение?

**Исключение** — это **ошибка во время выполнения программы**, которая может остановить её.

Примеры:

```python
x = 1 / 0             # ZeroDivisionError
int("abc")           # ValueError
open("нет_такого.txt")  # FileNotFoundError
```

Если не обработать — программа **упадёт** с ошибкой. А если обработать — всё будет культурно и безопасно 😎

---

## 🔸 Синтаксис try-except

```python
try:
    # код, который может вызвать ошибку
    x = int("abc")
except ValueError:
    print("Ошибка: нельзя преобразовать в число!")
```

---

## 🔸 Можно ловить несколько исключений

```python
try:
    x = 1 / 0
except ZeroDivisionError:
    print("Деление на ноль недопустимо!")
except ValueError:
    print("Ошибка значения!")
```

---

## 🔸 Обработка нескольких типов сразу

```python
try:
    some_function()
except (ValueError, TypeError):
    print("Ошибка значения или типа")
```

---

## 🔸 Блок `else`

Если в `try` не было ошибки — выполняется `else`.

```python
try:
    x = int("123")
except ValueError:
    print("Ошибка!")
else:
    print("Всё прошло отлично:", x)
```

---

## 🔸 Блок `finally`

Выполняется **всегда** — была ошибка или нет. Обычно используется для закрытия ресурсов.

```python
try:
    f = open("data.txt", "r")
    content = f.read()
except FileNotFoundError:
    print("Файл не найден")
finally:
    f.close()
    print("Файл закрыт")
```

---

## 🔸 Ловим любую ошибку (нежелательно, но можно)

```python
try:
    do_something()
except Exception as e:
    print("Произошла ошибка:", e)
```

🔍 `Exception` — базовый класс всех исключений

---

## 🔸 Генерация своих ошибок

```python
age = -1
if age < 0:
    raise ValueError("Возраст не может быть отрицательным!")
```

📌 `raise` — возбуждает исключение вручную

---

## 🔥 Резюме

| Команда   | Что делает                       |
| --------- | -------------------------------- |
| `try`     | Пробует выполнить код            |
| `except`  | Обрабатывает конкретную ошибку   |
| `else`    | Выполняется, если ошибок не было |
| `finally` | Выполняется всегда               |
| `raise`   | Создаёт собственную ошибку       |

---

Что добавить?

Вот что можно улучшить и добавить в вашем README:

### Ошибки и улучшения

1. **Закрытие файла в finally**  
   В примере с `finally`:
   ```python
   try:
       f = open("data.txt", "r")
       content = f.read()
   except FileNotFoundError:
       print("Файл не найден")
   finally:
       f.close()
       print("Файл закрыт")
   ```
   Если файл не найден, переменная `f` не будет создана, и вызов `f.close()` вызовет ошибку.

   **Рекомендуемое исправление:**
   ```python
   try:
       f = open("data.txt", "r")
       content = f.read()
   except FileNotFoundError:
       print("Файл не найден")
       f = None
   finally:
       if f:
           f.close()
           print("Файл закрыт")
   ```

   Или использовать менеджер контекста:
   ```python
   try:
       with open("data.txt", "r") as f:
           content = f.read()
   except FileNotFoundError:
       print("Файл не найден")
   ```

2. **Ловля всех ошибок**  
   В разделе "Ловим любую ошибку" стоит добавить предупреждение, что это может скрыть реальные баги и затруднить отладку.

3. **Генерация своих ошибок**  
   Можно добавить пример с созданием собственного класса исключения.

### Что добавить

- **Менеджер контекста (`with`)**  
  Пример безопасного открытия файла:

  ```python
  try:
      with open("data.txt", "r") as f:
          content = f.read()
  except FileNotFoundError:
      print("Файл не найден")
  ```

- **Создание собственного исключения** 
  ```python
  class MyError(Exception):
      pass

  raise MyError("Моё собственное исключение!")
  ```

- **Совет по стилю**  
  Не используйте голый `except:` — всегда указывайте тип ошибки.

---

Если хотите, могу внести эти изменения прямо в файл!

   ```python
   try:
       f = open("data.txt", "r")
       content = f.read()
   except FileNotFoundError:
       print("Файл не найден")
       f = None
   finally:
       if f:
           f.close()
           print("Файл закрыт")
   ```
   Или использовать менеджер контекста:
   ```python
   try:
       with open("data.txt", "r") as f:
           content = f.read()
   except FileNotFoundError:
       print("Файл не найден")
   ```

2. **Ловля всех ошибок**  
   В разделе "Ловим любую ошибку" стоит добавить предупреждение, что это может скрыть реальные баги и затруднить отладку.

3. **Генерация своих ошибок**  
   Можно добавить пример с созданием собственного класса исключения.

### Что добавить

- **Менеджер контекста (`with`)**  
  Пример безопасного открытия файла:
  ```python
  try:
      with open("data.txt", "r") as f:
          content = f.read()
  except FileNotFoundError:
      print("Файл не найден")
  ```

- **Создание собственного исключения**  
  ```python
  class MyError(Exception):
      pass

  raise MyError("Моё собственное исключение!")
  ```

- **Совет по стилю**  
  Не используйте голый `except:` — всегда указывайте тип ошибки.

---
