# Топ 30 модулей

## 🔧 30 самых популярных встроенных модулей Python (из стандартной библиотеки)

Основано на официальных списках модулей и рекомендациях ([Sunscrapers][1], [GeeksforGeeks][2]):

1. **`sys`** — взаимодействие с интерпретатором (аргументы, версия, sys.path).
   *Установка не нужна*
2. **`os`** — работа с файлами, папками, системными функциями.
3. **`math`** — математические функции: sqrt, sin, cos, pi и др.
4. **`datetime`** — работа с датой и временем, временные зоны, timedelta
5. **`json`** — кодирование/декодирование JSON через `.dumps()` / `.loads()`.
6. **`re`** — регулярные выражения.
7. **`collections`** — расширенные контейнеры: `Counter`, `defaultdict`, `deque`
8. **`itertools`** — итераторы: `chain`, `cycle`, `islice`
9. **`functools`** — функции высшего порядка: `partial`, `reduce`, `lru_cache`
10. **`contextlib`** — утилиты для контекстных менеджеров, например `ExitStack`
11. **`argparse`** — парсер командной строки.
12. **`logging`** — гибкий механизм логирования.
13. **`pathlib`** — удобная работа с путями к файлам.
14. **`subprocess`** — запуск внешних процессов.
15. **`threading` / `_thread` (не рекомендуется) ** — работа с потоками.
16. **`multiprocessing`** — параллельная обработка.
17. **`random`** — генерация случайных чисел.
18. **`decimal`** — точная арифметика с дробями (фиксации ошибок float)
19. **`uuid`** — генерация уникальных идентификаторов.
20. **`hashlib`** — хеширование данных (MD5, SHA и пр.).
21. **`gzip`, `bz2`, `zipfile`** — работа с архивами.
22. **`csv`** — парсинг CSV-файлов.
23. **`xml.etree.ElementTree`** — парсинг XML.
24. **`pprint`** — красивый вывод структур данных.
25. **`zlib`** — сжатие и распаковка.
26. **`time`** — работа с временем, таймерами.
27. **`sysconfig`** — конфигурация Python среды.
28. **`warnings`** — выдача предупреждений в коде.
29. **`statistics`** — простые статистики: mean, median, variance.
30. **`pydoc`** — генерация документации и просмотр помощи.

Все эти модули входят в стандартную поставку Python — **ничего устанавливать не нужно**, просто импортируешь.

---

## 🌐 30 популярных сторонних (third‑party) модулей
Основываясь на актуальных рейтингах и статьях 2024–2025 годов 

1. **Requests** — HTTP‑клиент, простой и мощный

   ```bash
   pip install requests
   ```

2. **NumPy** — числовые массивы и математика

   ```bash
   pip install numpy
   ```

3. **Pandas** — табличные данные, DataFrame

   ```bash
   pip install pandas
   ```

4. **Matplotlib** — визуализация: графики, hist, plot

   ```bash
   pip install matplotlib
   ```

5. **Seaborn** — статистическая визуализация, построенное на Matplotlib

   ```bash
   pip install seaborn
   ```

6. **SciPy** — научные вычисления: оптимизация, линалг, FFT и пр.

   ```bash
   pip install scipy
   ```

7. **scikit‑learn** — машинное обучение простыми методами

   ```bash
   pip install scikit-learn
   ```

8. **TensorFlow** — глубокое обучение от Google

   ```bash
   pip install tensorflow
   ```

9. **Keras** — высокоуровневый API поверх TensorFlow

   ```bash
   pip install keras
   ```

10. **PyTorch** — динамичные нейронные сети от Meta AI

    ```bash
    pip install torch
    ```

11. **XGBoost** — градиентный бустинг, часто на соревнованиях ML

    ```bash
    pip install xgboost
    ```

12. **LightGBM** — быстрое обучение бустинговых моделей

    ```bash
    pip install lightgbm
    ```

13. **Statsmodels** — статистическое моделирование и тестирование

    ```bash
    pip install statsmodels
    ```

14. **NLTK** — NLP-библиотека с токенизацией, классификацией

    ```bash
    pip install nltk
    ```

15. **spaCy** — промышленная NLP (быстро и продакшн)

    ```bash
    pip install spacy
    ```

16. **Gensim** — тематическое моделирование, векторные модели слов

    ```bash
    pip install gensim
    ```

17. **Beautiful Soup** — парсинг HTML и XML, скрапинг веб-страниц

    ```bash
    pip install beautifulsoup4
    ```

18. **ipython** — улучшенная консоль для интерактивной разработки

    ```bash
    pip install ipython
    ```

19. **Jinja2** — шаблонизатор (часто с Flask/Django)

    ```bash
    pip install jinja2
    ```

20. **Flask** — лёгкий веб-фреймворк

    ```bash
    pip install flask
    ```

21. **Django** — мощный full-stack фреймворк для веба

    ```bash
    pip install django
    ```

22. **SQLAlchemy** — ORM и работа с БД

    ```bash
    pip install SQLAlchemy
    ```

23. **Twisted** — асинхронная сеть, фреймворк для событий

    ```bash
    pip install twisted
    ```

24. **Pygame** — разработка игр на Python

    ```bash
    pip install pygame
    ```

25. **OpenCV (cv2)** — компьютерное зрение и обработка изображений

    ```bash
    pip install opencv-python
    ```

После установки используйте:

    ```python
    import cv2
    ```
    Модуль называется cv2, хотя пакет для установки — opencv-python.

26. **SymPy** — символьная математика, аналитика

    ```bash
    pip install sympy
    ```

27. **Cython** — ускорение Python‑кода с C, часто используется в SciPy, pandas

    ```bash
    pip install cython
    ```

28. **Loguru** — удобный логгер, заменяет стандартный logging (часто хвалят)

    ```bash
    pip install loguru
    ```

29. **Tqdm** — красивый прогресс‑бар для циклов и итераций

    ```bash
    pip install tqdm
    ```

30. **NetworkX** — работа с графами и сетями

    ```bash
    pip install networkx
    ```

---

## ✅ Как ставить сторонние модули:

Самое просто — через `pip`:

```bash
pip install имя_модуля
```

Можно использовать `python -m pip install ...` вместо просто `pip install ...` для избежания конфликтов версий.

Если используешь виртуальное окружение (рекомендуется):

```bash
# выбери свою ось
python -m venv venv
source venv/bin/activate  # в Linux/Mac
venv\Scripts\activate     # в Windows

pip install имя_модуля
```

Виртуальное окружение — это отдельная папка с собственной копией Python и установленными библиотеками. Оно позволяет изолировать зависимости для каждого проекта, чтобы разные проекты не мешали друг другу и не возникали конфликты версий. Рекомендуется создавать виртуальное окружение для каждого нового проекта, чтобы не засорять глобальную систему Python и работать безопасно.

Можно также использовать:
- `pip install requests==2.28.1` для конкретной версии или `pip install -r requirements.txt`.
- `pip install --upgrade имя_модуля` - для обновления модуля

---

## 🧠 Итог:

* Встроенные модули доступны сразу, без установки — просто `import …`.
* Сторонние устанавливаются через `pip install`.
* Эти модули — инструменты для самых разных сфер: веб, данные, ML, визуализация, игры и т.д.
