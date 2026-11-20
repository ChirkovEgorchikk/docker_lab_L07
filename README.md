# Л07: Docker basics

## Цель
Изучить основы работы с Docker: запуск готовых контейнеров, создание собственного `Dockerfile`, сборка образа и проброс портов.

## Файлы проекта
- `Dockerfile` — инструкция для сборки кастомного образа на базе Nginx.
- `index.html` — статическая страница, которая копируется внутрь контейнера.

## Ход выполнения

### 1. Запуск тестового контейнера
Выполнена команда `docker run hello-world` для проверки работоспособности Docker Engine.
<img width="887" height="642" alt="Снимок экрана 2026-11-20 153311" src="https://github.com/user-attachments/assets/74830fc3-ef24-4c71-954b-3a94fd3886c5" />


### 2. Сборка и запуск кастомного образа
Создан `Dockerfile`, который берет за основу легковесный образ `nginx:alpine` и копирует туда локальный `index.html`.
Выполнена сборка образа:
```bash
sudo docker build -t my-web-app .
```
Запущен контейнер с пробросом порта (хост 8080 -> контейнер 80):
```bash
sudo docker run -d -p 8080:80 --name my-web-container my-web-app
```
<img width="871" height="983" alt="Снимок экрана 2026-11-20 153815" src="https://github.com/user-attachments/assets/2e82fb86-a083-4d1c-b43c-610f4ea1e44b" />

### 3. Проверка работы
Выполнен запрос curl http://localhost:8080. Контейнер успешно отдает кастомную страницу.
Список запущенных контейнеров (docker ps):
<img width="890" height="202" alt="Снимок экрана 2026-11-20 153824" src="https://github.com/user-attachments/assets/7917503a-213e-4905-b0b7-69a4c89e70b4" />

## Итог
Отработаны базовые команды Docker: run, build, ps. Изучен принцип написания Dockerfile и маппинга портов.
