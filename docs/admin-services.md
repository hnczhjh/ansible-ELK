# Start or Stop the Services

These commands you must know when you using the Elasticsearch of Websoft9

### Elasticsearch

```shell
sudo systemctl start elasticsearch-server
sudo systemctl stop elasticsearch-server
sudo systemctl restart elasticsearch-server
sudo systemctl status elasticsearch-server

# you can use this debug mode if Elasticsearch service can't run
elasticsearch-server console
```

### MySQL

```shell
sudo systemctl start mysql
sudo systemctl stop mysql
sudo systemctl restart mysql
sudo systemctl status mysql
```

### Redis

```shell
systemctl start redis
systemctl stop redis
systemctl restart redis
systemctl status redis
```
