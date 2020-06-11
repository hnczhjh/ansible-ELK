# Troubleshooting

We collect the most common troubleshooting of using Elasticsearch for your reference:

> Instance troubleshooting is closely related to the Instance provider that is Cloud Platform, refer to [Cloud Platform Documentation](https://support.websoft9.com/docs/faq/tech-instance.html)

#### How can I use the logs?

You can find the keywords **Failed** or **error** from the logs directory: `/data/logs`

#### Elasticsearch service can't start?

Insufficient disk space, insufficient memory, and configuration file errors can make service could not be started  

It is recommended to first check through the command.

```shell
# restart Elasticsearch service
systemctl status elasticsearch
journalctl -u elasticsearch

# view disk space
df -lh

# view memory rate
free -lh
```

#### Error in Chrome when modify password?

This error is not attribute to Elasticsearch server, once you have upgraded you local Chrome, it solved

![chrome error of Elasticsearch](https://libs.websoft9.com/Websoft9/DocsPicture/zh/elasticsearch/elasticsearch-chromeerror-websoft9.png)
