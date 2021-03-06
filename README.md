# Starnavi – тестовое задание
Предполагается, что все команды ниже будут вводится из корня проекта с активированной вертуальной средой (команда source из скрипта ниже). 
В качестве БД используется sqlite.


Запуск проекта:

```shell script
python -m venv venv
source venv/bin/activate
python -m pip install -r requirements.txt
cd src
python manage.py migrate
python manage.py runserver
```

Приложение доступно по адресу http://localhost:8000. 
Для удобства добавлена поддержка django-admin.

Запуск бота:
```shell script
cp .env.example .env
source venv/bin/activate
python src/bot.py
```

Конфигурация бота производится с помощью .env файла в корне проекта. 
Для примера приложен файл .env.example. 

Путь до .env файла можно также задать с помощью параметра _--env-file_, например: `python src/bot.py --env-file .env.example`.

 # Описание API
 К проекту приложен дамп Postman-коллекции (v2.1) в качестве документации.
 
 Для авторизации используюся методы:
 - api/auth/obtain – получение access и refresh токенов и 
 - api/auth/refresh – для обновления access и refresh токена по refresh токену.
 
 Время жизни access токена по умолчанию равно 10 минутам.
 Время жизни refresh токена по умолчанию равно 7 дням.
 
 Помимо указанных в задании методов добавлены также методы:
 - api/user – получение данных текущего пользователя
 - api/analytics/users – получение статистики по всем пользователям
 - api/analytics/user/{username} - получение статистики по конкретному пользователю (в задании не был указан url для этого метода)
 
 Методы из раздела analytics требуют прав администратора (поле is_staff). Для создания администратора:
 
```shell script
source venv/bin/activate
cd src
python manage.py createsuperuser
```
