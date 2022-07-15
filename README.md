## Yatube API

Проект API позволяет делать запросы к базе данных социальной сети Yatube. Поддерживаются все функции, которые есть в социальной сети (регистрация, получение списка постов и отдельного поста, отправка поста и комментария, подписка на авторов), также реализована авторизация по JWT-токенам при помощи библотеки Djoser.


### Как запустить проект:

Клонировать репозиторий и перейти в него в командной строке:

```
git clone https://github.com/qutha/api_final_yatube.git
```

```
cd yatube_api
```

Cоздать и активировать виртуальное окружение:

```
python3 -m venv venv
```

```
source env/bin/activate
```

```
python3 -m pip install --upgrade pip
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

***

### Примеры запросов



#### Запрос

Пример POST-запроса с токеном Антона Чехова: добавление нового поста.

```
POST /api/v1/posts/
```
```
{
    "text": "Вечером собрались в редакции «Русской мысли», чтобы поговорить о народном театре.",
    "group": 1
} 
```

#### Ответ

```
{
    "id": 14,
    "text": "Вечером собрались в редакции «Русской мысли», чтобы поговорить о народном театре.",
    "author": "anton",
    "image": null,
    "group": 1,
    "pub_date": "2021-06-01T08:47:11.084589Z"
} 
```

***

#### Запрос

Пример POST-запроса с токеном Антона Чехова: отправляем новый комментарий к посту с ```id=14```

```
POST /api/v1/posts/14/comments/
```

```
{
    "text": "Ваша статья меня поразила!"
} 
```

#### Ответ

```
{
    "id": 4,
    "author": "anton",
    "post": 14,
    "text": "Ваша статья меня поразила!",
    "created": "2021-06-01T10:14:51.388932Z"
}
```

***

### Использованные технологии


- Python 3.7
- Django 2.2
- Django REST 3.12
- SQLite

***

### Автор

Студент по специальности информатика и вычислительная техника, backend разработчик, или же просто Василий
