# REQUIRE:
- install `docker` : https://docs.docker.com/install/
- install `composer`, `laravel`
- **NO NEED**  to install `webserver`, `php`, as well as `mysql`


# SPEC: 
- Docker version `18.09.2`
- Laravel Installer `2.0.1`
- Composer version `1.8.5`
- Laravel Framework `5.8.28`

# RUN:
- Step 1: Build project:
```console
docker-compose up -d
```

- Step 2: Download vendor for laravel:
```console
composer install
php artisan key:generate
```


- Step 3: **NOTE:** Access to work directory for `php artisan migrate` or something relate to the `database` 
```console
docker exec -it c-php bash
```

- Step 4: Navigate bellow `url` to your browser: 
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