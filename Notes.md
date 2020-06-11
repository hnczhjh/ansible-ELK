# Elasticsearch on CentOS.notes

组件名称：Elasticsearch
安装文档：https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html
配置文档：https://www.elastic.co/guide/en/elasticsearch/reference/current/settings.html

支持平台：Debian家族 | RHEL家族 | Windows |Mac

责任人：helin

## 概要

Elasticsearch 是一个开源的分布式 RESTful 搜索和分析引擎，能够解决越来越多不同的应用场景。Elasticsearch为所有类型的数据提供实时搜索和分析。无论您是结构化文本还是非结构化文本，数字数据或地理空间数据，Elasticsearch都能以支持快速搜索的方式有效地对其进行存储和索引。您不仅可以进行简单的数据检索，还可以聚合信息来发现数据中的趋势和模式。随着数据和查询量的增长，Elasticsearch的分布式特性使您的部署可以随之无缝地增长。
Elasticsearch也使用Java开发并使用Lucene作为其核心来实现所有索引和搜索的功能，但是它的目的是通过简单的RESTful API来隐藏Lucene的复杂性，从而让全文搜索变得简单。

## 环境要求

- 程序语言：Java
- 应用服务器：自带
- 数据库：无
- 依赖组件：无
- 其他：

## 安装说明

### CentOS下

```
yum search java|grep jdk         
yum install java-1.8.0-openjdk                     #安装java
rpm --import https://artifacts.elastic.co/GPG-KEY-elasticsearch #导入key
cd /etc/yum.repos.d/                          
vi es.repo        
[elasticsearch-7.x]
name=Elasticsearch repository for 7.x packages
baseurl=https://artifacts.elastic.co/packages/7.x/yum
gpgcheck=1
gpgkey=https://artifacts.elastic.co/GPG-KEY-elasticsearch
enabled=1
autorefresh=1
type=rpm-md                                             #导入es仓库


yum install elasticsearch -y                       #安装elasticsearch
```

## 路径

- 程序路径： /usr/share/elasticsearch
- 日志路径：/var/log/elasticsearch/
- 配置文件路径：/etc/elasticsearch
- 其他...

## 配置

安装完成后，需要顺序完成如下配置

```
vi /etc/elasticsearch/elasticsearch.yml 在其中:
network.host: 0.0.0.0              #设置绑定地址默认为0.0.0.0 
http.port: 9200                    #设置端口为9200
cluster.initial_master_nodes: ["node-1", "node-2"]



vi /etc/sysctl.conf 在其中增加：
vm.max_map_count=655360           #调大普通用户虚拟内存

接着执行 sysctl -p              


```

## 账号密码

后台账号

- 登录地址: http://localhost:9200

- 账号密码：无

- 密码修改方案：最好是有命令行修改密码的方案

  

## 服务

```
安装后自带服务

systemctl daemon-reload                    #重新加载systemctl服务
sudo systemctl start elasticsearch         #启动服务
sudo systemctl enable elasticsearch         #服务自启
sudo systemctl status elasticsearch        #查看服务状态
```





## 环境变量

列出需要增加的环境变量以及增加环境变量的命令：

-无




## 版本号

通过如下的命令获取主要组件的版本号：

```
# Check elasticsearch version
rpm -qa|grep elasticsearch

```

## 常见问题

#### 有没有管理控制台？

http：//公网IP：9200可访问控制台

#### 本项目需要开启某些端口？

| 项目 | 端口 |
| ---- | ---- |
| node | 5601 |
| java | 9200 |
| java | 9300 |

#### 有没有CLI工具？

 有，通过elasticsearch-cli查看工具的说明

## 日志

- 2020-04-22完成CentOS安装研究


 **当前的elasticsearch在root用户目录下，需要把elasticsearch移动到非root用户目录中就可以了**