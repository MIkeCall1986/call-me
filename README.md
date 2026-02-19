# Call-Me

This project enables easy one-to-one video calls directly from your web browser using WebRTC technology.

![callme](./assets/doc/callme.png)

## Getting Started

### Overview

This project allows you to:

- `Sign in` with a username.
- `Set your preferred language`.
- `Initiate video calls` by clicking the call button next to a recipient’s username.
- `Switch between cameras, microphones, and speakers` during a call.
- `Chat in real time` with participants.
- `Hide your video` feed when needed.
- `Toggle your microphone` (mute/unmute).
- `Toggle your camera` (video on/off).
- `Share your screen` (start/stop).
- `Share files` with other participants.
- `Hang up the call` when finished.
- `Enable Host Protection` mode with a password.
- `Use the REST API` to retrieve the list of connected users or initiate a call.
- `End-to-End Encryption` for secure and private communications.

---

### Quick Start

- #### Using NodeJs

![nodejs](public/assets/nodejs.png)

**[Install Node.js and npm](https://nodejs.org/en/download)**

```shell
# Clone this repo
git clone https://github.com/miroslavpejic85/call-me.git

# Go to to dir call-me
cd call-me

# Copy the config file
$ cp public/config.template.js public/config.js

# Copy .env.template to .env
cp .env.template .env

# Install dependencies
npm install

# Start the application
npm start
```

---

- #### Using Docker

![docker](public/assets/docker.png)

Install [docker engine](https://docs.docker.com/engine/install/) and [docker compose](https://docs.docker.com/compose/install/)

```shell
# Clone this repo
git clone https://github.com/miroslavpejic85/call-me.git

# Go to to dir call-me
cd call-me

# Copy .env.template to .env
cp .env.template .env

# Create your own docker-compose.yml
cp docker-compose.template.yml docker-compose.yml

# Get official image from Docker Hub
docker-compose pull

# Create and start containers
docker-compose up
```

---

1. `Open` your browser and visit [http://localhost:8000](http://localhost:8000).

2. `Sign in` with your username.

3. `Select` the connected recipient's username and click `Call`.

4. `Enjoy` your one-to-one video call.

---

## Click to Call

Allows a user to `join` the room as a `user1`

- [http://localhost:8000/join?user=user1](http://localhost:8000/join?user=user1) (dev)
- [https://cme.mirotalk.com/join?user=user1](https://cme.mirotalk.com/join?user=user1) (prod)

Lets the `user2 join` the room and initiate a `call` to the `user1`

- [http://localhost:8000/join?user=user2&call=user1](http://localhost:8000/join?user=user2&call=user1) (dev)
- [https://cme.mirotalk.com/join?user=user2&call=user1](https://cme.mirotalk.com/join?user=user2&call=user1) (prod)

You can explore a `widget` example that demonstrates this functionality [here](./integration/widget.html).

---

## Fast Integration

![iframe](public/assets/iframe.png)

Easily integrate `Call-Me` into your website or application with a [simple iframe](https://codepen.io/Miroslav-Pejic/pen/qEWBaKP). Just add the following code to your project:

```html
<iframe
    allow="camera; microphone; speaker-selection; fullscreen; clipboard-read; clipboard-write; web-share; autoplay"
    src="https://cme.mirotalk.com/"
    style="width: 100vw; height: 100vh; border: 0px;"
></iframe>
```

---

## API

Get all connected users

```shell
# Get all connected users
curl -X GET "http://localhost:8000/api/v1/users" -H "authorization: call_me_api_key_secret" -H "Content-Type: application/json"
curl -X GET "https://cme.mirotalk.com/api/v1/users" -H "authorization: call_me_api_key_secret" -H "Content-Type: application/json"

# Generate call links for connected users to call
curl -X GET "http://localhost:8000/api/v1/connected?user=call-me" -H "authorization: call_me_api_key_secret" -H "Content-Type: application/json"
curl -X GET "https://cme.mirotalk.com/api/v1/connected?user=call-me" -H "authorization: call_me_api_key_secret" -H "Content-Type: application/json"
```

Docs: http://localhost:8000/api/v1/docs/ or you can check it out live in prod [here](https://cme.mirotalk.com/api/v1/docs/).

---

## Self-Hosting

To install this on your VPS, VDS, or personal server, please follow the instructions in **[the self-hosting documentation](./doc/self-hosting.md)**.

---

![Star History Chart](https://app.repohistory.com/api/svg?repo=miroslavpejic85/call-me&type=Date&background=0D1117&color=62C3F8)

19.02.26
Ось результати аналізу та стратегія трансформації для проекту **Call-Me**, підготовлені у форматі для копіювання в Notion.

---

# 📑 Звіт AI-консультанта: Проект "Call-Me"

**Call-Me** — це рішення для миттєвих відеодзвінків форматі "один-на-один", що працює безпосередньо у браузері на базі технології WebRTC.

## 🧬 Частина 1: "ДНК" Проекту

Логіку коду проекту можна розбити на такі **атомарні функції**:

*   **Авторизація та ідентифікація:** Простий вхід у систему за допомогою імені користувача (username).
*   **Сигналінг та ініціація дзвінка:** Встановлення зв'язку між двома точками шляхом введення імені отримувача або через спеціальні URL-параметри для приєднання до кімнати (`/join?user=...&call=...`).
*   **Управління медіа-потоками:** Передача аудіо та відео через WebRTC, а також функції ввімкнення/вимкнення відеокамери.
*   **Управління сесією:** Можливість завершення дзвінка ("Hang up") та очищення ресурсів.
*   **API-взаємодія:** REST API для отримання списку всіх підключених користувачів та генерації посилань для дзвінків.
*   **Інтеграція (Embedding):** Функціонал для швидкого вбудовування сервісу на сторонні сайти за допомогою `iframe`.

### 💎 Головна технічна цінність
Головна цінність проекту полягає в **ультра-низькому порозі входу для розробника та користувача**. Він надає легку інфраструктуру для відеозв'язку, яку можна розгорнути за хвилини через Node.js або Docker і інтегрувати в будь-який веб-проект одним рядком коду без необхідності складних налаштувань серверів.

---

## 🚀 Частина 2: "Трансформація" (Інтеграція з Gemini LLM)

Додавання мультимодальної моделі **Gemini** (через **GitHub Models**) перетворює "Call-Me" з простого інструменту зв'язку на **інтелектуального відео-асистента**.

### Як зміниться функціонал?
1.  **Синхронний переклад та субтитри:** Gemini може в реальному часі транскрибувати мовлення обох учасників і надавати переклад безпосередньо у вікні дзвінка.
2.  **AI-Протоколювання (Summary):** Після завершення дзвінка модель автоматично створює резюме розмови, виділяючи ключові тези та завдання.
3.  **Контекстні підказки:** Під час дзвінка ШІ може аналізувати аудіопотік і підказувати оператору відповіді на складні запитання або посилатися на документацію.

### Сценарій сервісу "Smart Support Agent" (Call-Me + Gemini + ID_{$})

Створення сервісу інтелектуальної підтримки на вашому сайті:
1.  **Черга запитів (ID_{$}):** Коли клієнт хоче зателефонувати, ваш Python-скрипт **ID_{$}** перевіряє через API проекту (`/api/v1/users`), хто з операторів вільний.
2.  **З'єднання:** Скрипт автоматично генерує лінк для дзвінка та відкриває його у клієнта через iframe.
3.  **Асистування (Gemini):** Gemini "слухає" розмову. Якщо клієнт запитує технічні деталі, Gemini через GitHub Models аналізує запит і виводить підказку оператору.
4.  **Аналіз даних (ID_{$}):** Після дзвінка інший ваш скрипт **ID_{$}** отримує від Gemini готове резюме розмови та автоматично зберігає його у вашу базу даних клієнтів.
5.  **Деплой:** Використовуючи **GitHub Spark**, ви розгортаєте цей інтелектуальний інтерфейс як готовий додаток.

---

## 📋 План дій для Notion
| Крок | Дія | Результат |
| :--- | :--- | :--- |
| **1** | Розгортання: `docker-compose up` | Робочий сервер відеозв'язку |
| **2** | Підключення Gemini через **GitHub Models** | Додавання ШІ-інтелекту до системи |
| **3** | Інтеграція ваших скриптів `ID_{$}` через REST API | Автоматизація викликів та обробки даних |
| **4** | Використання **GitHub Spark** для інтерфейсу | Готовий інтелектуальний сервіс на сайті |

---

### 💡 Резюме

**Суть:** **Миттєві відеодзвінки в браузері через WebRTC**.

**AI-Роль:** **Створення інтелектуальних застосунків через Spark**.
