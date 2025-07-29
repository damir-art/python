**DotaBuff**, **OpenDota**, **Steam Web API** — все они отдают данные через **API в формате JSON**.

А значит — ты можешь **спокойно подключиться к ним из Python**, получить данные и обработать с помощью `requests` + `json`.

---

## 🔥 Как это работает?

1. Ты делаешь **HTTP-запрос** на нужный API (через `requests`)
2. Получаешь **ответ в JSON**
3. Преобразуешь JSON → в Python-объект
4. Достаёшь, что хочешь: героев, матчи, MMR, винрейты, KDA и т.д.

---

## 🔸 Пример с OpenDota

```python
import requests

player_id = 70388657  # например, твой Steam ID

response = requests.get(f"https://api.opendota.com/api/players/{player_id}")
data = response.json()

print(f"Игрок: {data['profile']['personaname']}")
print(f"MMR estimate: {data['mmr_estimate']['estimate']}")
```

🎮 Этот код достанет имя и примерный рейтинг игрока.

---

## 🔸 Пример — последние матчи игрока

```python
response = requests.get(f"https://api.opendota.com/api/players/{player_id}/recentMatches")
matches = response.json()

for match in matches[:5]:  # последние 5 матчей
    print(f"Match ID: {match['match_id']}, Герой: {match['hero_id']}, Победа: {match['radiant_win']}")
```

---

## 📦 Что нужно?

* Установить `requests`:

```bash
pip install requests
```

* Понимать базовую структуру JSON-ответа (документация OpenDota: [https://docs.opendota.com/](https://docs.opendota.com/))

---

## ❗ Важно знать:

* **Steam Web API** требует ключ (`API key`) от тебя
* **OpenDota** можно использовать без ключа (публичное API), но есть лимиты
* Ответы бывают большими — обрабатывай аккуратно (можно сохранять в файл, фильтровать, использовать `pandas`)

---

## 🧠 Хочешь, сделаю тебе мини-программу на Python, которая:

* Подключается к OpenDota
* Получает твои 5 последних матчей
* Показывает героя, KDA, победу/поражение?

Или вообще сделаем **свой дота-аналитик** с красивым интерфейсом на базе твоего SEO-анализатора? 😏
