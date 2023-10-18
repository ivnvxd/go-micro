# go-microservices

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
