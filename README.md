# Задание 2

1. В корневой папке проекта есть Dockerfile, который содержит
   инструкции для создания образа.
   Создать образ:

```bash
docker build -t django_app .
```

Проверить, что образ создан, можно с помощью команды:

```bash
docker images
```

В списке образов должен быть образ django_app.

2. Запустить контейнер с приложением:

```bash
docker run --name django-app -p 8000:8000 django_app
```

3. Открыть стартовую страницу на хостовой машине:
   http://127.0.0.1:8000

# Задание 3

- Создать контейнер, в котором будет развернута БД PostgreSQL.
- Создать локально папку, в которую будут размещаться данные базы.

1. Создать локальную папку для хранения данных БД.

2. Убедиться, что порт 5432 свободен.

3. Запуск контейнера с PostgreSQL с помощью официального образа.

```bash
docker run --name db-postgres -e POSTGRES_PASSWORD=qwerty123 -v ~/Documents/python_developer/skypro/postgres-data:/var/lib/postgresql/data -p 5432:5432 -d postgres
```

4. Проверка работы PostgreSQL

- Запустить оболочку bash, чтобы получить доступ к командной строке контейнера

```bash
docker exec -it db-postgres /bin/bash
```

- Запустить клиентскую утилиту командной строки PostgreSQL

```bash
psql -U postgres
```

- Создать БД

```bash
create database django_project;
```

- Просмотерть список БД

```bash
\l
```

- Выход

```bash
\q
```

- Выход из контейнера

```bash
exit
```
