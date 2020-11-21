You must need to install database before run Strapi project

## 1. Install postgress

Update docker-compose.yml

```
  postgres:
    image: postgres
    environment:
      POSTGRES_DB: strapi
      POSTGRES_USER: strapi
      POSTGRES_PASSWORD: strapi
    volumes:
      - ./data:/var/lib/postgresql/data

```

## 2. Run docker-compose pull && docker-compose up

Now you have the database and you can return the original docker-compose.yml

```
version: "3"
services:
  strapi:
    image: strapi/strapi
    environment:
      DATABASE_CLIENT: postgres
      DATABASE_NAME: strapi
      DATABASE_HOST: postgres
      DATABASE_PORT: 5432
      DATABASE_USERNAME: strapi
      DATABASE_PASSWORD: strapi
    volumes:
      - ./app:/srv/app
    ports:
      - "1337:1337"
    depends_on:
      - postgres

  postgres:
    image: postgres
    environment:
      POSTGRES_DB: strapi
      POSTGRES_USER: strapi
      POSTGRES_PASSWORD: strapi
    volumes:
      - ./data:/var/lib/postgresql/data
```

## 3. Run docker-compose run -D

If you have an error when initialize docker-compose, try up your database first and then strapi container .
This step spended 5min to me, maybe is a good time to enjoy a coffee :)

