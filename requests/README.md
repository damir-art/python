#  API / HTTP / requests
API, HTTP-запросы, загрузка данных, работа с сайтами, парсеры, боты.

## 🔹 Что такое API?

**API (Application Programming Interface)** — это способ **общения программ** друг с другом.

Когда ты обращаешься к сайту, например `https://api.weatherapi.com/...`,
ты отправляешь **HTTP-запрос** — и получаешь **JSON-ответ**, который можно обработать в Python.

---

## 🔸 Основной инструмент: `requests`

Устанавливаем:

```bash
pip install requests
```

---

## 🔸 Простой `GET` запрос

```python
import requests

response = requests.get("https://api.github.com")
print(response.status_code)      # 200
print(response.headers["Content-Type"])
print(response.text)             # Текст ответа (обычно JSON)
```

---

## 🔸 Парсим JSON-ответ

```python
data = response.json()
print(data["current_user_url"])  # пример ключа
```

---

## 🔸 Запрос с параметрами (`?key=value`)

```python
params = {"q": "Dota 2", "lang": "ru"}
response = requests.get("https://api.example.com/search", params=params)
```

📎 Адрес будет выглядеть как: `...?q=Dota+2&lang=ru`

---

## 🔸 Заголовки

```python
headers = {
    "Authorization": "Bearer Мой_API_Ключ",
    "User-Agent": "Даян-бот/1.0"
}
requests.get("https://api.example.com/data", headers=headers)
```

---

## 🔸 POST-запрос (например, для авторизации)

```python
data = {"username": "dayan", "password": "1234"}
response = requests.post("https://api.example.com/login", json=data)
print(response.status_code)
```

---

## 🔸 Проверка на успех

```python
if response.status_code == 200:
    print("Успешно!")
else:
    print("Ошибка:", response.status_code)
```

---

## 🔸 Таймауты и исключения

```python
try:
    response = requests.get("https://api.example.com", timeout=5)
except requests.exceptions.Timeout:
    print("Сервер не ответил вовремя 😡")
```

---

## 🔥 Практика: получаем погоду

```python
import requests

url = "https://wttr.in/Moscow?format=j1"
response = requests.get(url)
weather = response.json()

temp = weather['current_condition'][0]['temp_C']
desc = weather['current_condition'][0]['weatherDesc'][0]['value']

print(f"Температура: {temp}°C, {desc}")
```

🎯 Всё — ты только что создал погодный бот!

---

## 🔸 Как найти API?

* [https://rapidapi.com/](https://rapidapi.com/)
* [https://public-apis.io/](https://public-apis.io/)
* [https://github.com/public-apis/public-apis](https://github.com/public-apis/public-apis)

---

**Ошибки и улучшения:**

1. **Нет обработки ошибок при запросе погоды**  
   Если сервер не отвечает или структура ответа изменилась, код упадёт с ошибкой.  
   Рекомендуется добавить обработку исключений и проверку ключей.

2. **Не указана кодировка при выводе текста**  
   Иногда ответ содержит не-UTF8 символы, стоит добавить `encoding="utf-8"` при открытии файла или явно указать в requests.

3. **Нет примера работы с другими HTTP-методами**  
   Можно добавить пример PUT/DELETE-запроса.

4. **Нет пояснения про работу с cookies и сессиями**  
   Для сложных API часто требуется авторизация через сессии.

5. **Нет примера сохранения ответа в файл**  
   Это часто нужно для парсеров.

6. **Нет раздела про обработку ошибок HTTP (например, 404, 500)**  
   Можно добавить пример с `response.raise_for_status()`.

7. **Нет примера с парсингом вложенного JSON или списков**  
   Для сложных API это важно.

**Что добавить:**

```python
# Пример обработки ошибок при запросе погоды
import requests

url = "https://wttr.in/Moscow?format=j1"
try:
    response = requests.get(url, timeout=5)
    response.raise_for_status()  # выбросит исключение при ошибке HTTP
    weather = response.json()
    temp = weather['current_condition'][0]['temp_C']
    desc = weather['current_condition'][0]['weatherDesc'][0]['value']
    print(f"Температура: {temp}°C, {desc}")
except requests.exceptions.RequestException as e:
    print("Ошибка запроса:", e)
except (KeyError, IndexError):
    print("Ошибка структуры ответа!")
```

Пример работы с сессией:
```python
import requests

session = requests.Session()
session.headers.update({"User-Agent": "Даян-бот/1.0"})
response = session.get("https://api.example.com/data")
```

Пример сохранения ответа в файл:
```python
with open("weather.json", "w", encoding="utf-8") as f:
    f.write(response.text)
```

Пример PUT/DELETE:
```python
response = requests.put("https://api.example.com/item/1", json={"name": "new"})
response = requests.delete("https://api.example.com/item/1")
```

Пояснить, что для сложных API часто требуется авторизация, работа с токенами, cookies.

Добавить ссылку на официальную документацию:  
[https://docs.python-requests.org/en/latest/](https://docs.python-requests.org/en/latest/)

---