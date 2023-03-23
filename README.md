# api_final_yatube

### Описание:
Финальный проект спринта.
Соц. сеть где можно комментировать и делать записи, подписываться на авторов.


### Технологии:

Python 3.9, Django 2.2, DRF

### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:
```
git clone https://github.com/nikitaloshch/api_final_yatube.git
```
```
cd api_final_yatube
```
Cоздай и активируй виртуальное окружение:
```
python3 -m venv venv
```

* Если у вас Linux/macOS

    ```source venv/bin/activate```

* Если у вас windows
    ```
    source venv/scripts/activate
    ```

Установить зависимости из файла requirements.txt:

```
pip install -r requirements.txt
```

Выполнить миграции:

```
python3 manage.py migrate
```

Запустить проект:
```
python3 manage.py runserver
```

# Авторизация

Cоздать суперюзера:
```
python manage.py createsuperuser
```
- Получить JWT токен можно по: 
```
POST запрос - /api/v1/jwt/create/
```
- Запрос:
```
{
  "username": "Ваш ник",
  "password": "пароль"
}
```
- В ответе будет получен токен
```
{
  "refresh":  "...",
  "access":  "..."
}
```
####  Токен под ключом access нужно буде закинуть во вкладку HEADERS
#### В столбике Key выбрать вариант   Authorization
#### Во втором столбике написать Bearer и ваш токен
| Authorization | Bearer {ваш токен}|
|--|--|

# Примеры 
### Неавторизованным пользователям можно просматривать контент
```
GET запрос - /api/v1/posts/ - получить все посты.
```
- Ответ:


```
[
  {
    "id":1,
    "author":"...",
    "text":"...",
    "pub_date":"...",
    "image":null,
    "group":null
  },
  {
    "id":2,
    "author":"...",
    "text":"...",
    "pub_date":"...",
    "image":null,
    "group":null
  }
,]
```
```
GET запрос - /api/v1/posts/{id}/ - получить определенный пост.
```

- Ответ:
```
{
    "id":1,
    "author":"...",
    "text":"...",
    "pub_date":"...",
    "image":null,
    "group":null
},
```
```
GET запрос - /api/v1/groups/ - получить все группы.
```
- Ответ:
```
[
  {
    "id": 1,
    "title": "...",
    "slug": "...",
    "description": "..."
  },
  {
    "id": 2,
    "title": "...",
    "slug": "...",
    "description": "..."
  },
]
```

```
GET запрос - /api/v1/groups/{group_id}/ - получить определенную группу.
```
- Ответ:
```
{
    "id": 1,
    "title": "...",
    "slug": "...",
    "description": "..."
},
```
```
GET запрос - /api/v1/posts/{post_id}/comments/ - получить все комментарии под определнным постом.
```
- Ответ:
```
[
  {
    "id": 1,
    "author": "...",
    "text": "...",
    "created": "...",
    "post": 0
  },
  {
    "id": 2,
    "author": "...",
    "text": "...",
    "created": "...",
    "post": 0
  }
]
```
```
GET запрос - /api/v1/posts/{post_id}/comments/{comment_id}/ - получить опрнделенный комментарий под определенным постом
```
- Ответ:
```
{
    "id": 2,
    "author": "...",
    "text": "...",
    "created": "...",
    "post": 0
}
```

### Авторизованным пользователям можно делать посты, изменять их и т.д.

```
POST запрос - /api/v1/posts/ - сделать пост.
```
- Запрос:
```
{
  "text": "string",
  "image": "string",
  "group": null
}
```
```
POST запрос - /api/v1/posts/{post_id}/comments/ - сделать комментарий под определённым постом.
```
- Запрос:
```
{
  "text": "string"
}
```
```
DEL запрос - /api/v1/posts/{post_id}/comments/{comment_id}/ - Удалить определенный комментарий.
```
