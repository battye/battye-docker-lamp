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
docker exec -it battye-docker-lamp_www_1 /bin/bash
```

### XDebug, Docker, VS Code, PHP and Mac

The tutorial [here](https://php.tutorials24x7.com/blog/how-to-debug-php-using-xdebug-visual-studio-code-and-docker-on-ubuntu) is quite useful for getting Xdebug, Docker and VS Code working. In the launch.json file, you might need to hardcode the path mapping (which might look something like this on Mac) if you see errors about an unverified breakpoint:

    "pathMappings": {
        "/var/www/html": "/Users/username/path/to/code/www/"
    }

In settings.json for VS Code, you might also need to have something like this so that the IDE does not look for a local PHP executable:

    {
        "php.debug.executablePath": "/Users/username/path/to/code/phpwrapper",
        "php.validate.executablePath": "/Users/username/path/to/code/phpwrapper",
        "php.suggest.basic": false
    }

Other important settings can be found in xdebug.ini in this repository. `host.docker.internal` can be used on Mac to determine the host machine. Xdebug logs can be found inside `./xdebug/xdebug.log`.

To access a website from within a Docker container from another computer on the same local network, run `ipconfig getifaddr en0` and then use the IP address. For Symfony websites, make sure the `APP_ENV` is set to `prod` first.

### docker-lamp documentation

This is a Docker example with Apache, MySQL 8.0, PhpMyAdmin and PHP 8.1

- You can use MariaDB 10.1 if you checkout to the tag `mariadb-10.1` - contribution made by [luca-vercelli](https://github.com/luca-vercelli)
- You can use MySQL 5.7 if you checkout to the tag `mysql5.7`

Open phpMyAdmin at [http://localhost:8000](http://localhost:8000)
Open wthe eb browser to look at a simple PHP example at [http://localhost:8001](http://localhost:8001) (the `www/` directory is where the files should be stored)

Run the MySQL client with:

- `docker-compose exec db mysql -u root -p` 

Enjoy!
