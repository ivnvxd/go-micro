# go-micro

:construction: Work in progress! :construction:

## Demo

Available at: [https://swarm.ivnv.dev/]

## Installation

### Clone repository

```sh
git clone git@github.com:ivnvxd/go-micro.git
```

### Auth Service

To add new users database run:

```sh
make schema
```

## Usage

### docker-compose

To build all microservices and start the app:

```sh
make up_build
```

The app will be avaialble on: [http://localhost/]

### Docker Swarm

```sh
docker swarm init
docker stack deploy -c swarm.yml myapp
```

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
