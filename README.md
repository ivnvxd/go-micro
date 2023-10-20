# go-micro

Install the necessary tools for gRPC:

```sh
go install google.golang.org/protobuf/cmd/protoc-gen-go@v1.27
go install google.golang.org/grpc/cmd/protoc-gen-go-grpc@v1.2
```

Install the [protocol buffer compiler](https://grpc.io/docs/protoc-installation/)

```sh
brew install protobuf
```

Run the following command to generate the gRPC code (optional):

```sh
cd logger-service/logs
protoc --go_out=. --go_opt=paths=source_relative --go-grpc_out=. --go-grpc_opt=paths=source_relative logs.proto
```

To build all microservices and the project run:

```sh
make up_build
```

To run the frontend run:

```sh
make start
```

To add new users database run:

```sh
cat authentication-service/users.sql | docker exec -i go-microservices-postgres-1 psql -U postgres -d users
```

Check users database in PostgreSQL:

```sh
echo "SELECT * FROM public.users;" | docker exec -i go-microservices-postgres-1 psql -U postgres -d users
```

Check logs in MongoDB with [MongoDB Compass](https://www.mongodb.com/try/download/compass):

```mongodb
mongodb://admin:password@localhost:27017/logs?authSource=admin&readPreference=primary&appname=MongoDB%20Compass&directConnection=true&ssl=false
```

---

:octocat: This is the training project of the ["Working with Microservices in Go"](https://www.udemy.com/course/working-with-microservices-in-go/) course on [Udemy](https://www.udemy.com)

> GitHub [@ivnvxd](https://github.com/ivnvxd) &nbsp;&middot;&nbsp;
> LinkedIn [@Andrey Ivanov](https://www.linkedin.com/in/abivanov/)
