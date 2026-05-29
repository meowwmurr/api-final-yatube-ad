# API для Yatube

## Описание проекта

Это учебный API для проекта Yatube на Django REST Framework.
Через API можно:
- получать, создавать, редактировать и удалять посты;
- работать с комментариями к постам;
- получать список групп;
- подписываться на авторов;
- получать JWT-токены для авторизации.

Документация доступна после запуска по адресу:
`http://127.0.0.1:8000/redoc/`

## Как установить и запустить проект

1. Клонировать репозиторий:
```bash
git clone <url_репозитория>
cd api-final-yatube-ad
```

2. Создать и активировать виртуальное окружение:
```bash
python -m venv venv
# Windows
venv\Scripts\activate
# Linux/macOS
source venv/bin/activate
```

3. Установить зависимости:
```bash
pip install -r requirements.txt
```

## Как выполнить миграции

Из директории `yatube_api` выполнить:
```bash
python manage.py makemigrations
python manage.py migrate
```

## Как запустить сервер

Из директории `yatube_api`:
```bash
python manage.py runserver
```

Сервер будет доступен по адресу:
`http://127.0.0.1:8000/`

## Примеры запросов к API

### Получить список постов
```http
GET /api/v1/posts/
```

### Получить пост по id
```http
GET /api/v1/posts/1/
```

### Создать пост (требуется JWT)
```http
POST /api/v1/posts/
Authorization: Bearer <access_token>
Content-Type: application/json

{
  "text": "Новый пост",
  "group": 1
}
```

### Получить комментарии поста
```http
GET /api/v1/posts/1/comments/
```

### Подписаться на пользователя
```http
POST /api/v1/follow/
Authorization: Bearer <access_token>
Content-Type: application/json

{
  "following": "username"
}
```

### Получить JWT токен
```http
POST /api/v1/jwt/create/
Content-Type: application/json

{
  "username": "TestUser",
  "password": "1234567"
}
```
