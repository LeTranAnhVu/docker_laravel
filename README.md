# REQUIRE:
- install `docker` : https://docs.docker.com/install/
- install `composer`, `laravel`
- **NO NEED**  to install `webserver`, `php`, as well as `mysql`


# SPEC: 
- Docker version `18.09.2`
- Laravel Installer `2.0.1`
- Composer version `1.8.5`
- Laravel Framework `5.8.28`

# PREPARE:

- Create the empty folder `docker_db_storage`
- Create `.env` file in root directory by duplicate the `.env-example`
- **NOTICE:** `mysql` configure should like snippet below due to configure in `docker-compose.yml` at `mysql` service.

```console
DB_CONNECTION=mysql
DB_HOST=c-mysql
DB_PORT=3306
DB_DATABASE=laravel
DB_USERNAME=admin
DB_PASSWORD=password
```


# RUN:
- Step 1: Build project:
```console
docker-compose up -d
```

- Step 2: **NOTE:** Access to work directory for `php artisan migrate` or something relate to the `database` 
```console
docker exec -it c-php bash
```
Then:
```console
composer install
php artisan key:generate
php artisan migrate
php artisan db:seed
```

- Step 3: Navigate bellow `url` to your browser: 
```console
localhost:8080
```


# Docker command:
- Build project:
```console
docker-compose up -d
```

- Restart the project
```console
docker-compose restart
```

- Access to work directory for `php artisan migrate` or something relate which the `database` 
```console
docker exec -it c-php bash
```
