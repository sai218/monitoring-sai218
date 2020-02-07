# Kibana

```
Lunch instance of Ubuntu 16.04 2gb ram
# apt-get update
# wget -qO - https://packages.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
# echo "deb https://artifacts.elastic.co/packages/5.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elasticsearch-5.x.list
# apt-get update
# apt-get install kibana

```

```
Open 
# vi /etc/kibana/kibana.yml
server.host: private <ipaddress> of kibina
server.name: private <hostname> of kibina
elasticsearch.url: <elasticsearchurl> of  electric search of public ip
:wq!
```

```
# service kibana start
http:// <kinba public ip>:5601 

```

[Kibana Refs Link](https://www.elastic.co/guide/en/kibana/current/install.html)