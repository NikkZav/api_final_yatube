# api_final

## **Описание:**
#### Бэкенд для REST-API приложения.
В приложении имеются посты, под которыми другие пользователи могут оставлять, а также удалять или редактировать (но только свои) комментарии.
Аналогично авторы могут создавать, удалять и редактировать и свои посты.
Также пользователи могут подписываться друг на друга.
Сами пользователи должны быть зарегестрированы, т.к. анонимные пользователи имеют лишь ограниченный доступ.

В дальнейшем на базе такого бэкенда при дальнейшем развитии можно сделать полноценнный сайт или приложение для ведения блогов.



## **Как запустить проект:**

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/NikkZav/api_final_yatube.git
```

```
cd api_final_yatube
```

Cоздать и активировать виртуальное окружение:

```
py -3.10 -m venv env
```

```
source env/bin/activate
```

Установить зависимости из файла requirements.txt:

```
python -m pip install --upgrade pip
```

```
pip install -r requirements.txt
```

Выполнить миграции:

```
python manage.py migrate
```

Запустить проект:

```
python manage.py runserver
```


## **Примеры:**
1. Полуить все посты: <p>
  GET `/api/v1/posts/` <p>
    Ответ: <p>
```
[
    {
        "id": 4,
        "author": "regular_user",
        "text": "Пост зарегистрированного пользователя.",
        "pub_date": "2025-03-09T00:15:48.444104Z",
        "image": null,
        "group": null
    },
    {
        "id": 5,
        "author": "regular_user",
        "text": "Пост с группой",
        "pub_date": "2025-03-09T00:16:56.553192Z",
        "image": null,
        "group": 1
    }
]
```

2. Полуить пост под конкретным индексом: <p>
  GET `/api/v1/posts/5/` <p>
    Ответ: <p>
```
{
    "id": 5,
    "author": "regular_user",
    "text": "Пост с группой",
    "pub_date": "2025-03-09T00:16:56.553192Z",
    "image": null,
    "group": 1
}
```

3. Cоздать пост: <p>
  POST `/api/v1/posts/` <p>
  Body (тело запроса):
```
{
    "text": "Пост зарегистрированного пользователя."
}
```
  Ответ: <p>
```
{
    "id": 5,
    "author": "regular_user",
    "text": "Пост с группой",
    "pub_date": "2025-03-09T00:16:56.553192Z",
    "image": null,
    "group": 1
}
```

4. Cоздать комментарий: <p>
  POST `/api/v1/posts/5/comments/` <p>
  Body (тело запроса):
```
{
    "text": "Тестовый комментарий"
}
```
  Ответ: <p>
```
{
    "id": 4,
    "author": "regular_user",
    "text": "Тестовый комментарий",
    "created": "2025-03-09T00:33:08.070674Z",
    "post": 5
}
```

> [!NOTE]
> Более подробно с примерами запросов можно ознакомиться при помощи файла https://github.com/NikkZav/api_final_yatube/blob/master/yatube_api/static/redoc.yaml
