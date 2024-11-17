### Installation and running Atutor

Create the following directories

```bash
mkdir -p bin/webserver bin/mysql bin/phpmyadmin
mkdir -p www data/mysql logs/mysql
```

Docker configuration for Apache, PHP 7.4, MySQL 8 and phpmyadmin.

1. Create sessions folder.
2. Create data/mysq folder.
3. Create logs/mysql folder.
4. Run: docker-compose build
5. Run: docker-compose up

phpmyadmin username / password: root / password

Config logs mysql :

sudo docker exec a258924db900 chmod 0750 /var/log/mysql
sudo docker exec a258924db900 chmod 0775 /var/log
sudo docker exec a258924db900 chmod 0755 /var
sudo docker exec a258924db900 chmod 777 /var/log/mysql/error.log
sudo docker exec a258924db900 chmod 0444 /etc/mysql/mysql.conf.d/\*
sudo docker exec a258924db900 touch /var/log/mysql/slow.log
sudo docker exec a258924db900 chmod 666 /var/log/mysql/slow.log
sudo docker cp ~/Desktop/mysqld.cnf 34b2913dd61a:/etc/mysql/mysql.conf.d/mysqld.cnf
sudo docker restart a258924db900

To run the application


Rebuild container 
```bash
sudo docker compose down
sudo docker compose build
sudo docker compose up -d
```

Open a web browser and go to:

```
(localhost)[http://localhost:8009]
```

Access the mySQL shell inside the container.

```bash
sudo docker exec -it png-mysql-test mysql -u atutor -p
```

### Misc
Fix persmissions


```bash
sudo chmod -R 777 ./sessions
```

Ensure the container has access
```bash
sudo chown -R www-data:www-data ./sessions

```
Make sure that the ./data/mysql and ./logs/mysql directories on the host machine have the correct permissions, so MySQL can write data to them. You can run:

```
sudo chown -R 999:999 ./data/mysql ./logs/mysql
```

Check permission

```bash
sudo docker exec -it <container_id> bash
ls -l /sessions  # Check permissions
```
