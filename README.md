# 📝 Todo App — Full-stack приложение в Docker

![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=for-the-badge&logo=vite&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)

Учебный проект, в котором я разбирал контейнеризацию full-stack приложения:
React-фронтенд, Node.js-бэкенд, база данных MySQL, Docker Compose и CI на GitHub Actions.

> Проект основан на официальном примере
> [docker/getting-started-todo-app](https://github.com/docker/getting-started-todo-app).

---

## 🏗 Архитектура

![Архитектура приложения](https://github.com/docker/getting-started-todo-app/assets/313480/c128b8e4-366f-4b6f-ad73-08e6652b7c4d)

| Компонент | Технология | Назначение |
|-----------|------------|------------|
| Frontend  | React + Vite | Интерфейс списка задач |
| Backend   | Node.js + nodemon | REST API и раздача статики |
| Database  | MySQL | Хранение задач |
| DB UI     | phpMyAdmin | Просмотр базы в режиме разработки |
| Proxy     | Traefik | Маршрутизация `localhost` / `db.localhost` |

**В продакшене** фронтенд собирается в статические HTML/CSS/JS и раздаётся бэкендом —
получается один контейнер, без server-side rendering.

**В разработке** фронтенд и бэкенд работают как отдельные сервисы: Vite обеспечивает
горячую перезагрузку React, а nodemon перезапускает сервер при изменении кода.

---

## 🚀 Быстрый старт

Нужен только [Docker Desktop](https://www.docker.com/products/docker-desktop/) — ставить Node.js или MySQL не требуется.

```bash
git clone https://github.com/<your-username>/<repo-name>
cd <repo-name>
docker compose up --watch
```

После запуска:

- 🌐 Приложение — [http://localhost](http://localhost)
- 🗄 phpMyAdmin — [http://db.localhost](http://db.localhost)

Изменения во фронтенде и бэкенде подхватываются сразу, без пересборки контейнеров.

Остановить и удалить контейнеры:

```bash
docker compose down
```

---

## 📚 Что разобрано в проекте

- Разделение dev- и prod-окружений через multi-stage Dockerfile
- Оркестрация нескольких сервисов в Docker Compose
- Hot reload внутри контейнеров с помощью `docker compose watch`
- Связка React-фронтенда с Node.js API
- Работа с MySQL в контейнере
- Запуск тестов и сборки в CI (GitHub Actions)