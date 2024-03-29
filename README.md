# Assessment Exam

## Setup Guide

1. Start services and install dependencies

```
$ docker-compose up -d --build
$ docker-compose exec app composer install
$ docker-compose exec app cp .env.dev .env
```

2. Add/modify database configuration in `.env` file

```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=root
DB_PASSWORD=secret
```

3. Start the project

```
$ docker-compose exec app php artisan config:clear
$ docker-compose exec app php artisan key:generate
$ docker-compose exec app php artisan storage:link
$ docker-compose exec app chmod -R 777 storage
$ docker-compose exec app chmod -R 777 bootstrap/cache
$ docker-compose exec app php artisan optimize
```

4. Start database migration

```
$ docker-compose exec app php artisan migrate
```

## API Usage

API Endpoint:

```
http://localhost:8000/api/users
```

Headers:

```
Accept: application/json
```

Payload:
| Key | Value (Sample) | Description |
|-----------|------------------|-------------------|
| firstName | John | User's first name |
| lastName | Doe | User's last name |
| email | johndoe@test.com | User's email |

## Notification Logs

Notification logs can be found on the directory:

```
storage/logs/users.log
```
