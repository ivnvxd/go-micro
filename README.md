# go-microservices

To add new users database run:

```sh
cat authentication-service/users.sql | docker exec -i go-microservices-postgres-1 psql -U postgres -d users
```

To check database run:

```sh
echo "SELECT * FROM public.users;" | docker exec -i go-microservices-postgres-1 psql -U postgres -d users
```

---

:octocat: This is the training project of the ["Working with Microservices in Go"](https://www.udemy.com/course/working-with-microservices-in-go/) course on [Udemy](https://www.udemy.com)

> GitHub [@ivnvxd](https://github.com/ivnvxd) &nbsp;&middot;&nbsp;
> LinkedIn [@Andrey Ivanov](https://www.linkedin.com/in/abivanov/)
