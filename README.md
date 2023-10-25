# go-micro

A comprehensive example of building a web application with microservices architecture using **Go**.

## Overview

This repository serves as an example of a microservices-oriented application. *Microservices* are a contemporary architectural choice that breaks down applications into loosely coupled, independently deployable, and maintainable services. This project demonstrates how multiple services can effectively interact and accomplish various tasks.

### Features:

- **Front End Service**: Displays web pages.
- **Authentication Service**: Manages user authentication using a Postgres database.
- **Logging Service**: Logs events and stores them in a MongoDB database.
- **Listener Service**: Receives and processes messages from RabbitMQ.
- **Broker Service**: Optional gateway for the entire microservices cluster.
- **Mail Service**: Processes JSON payloads, formats them as emails, and sends them.

All the services mentioned above communicate with each other and a front-end application through multiple mechanisms: *REST API*, *RPC*, *gRPC*, and *AMQP*.

The choice of Go for these services is due to its efficiency and capabilities in building distributed web applications.

Moreover, this project also provides guidance on deploying the application to *Docker Swarm* and *Kubernetes*, ensuring scalability and high availability.

## Demo

Live demonstration of the cluster running on *Caddy* using *Docker Swarm*: [https://swarm.ivnv.dev/](https://swarm.ivnv.dev/)

## Installation & Usage

### Clone the Repository

```sh
git clone git@github.com:ivnvxd/go-micro.git
```

### 🐳 Using Docker-Compose

This is the easiest way to run the application. It will build all the services and launch them in *Docker* containers.

```sh
make up_build # Build all microservices and start the app
make schema   # Initialize schema in PostgreSQL and populate with test data
```

Access the application at: [http://localhost/](http://localhost/)

To stop the application use `make down`.

### 🐝 Deploying with Docker Swarm

*Docker Swarm* is a container orchestration tool built into Docker Engine. It allows deploying and managing a cluster of Docker nodes. The images for all services are available on [Docker Hub](https://hub.docker.com/u/ivnvxd).

```sh
docker swarm init                        # Initialize Docker Swarm
docker stack deploy -c swarm.yml myapp   # Deploy all services to the cluster
```

The application will be available at: [http://localhost/](http://localhost/)

To stop the application use `docker stack rm myapp && docker swarm leave --force`.

### ☸️ Running on Kubernetes with Minikube

This is a more advanced way to run the application. It will deploy the application to a local *Kubernetes* cluster using *Minikube*. The images for all services are available on [Docker Hub](https://hub.docker.com/u/ivnvxd).

The local Postgres instance is used for the user database.

```sh
docker-compose -f postgres.yml up -d      # Launch the local Postgres instance
minikube start                            # Initialize the local Kubernetes cluster
minikube addons enable ingress            # Activate Ingress addon
kubectl apply -f k8s                      # Deploy all services to the cluster
minikube tunnel                           # Expose application to the web
```

Visit the app here: [http://front-end.info/](http://front-end.info/)

To stop the application use `kubectl delete -f k8s && minikube stop && docker-compose -f postgres.yml down`.

## Testing

- For PostgreSQL User Database:

```sh
echo "SELECT * FROM public.users;" | docker exec -i go-micro-postgres-1 psql -U postgres -d users
```

- For MongoDB Logs:
Use [MongoDB Compass](https://www.mongodb.com/try/download/compass):

```mongodb
mongodb://admin:password@localhost:27017/logs?authSource=admin&readPreference=primary&appname=MongoDB%20Compass&directConnection=true&ssl=false
```

- To run unit tests:

```sh
make test
```

---

:octocat: This is the training project of the ["Working with Microservices in Go"](https://www.udemy.com/course/working-with-microservices-in-go/) course available on [Udemy](https://www.udemy.com)

> GitHub [@ivnvxd](https://github.com/ivnvxd) &nbsp;&middot;&nbsp;
> LinkedIn [@Andrey Ivanov](https://www.linkedin.com/in/abivanov/)
