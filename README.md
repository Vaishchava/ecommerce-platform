# Docker Setup

This fork adds Docker support to the original project, allowing the complete application stack to run using Docker Compose.

> **Original Project:** https://github.com/adarshdhauni/ecommerce-platform

## What Was Added

* Dockerfile for the React (Vite) frontend
* Dockerfile for the Express backend
* Docker Compose configuration
* MongoDB container using the official MongoDB image
* Persistent Docker volume for MongoDB data
* Container networking between frontend, backend, and database
* Development configuration for Vite (`--host 0.0.0.0`) to allow access from outside the container

## Project Structure

```
ecommerce-platform/
│
├── client/
│   ├── Dockerfile
│   └── ...
│
├── server/
│   ├── Dockerfile
│   └── ...
│
├── docker-compose.yml
└── README.md
```

## Containers

| Service  | Technology   | Port  |
| -------- | ------------ | ----- |
| Frontend | React + Vite | 5173  |
| Backend  | Express.js   | 3000  |
| Database | MongoDB      | 27017 |

## Start the Application

Build the Docker images:

```bash
docker compose build
```

Start all services:

```bash
docker compose up
```

Run in detached mode:

```bash
docker compose up -d
```

Stop the application:

```bash
docker compose down
```

Stop and remove volumes:

```bash
docker compose down -v
```

## Access the Application

Frontend

```
http://localhost:5173
```

Backend

```
http://localhost:3000
```

MongoDB

```
localhost:27017
```

## Docker Networking

The application uses Docker Compose networking.

* React communicates with the Express backend.
* Express communicates with MongoDB using the Docker service name:

```
mongodb://mongo:27017/ecommerce
```

Using the service name (`mongo`) instead of `localhost` allows containers to communicate over Docker's internal network.

## Persistent Storage

MongoDB data is stored in a Docker named volume.

This ensures database data is preserved even if the MongoDB container is recreated.

## Learning Outcomes

While Dockerizing this project, I practiced:

* Understanding an unfamiliar project structure
* Identifying multiple services
* Writing multiple Dockerfiles
* Creating a Docker Compose configuration
* Docker networking
* Persistent volumes
* Container debugging using Docker logs
* Environment variable configuration
* Debugging Vite container networking (`--host 0.0.0.0`)

## Acknowledgement

This repository is based on the original open-source project created by **Adarsh Dhauni**.

The application source code belongs to the original author.

This fork was created solely as a learning exercise to practice Docker and Docker Compose by containerizing the application.
