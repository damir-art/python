# 🔹 Что такое BeautifulSoup?
Если тебе нужно **спарсить только одну страницу сайта** — без заморочек, без авторизации, без API, то тебе подойдёт **лёгкий и удобный модуль: `BeautifulSoup`**. Работает в паре с `requests`, идеально для **HTML-парсинга**.

`BeautifulSoup` — это **библиотека для разбора HTML**.
Ты передаёшь ей страницу — она превращает её в удобное дерево, где можно искать теги, классы, ID, текст и т.д.

---

## 🔸 Установка

```bash
pip install beautifulsoup4
pip install lxml
```

📦 `lxml` — быстрый парсер HTML.

---

## 🔸 Пример: парсим страницу

```python
import requests
from bs4 import BeautifulSoup

url = "https://example.com"
response = requests.get(url)
soup = BeautifulSoup(response.text, "lxml")

print(soup.title.text)  # Выводит заголовок страницы
```

---

## 🔹 Как искать элементы

### 🔸 По тегу:

```python
h1 = soup.find("h1")
print(h1.text)
```

### 🔸 Все теги (например, все ссылки):

```python
links = soup.find_all("a")
for link in links:
    print(link.get("href"))
```

---

### 🔸 По классу:

```python
items = soup.find_all("div", class_="product")
```

📌 В `class_` вместо `class`, потому что `class` — зарезервированное слово в Python.

---

### 🔸 По ID:

```python
block = soup.find(id="main-content")
```

---

### 🔸 CSS-селекторы:

```python
elements = soup.select("div.content > p")
for el in elements:
    print(el.text)
```

---

## 🔥 Пример боевой:

```python
url = "https://quotes.toscrape.com/"

r = requests.get(url)
soup = BeautifulSoup(r.text, "lxml")

quotes = soup.find_all("span", class_="text")

for q in quotes:
    print(q.text)
```

Выведет 10 цитат с главной страницы сайта ✍️

---

## 🛡️ Важно!

* Уважай правила сайта. Проверяй `robots.txt`
* Не бомби 1000 запросов — это неэтично
* Некоторые сайты защищаются от ботов (нужно `headers` или `selenium`)

---
