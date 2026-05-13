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
- **HTML-версия:** JSON в `localStorage` (
