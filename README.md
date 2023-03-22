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

# Примеры запросов

Cоздать суперюзера:
```
python manage.py createsuperuser
```
### Неавторизованным пользователям можно просматривать контент
```
GET запрос - /api/v1/posts/ - получить все посты.
GET запрос - /api/v1/posts/{id}/ - получить определенный пост.
```
- Ответ будет примерно таким:
```
[{"id":1,
"author":"...",
"text":"...",
"pub_date":"...",
"image":null
,"group":null
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
GET запрос - /api/v1/groups/ - получить все группы.
GET запрос - /api/v1/groups/{group_id}/ - получить определенную группу.

GET запрос - /api/v1/posts/{post_id}/comments/ - получить все комментарии под определнным постом.
GET запрос - /api/v1/posts/{post_id}/comments/{comment_id}/ - получить опрнделенный комментарий под определенным постом)
```
- Ответ на запрос комментария будет примерно таким:
```
{
"id": ...,
"author":"...",
"text":"...",
"created":"...",
"post": ...
}
```
### Авторизованным пользователям можно делать посты, изменять их и т.д.

```
POST запрос - /api/v1/posts/ - сделать пост.

POST запрос - /api/v1/posts/{post_id}/comments/ - сделать комментарий под определённым постом.

PUT, PATCH, DELETE запрос - /api/v1/posts/{post_id}/comments/{comment_id}/ - редактировать или удалить комментарий определенного поста.
```
- Получить JWT токен можно по: 
```
POST запрос - /api/v1/jwt/create/
```
- Нужно в body передать ваш ник и пароль при создании суперюзера
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
#### Во втором столбике написать Bearer и ваш токен :
| Authorization | Bearer {ваш токен}|
|--|--|