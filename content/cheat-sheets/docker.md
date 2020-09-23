+++ 
date = "1979-01-01"
title = "docker"
description = "docker"
type ="fab fa-docker"
+++

[Everything](https://github.com/wsargent/docker-cheat-sheet)

<h2 id=Docker>Docker
<img src="https://www.docker.com/sites/default/files/social/docker_facebook_share.png" height="100" width="100" align="right">
</h2>

#### Commandes

```sh
#container
docker container ls
docker container prune

#images
docker image ls -a
docker image prune -a

#sys
docker system info
docker system prune

#network
docker network ls
```


#### Exemple de docker compose file


```yml
version: '2.1'

services:

  users-db:
    container_name: users-db
    build: 
      context: ../usersTDDC/project/db
    # context: https://github.com/jbjouvin/usersTDDC.git#master:project/db
    ports:
        - 5435:5432  # expose ports - HOST:CONTAINER
    environment:
      - POSTGRES_USER=postgres
      - POSTGRES_PASSWORD=postgres
    healthcheck:
      test: exit 0

  users-service:
    container_name: users-service
    build: 
      context: ../usersTDDC
      dockerfile: Dockerfile-local
    # build: https://github.com/jbjouvin/usersTDDC.git
    volumes:
      - '../usersTDDC:/usr/src/app' # If working on docker machine on linux dont do this ! only win or osx
    ports:
      - "5001:5000"
    environment:
      - APP_SETTINGS=project.config.DevelopmentConfig
      - DATABASE_URL=postgres://postgres:postgres@users-db:5432/users_dev
      - DATABASE_TEST_URL=postgres://postgres:postgres@users-db:5432/users_test
      - SECRET_KEY=my_precious
    depends_on:
      users-db:
        condition: service_healthy
    links:
      - users-db

  nginx:
    container_name: nginx
    build: ./nginx/
    restart: always
    ports:
      - 80:80
    depends_on:
      users-service:
        condition: service_started
      web-service:
        condition: service_started
    links:
      - users-service
      - web-service

  web-service:
    container_name: web-service
    build:
      # context: https://github.com/jbjouvin/clientTDDC.git
      context: ../clientTDDC
      dockerfile: Dockerfile-local
    environment:
        - NODE_ENV=development
        - REACT_APP_USERS_SERVICE_URL=http://localhost
    volumes:
      - '../clientTDDC:/usr/src/app'
      - '/usr/src/app/node_modules'
    ports:
      - '9000:9000' # expose ports - HOST:CONTAINER
    depends_on:
      users-service:
        condition: service_started
    links:
      - users-service

  swagger:
    container_name: swagger
    build:
      context: ../swaggerTDDC
    ports:
      - '8080:8080' # expose ports - HOST:CONTAINER
    environment:
      - API_URL=https://raw.githubusercontent.com/jbjouvin/swaggerTDDC/master/swagger.json
    depends_on:
      users-service:
        condition: service_started
```

Il comprend:

<!-- | service     	| name          	|
|-------------	|---------------	|
| db postgres 	| users-db      	|
| front react 	| web-service   	|
| back python 	| users-service 	|
| nginx       	| nginx         	|
| swagger     	| swagger       	| -->

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;}
.tg th{font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;}
.tg .tg-jruv{font-size:13px;background-color:#ecf4ff;vertical-align:top}
.tg .tg-b3rt{font-weight:bold;font-size:15px;background-color:#68cbd0;vertical-align:top}
</style>
<table class="tg">
  <tr>
    <th class="tg-b3rt">service</th>
    <th class="tg-b3rt">name</th>
  </tr>
  <tr>
    <td class="tg-jruv">db postgres</td>
    <td class="tg-jruv">users-db</td>
  </tr>
  <tr>
    <td class="tg-jruv">front react</td>
    <td class="tg-jruv">web-service</td>
  </tr>
  <tr>
    <td class="tg-jruv">back python</td>
    <td class="tg-jruv">users-service</td>
  </tr>
  <tr>
    <td class="tg-jruv">nginx</td>
    <td class="tg-jruv">nginx</td>
  </tr>
  <tr>
    <td class="tg-jruv">swagger</td>
    <td class="tg-jruv">swagger</td>
  </tr>
</table>

