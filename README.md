# oms
Orders Management System

Собрать образы
```sh
docker-compose build
```

Выполнить миграции
```sh
docker-compose run app sh -c "python manage.py makemigrations"
```
или
```sh
docker-compose exec app python manage.py migrate --noinput
```

Запустить тестирование и проверку code style
```sh
docker-compose run app sh -c "python manage.py test && flake8"
```

Запустить приложение
```sh
docker-compose up -d
```
Пересобрать образы и запустить приложение
```sh
docker-compose up -d --build
```
Посмотреть логи
```sh
docker-compose logs -f
```
Подключиться к базе данных:
```sh
docker-compose exec db psql --username=oms --dbname=oms
```
Проверить подключенный том с файлами PGSQL:
```sh
docker volume inspect django-on-docker_postgres_data
```
Запуск в production environment
```sh
docker-compose -f docker-compose.prod.yml down -v
docker-compose -f docker-compose.prod.yml up -d --build
docker-compose -f docker-compose.prod.yml exec app python manage.py migrate --noinput
```
