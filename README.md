We need to create a `.env` file with this variables:

```
MYSQL_ROOT_PASSWORD=root
MYSQL_DATABASE=project
```

Create the containers

```
docker-compose build
```

Start the containers

```
docker-compose up -d
```

Optional: Check if everything is installed properly, not required

```
docker-compose exec app composer require symfony/requirements-checker
docker-compose exec app php ./vendor/bin/requirements-checker
docker-compose exec app composer remove symfony/requirements-checker
rm -rf ./www/*
```

Start a new project, this is going to install the basic files and structure

```
docker-compose exec app composer create-project symfony/website-skeleton ./
docker-compose exec app composer require server --dev
```

Start the `dev` server

```
docker-compose exec app php bin/console server:start 0.0.0.0:8000
```

Stop the `dev` server

```
docker-compose exec app php bin/console server:stop
```

Stop the containers

```
docker-compose stop
```
