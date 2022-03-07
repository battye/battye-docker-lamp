## Notes

Wait a minute or so after starting the containers before loading any database connections, because it cannot connect until all the containers have finished setting up.

### Starting and Stopping

```
# To start
docker-compose up -d

# To stop and remove (the image can be deleted in the Docker UI)
docker-compose down --volumes
```

### CLI

```
docker exec -it battye-docker-lamp-www-1 /bin/bash
```

### docker-lamp documentation

This is a Docker example with Apache, MySQL 8.0, PhpMyAdmin and PHP 8.1

- You can use MariaDB 10.1 if you checkout to the tag `mariadb-10.1` - contribution made by [luca-vercelli](https://github.com/luca-vercelli)
- You can use MySQL 5.7 if you checkout to the tag `mysql5.7`

Open phpMyAdmin at [http://localhost:8000](http://localhost:8000)
Open wthe eb browser to look at a simple PHP example at [http://localhost:8001](http://localhost:8001) (the `www/` directory is where the files should be stored)

Run the MySQL client with:

- `docker-compose exec db mysql -u root -p` 

Enjoy!
