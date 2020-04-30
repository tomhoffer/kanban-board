# Kanban Application

This is a simple implementation of a Kanban Board, a tool that helps visualize and manage work.
A Kanban Board usually contains 3 main columns - *TODO*, *InProgres*s and *Done* and enables you to move tasks between these states. 

![Kanban](https://github.com/wkrzywiec/kanban-board/blob/master/assets/kanban.gif)

The implementation contains of 3 separate Docker containers:

- PostgreSQL database
- Java backend (Spring Boot)
- Angular frontend

## kanban-postgres (Database)

PostgreSQL database contains only single schema with two tables - kanban
and task table.

After running the app it can be accessible using this connector:

- Host: *localhost*
- Database: *kanban*
- User: *kanban*
- Password: *kanban*

Just like the other parts of application, Postgres database is containerized and
the definition of its Docker container can be found in
*docker-compose.yml* file.

```yml
kanban-postgres:
    image: "postgres:9.6-alpine"
    container_name: kanban-postgres
    volumes:
      - kanban-data:/var/lib/postgresql/data
    ports:
      - 5432:5432
    environment:
      - POSTGRES_DB:kanban
      - POSTGRES_USER:kanban
      - POSTGRES_PASSWORD:kanban
```

## kanban-app (REST API)

This is a Spring Boot (Java) based application that connects with a
database that and exposes REST endpoints that can be consumed by
frontend. It provides GET, POST, PUT and DELETE methods for two resources - kanban and task.

Full list of available REST endpoints can be found in Swagger UI using link: **http://localhost:8080/api/swagger-ui.html**

![swagger-ui](https://github.com/wkrzywiec/kanban-board/blob/master/assets/swagger.png)

This app is also put in a Docker container and its definition can be found
in *kanban-app/Dockerfile*. 


## kanban-ui (Frontend)
This is an Angular-based UI for the user. It consumes the REST API endpoints provided by
*kanban-app*.
It can be accessed using link: **http://localhost:4200/**

---
# Installing assignment prerequisites

In order to run this application you need to install 3 tools: **Docker**, **Docker Compose** and **Cypress**.

Instructions how to install **Docker** on: [Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/), [Windows](https://docs.docker.com/docker-for-windows/install/) , [Mac](https://docs.docker.com/docker-for-mac/install/) .

**Docker Compose** is already included in installation packs for *Windows* and *Mac*, so only Ubuntu users needs to follow [these instructions](https://docs.docker.com/compose/install/) .

Cypress can be downloaded and installed via npm. Check the [cypress website](https://docs.cypress.io/guides/getting-started/installing-cypress.html) for a more detailed guide.

# Running the app
Excited to start with the assignment ?

Before moving on to the first task, spin-up the application and run it locally on your machine using docker-compose. The `docker-compose.yml` file contains all containers that you need. There's no need to modify them in any way.
After you spin-up the application, open it in your browser on URL: **http://localhost:4200/**.




