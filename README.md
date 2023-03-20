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