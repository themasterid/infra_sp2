# API_YAMDB
REST API для сервиса YaMDb — базы отзывов о фильмах, книгах и музыке.

## Описание

API для сервиса YaMDb.

Позволяет работать со следующими сущностями:
- Отзывы
- Коментарии к отзывам
- Пользователи
- Категории (типы) произведений
- Категории жанров
- Произведения (на которые пишут отзывы)

### Как запустить проект:

Клонируйте репозиторий и перейдите в него в командной строке:
```
git clone https://github.com/themasterid/infra_sp2
cd infra_sp2
```

Перейдите в папку с проектом:
```
cd api_yamdb
```

Cоздайте и активируйте виртуальное окружение:
```
python3 -m venv venv
source /venv/bin/activate
python -m pip install --upgrade pip
```

Установите зависимости из файла requirements.txt:
```
pip install -r requirements.txt
```

Перейдите в папку с файлом docker-compose.yaml:
```
cd infra
```

Разверните контейнеры:
```
docker-compose up -d --build
```

Выполните миграции:
```
docker-compose exec web python manage.py migrate
```

Создайте суперпользователя:
```
docker-compose exec web python manage.py createsuperuser
```

Соберите статику:
```
docker-compose exec web python manage.py collectstatic --no-input
```

Создайте дамп базы:
```
docker-compose exec web python manage.py dumpdata > fixtures.json
```

Остановите приложение в контейнерах:
```
docker-compose down -v
```

Запустите pytest (при запущенном виртуальном окружении):
```
cd infra_sp2 && pytest
```


### Шаблон наполнения .env
```
# указываем, с какой БД работаем
DB_ENGINE=django.db.backends.postgresql
# имя базы данных
DB_NAME=postgres
# логин для подключения к базе данных
POSTGRES_USER=postgres
# пароль для подключения к БД (установите свой)
POSTGRES_PASSWORD=postgres
# название сервиса (контейнера)
DB_HOST=db
# порт для подключения к БД
DB_PORT=5432
```

### Документация API YaMDb
Доступна по эндпойнту:
```json
/redoc/
```
