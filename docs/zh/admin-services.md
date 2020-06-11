# 服务启停

使用由Websoft9提供的 Elasticsearch 部署方案，可能需要用到的服务如下：

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
