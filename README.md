# API YAMDB
## Краткое описание проекта

Проект является REST API для сервиса по сбору отзывов о фильмах, музыке и книгах YAMDB. Пользователи портала могут оставлять свои отзывы и оценки к произведениям, а также комментировать другие рецензии. На основании оставленных произведению оценок, для него формируется средниий балл.

## Как запустить проект
         
1. Клонируйте репозиторий и перейдите в него в командной строке:
```      
git clone https://github.com/bigbang13/infra_sp2.git
cd infra_sp2
```      
2. Создайте в клонированной директории файл .env. Ниже приведен пример его наполнения:
```
DB_ENGINE=django.db.backends.postgresql #указываем что работаем с postgresql
DB_NAME=postgres #указываем имя базы данных
POSTGRES_USER=set_your_username #логин для подключения к БД
POSTGRES_PASSWORD=set_your_pwd #пароль для подключения к БД
DB_HOST=db #название контейнера
DB_PORT=5432 #порт для подключения к БД
```
3. Запустите docker-compose. Для этого необходимо перейти в папку infra и выполнить команду:
```
docker-compose up -d
```
4. Проверьте, что контейнеры запустились:
```
docker container ls
```
5. Выполните миграции:
```
docker-compose exec web python manage.py migrate
```
6. Создайте суперпользователя:
```
docker-compose exec web python manage.py createsuperuser
```
7. Подгрузите статику:
```
docker-compose exec web python manage.py collectstatic --no-input
```
8. Заполните базу данными:
```
docker-compose exec web python manage.py loaddata fixtures.json
```
Остановить работу контейнеров можно командой ```docker-compose down```.

Документация после запуска доступна по адресу [localhost/redoc](http://localhost/redoc/).

## Технологии
### API
- Python 3.8.10
- Django 2.2.16
- Django Rest Framework 3.12.4
- PostgreSQL 13.0
- Gunicorn 20.0.4
- Nginx 1.21.3

### Контейнер
- Docker 20.10.17
- Docker Compose 1.25.0

### Автор

_Рябов В.С._
_email: ryabov.v.s@yandex.ru_
_github: https://github.com/bigbang13_
