# Работа с git
Теперь давай быстренько проверим, что всё установилось как надо.

---

## ✅ Шаг 1: Проверка через `Git Bash`

1. Открой меню Пуск → введи **Git Bash** → запусти его.
2. Введи команду:

```bash
git --version
```

👉 Ожидаем увидеть что-то вроде:

```
git version 2.50.1.windows.1
```

Если так — всё работает! 💪

---

## ✅ Шаг 2: Проверка в VS Code (по желанию)

Если ты работаешь в VS Code:

1. Открой любую папку, например `D:\python_lab\parser`
2. Открой терминал внизу (Ctrl + \`)
3. Убедись, что терминал — это **Git Bash** (а не PowerShell)
   * Если не так — скажу, как поменять
4. Введи ту же команду:

```bash
git --version
```

Настраиваем в VS Code **Git Bash** по умолчанию:
- Ctrl + Shift + P (F1)
- Terminal: Select Default Profile
- Выбери: Git Bash

---

## ✅ Шаг 3: Проверим имя и email для Git

В Git обязательно нужно настроить своё имя и email — они будут отображаться в каждом твоём коммите.

Введи в терминале:

```bash
git config --global user.name "Dayan"
git config --global user.email "you@example.com"
```

(вместо `you@example.com` введи свою реальную почту от GitHub)

Потом проверим:

```bash
git config --global --list
```
