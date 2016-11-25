# [Mongo](https://hub.docker.com/_/mongo/)
```
$ docker run --name some-mongo \
             -v /scratch/mongo:/data/db \
             -p 27017:27017 -d mongo
```
### Client
```
$ docker run -it --link some-mongo:mongo --rm \
             mongo sh -c 'exec mongo "$MONGO_PORT_27017_TCP_ADDR:$MONGO_PORT_27017_TCP_PORT/test"'
```
# [Postgress](https://hub.docker.com/_/postgres/)
```
$ docker run --name some-postgres \
             -v /scratch/pg:/var/lib/postgresql/data \
             -e POSTGRES_PASSWORD=123456 -d postgres
```
### Client
```
$ docker run -it --rm \
             --link some-postgres:postgres \
             postgres psql -h postgres -U postgres
```
# [Jenkins](https://hub.docker.com/_/jenkins/)
```
$ docker run -u root --name jenkins \
             -p 10000:8080 -p 50000:50000 \
             -v host/path:/var/jenkins_home jenkins
```
# [MySQL](https://hub.docker.com/_/mysql/)
```
$ docker run --name mydb \
             -e MYSQL_ROOT_PASSWORD=123456 \
             -v host/path:/var/lib/mysql \
             -d mysql:5
```
### Client
```
$ docker run -it --rm mysql \
             mysql -hsome.mysql.host -usome-mysql-user -p
```
# [Grafana](https://hub.docker.com/r/grafana/grafana/)
```
$ docker run -it --name grafana \
         -p 3000:3000 \
         -v /scratch/grafana/etc:/etc/grafana \
         -v /scratch/grafana/var:/var/lib/grafana \
         -v /scratch/grafana/log:/var/log/grafana grafana/grafana:4.6.1
```

# [RabbitMQ](https://hub.docker.com/_/rabbitmq/)
```
docker run -d --hostname rmq --name rabbitmq \
           -e RABBITMQ_DEFAULT_USER=user -e RABBITMQ_DEFAULT_PASS=changeme \
           -p 25672:25672 -p 4369:4369 -p 5671:5671 -p 5672:5672 \
           -p 8080:15672 rabbitmq:3-management
```

# [Apache](https://hub.docker.com/_/httpd/)
```
docker run -d --name apache \
           -v /opt/www/:/usr/local/apache2/htdocs/ \
           -p 8080:80 httpd:2.4
```

# [Redis](https://hub.docker.com/_/redis/)
```
docker run -d --name redis_server \
           -v /scratch/data:/data \
           -p 6379:6379 redis:4
```
### Client
```
docker run -it --link redis_server:redis --rm redis redis-cli -h redis -p 6379
```
