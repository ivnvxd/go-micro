# go-micro

:construction: Work in progress! :construction:

## Demo

Demo cluster running on Caddy using Docker Swarm is available at: [https://swarm.ivnv.dev/](https://swarm.ivnv.dev/)

## Installation

### Clone repository

```sh
git clone git@github.com:ivnvxd/go-micro.git
```

## Usage

### docker-compose

<!-- create folder structure -->

```sh
make up_build # Build all microservices and start the app
make schema  # Create schema in PostgreSQL and add test data
```

The app will be avaialble at: [http://localhost/](http://localhost/)

### Docker Swarm

To get all services from Docker Hub and run using Docker Swarm:

```sh
docker swarm init
docker stack deploy -c swarm.yml myapp
```

### Kubernetes

To run the app on Kubernetes using Minikube:

```sh
docker-compose -f postgres.yml up -d  # run the local Postgres instance

minikube start  # start the local Kubernetes cluster
minikube addons enable ingress  # enable Ingress addon
kubectl apply -f k8s  # deploy all services to the cluster
minikube tunnel  # expose the app to the Internet
```

The app is available at: [http://front-end.info/](http://front-end.info/)

## Testing

Check users database in PostgreSQL:

```sh
echo "SELECT * FROM public.users;" | docker exec -i go-micro-postgres-1 psql -U postgres -d users
```

Check logs in MongoDB with [MongoDB Compass](https://www.mongodb.com/try/download/compass):

```mongodb
mongodb://admin:password@localhost:27017/logs?authSource=admin&readPreference=primary&appname=MongoDB%20Compass&directConnection=true&ssl=false
```

---

:octocat: This is the training project of the ["Working with Microservices in Go"](https://www.udemy.com/course/working-with-microservices-in-go/) course on [Udemy](https://www.udemy.com)

> GitHub [@ivnvxd](https://github.com/ivnvxd) &nbsp;&middot;&nbsp;
> LinkedIn [@Andrey Ivanov](https://www.linkedin.com/in/abivanov/)
