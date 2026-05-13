# 💳 Subscriptions — учёт подписок

[![HTML5](https://img.shields.io/badge/HTML5-Structure-E34F26?style=flat&logo=html5&logoColor=white)](https://developer.mozilla.org/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-Styling-1572B6?style=flat&logo=css3&logoColor=white)](https://developer.mozilla.org/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-Logic-F7DF1E?style=flat&logo=javascript&logoColor=black)](https://developer.mozilla.org/docs/Web/JavaScript)
[![Storage](https://img.shields.io/badge/Storage-localStorage%20%2F%20JSON-4285F4?style=flat)](https://developer.mozilla.org/docs/Web/API/Window/localStorage)
[![Electron](https://img.shields.io/badge/Desktop-Electron-47848F?style=flat&logo=electron&logoColor=white)](https://www.electronjs.org/)
[![License](https://img.shields.io/badge/License-Educational%20Use-9cf?style=flat)](#license)

**Subscriptions** — локальное приложение для учёта платных подписок (стриминг, музыка, игры, облако). Есть **две версии**: одностраничный **HTML-файл** (vanilla JS) и **десктоп на Electron**. Данные не уходят в интернет: только браузерный `localStorage` или файл `subscriptions.json` на диске.

---

## 📌 Содержание

- [✨ Ключевые моменты](#highlights)
- [🚀 Возможности](#features)
- [🧠 Как это устроено](#how-it-works)
- [💻 Стек технологий](#tech-stack)
- [📁 Структура проекта](#project-structure)
- [▶️ Запуск](#getting-started)
- [📄 Лицензия](#license)

---

<a id="highlights"></a>

## ✨ Ключевые моменты

- аккуратный **тёмный UI** в духе неоново-зелёного акцента;
- полный **CRUD** по подпискам (создать, читать, обновить, удалить);
- **офлайн**: без API, без сервера, без CDN;
- **10 демо-подписок** (Netflix, YouTube Premium, Spotify и др.) встроены в приложение;
- **нулевая настройка** для HTML-версии — достаточно открыть один файл в браузере;
- для Electron — изоляция контекста и безопасный **preload**-мост к файловой БД.

---

<a id="features"></a>

## 🚀 Возможности

### 📋 Обзор подписок

- отображение всех подписок **карточками** с суммой, периодом и датой следующего списания;
- индикатор **активна / неактивна**;
- сортировка по дате следующего списания;
- блок **«~ ₽ / мес. экв.»** — суммарная нагрузка с пересчётом годовых планов в месячный эквивалент.

### ✏️ Форма и данные

- поля: название, сумма, валюта, период (месяц / год), дата списания, категория, чекбокс активности;
- режим **редактирования** с отменой;
- **HTML-версия:** JSON в `localStorage` (ключ `subscriptions_json_db`);
- **Electron:** JSON-файл в каталоге данных приложения + демо из [`default-subscriptions.json`](default-subscriptions.json).

### 🎯 Дополнительно

- иконки на карточках по **категории** (музыка, видео, игры, облако и т.д.);
- при **пустой или повреждённой** базе автоматически подставляются встроенные демо-записи.

---

<a id="how-it-works"></a>

## 🧠 Как это устроено

1. **Однофайловый режим** — вся разметка, стили и логика в [`subscription-list.html`](subscription-list.html); при загрузке читается `localStorage`, при сохранении — запись JSON-строки.
2. **Electron** — процесс [`main.js`](main.js) читает/пишет файл через `fs`; окно рендера получает данные только через [`preload.js`](preload.js) и `contextBridge` (без прямого доступа к Node в UI).

---

<a id="tech-stack"></a>

## 💻 Стек технологий

| Слой        | Технологии                          |
| ----------- | ----------------------------------- |
| Разметка    | HTML5                               |
| Стили       | CSS3 (переменные, Grid, адаптив)    |
| Логика      | JavaScript (ES5+ совместимый стиль) |
| Хранение    | JSON + `localStorage` или файл    |
| Десктоп     | Electron                            |

---

<a id="project-structure"></a>

## 📁 Структура проекта

```
subscription-list-app/
├── subscription-list.html    # автономная веб-версия (один файл)
├── default-subscriptions.json  # встроенные демо-подписки (10 шт.)
├── package.json
├── main.js                     # главный процесс Electron
├── preload.js                  # IPC: read / write БД
├── index.html                  # оболочка окна Electron
├── README.md
└── src/
    ├── renderer.js             # UI и логика окна Electron
    └── styles.css              # стили десктоп-версии
```

---

<a id="getting-started"></a>

## ▶️ Запуск

### Вариант A — только браузер

Открой файл **`subscription-list.html`** двойным щелчком или через «Открыть с помощью» → браузер.

### Вариант B — Electron

Требуется [Node.js](https://nodejs.org/) (LTS).

```bash
git clone https://github.com/<username>/<repository>.git
cd subscription-list-app
npm install
npm start
```

На Windows файл пользовательской БД обычно лежит в `%AppData%\subscription-list\subscriptions.json`.

### Сброс демо (только HTML)

В консоли браузера (F12):

```js
localStorage.removeItem('subscriptions_json_db');
location.reload();
```

---

<a id="license"></a>

## 📄 Лицензия

Проект предназначен для **учебного использования**. При необходимости добавь в репозиторий свой файл `LICENSE`.
