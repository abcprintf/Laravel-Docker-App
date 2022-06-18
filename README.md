## Laravel-Docker-App
    - PHP 7.4
    - MySql
    - Nginx

## Setup
```
docker-compose up -d

docker-compose build --force-rm
```

## config laravel_app
```
docker exec -ti laravel_app php artisan key:generate

docker exec -ti laravel_app php artisan config:cache
```

## config db
```
docker exec -ti db bash

mysql -u root -p

show databases;

GRANT ALL ON laravel.* TO 'laraveluser'@'%' IDENTIFIED BY 'laravel_db_password';

FLUSH PRIVILEGES;

EXIT;
```

## After config DB
```
docker exec -it laravel_app php artisan migrate

docker exec -it laravel_app php artisan tinker

// test get data
\DB::table('migrations')->get();
```