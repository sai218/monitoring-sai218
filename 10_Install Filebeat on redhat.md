# Install Filebeat on redhat

```
Lunch redhat instance 
# curl -L -O https://artifacts.elastic.co/downloads/beats/filebeat/filebeat-5.6.4-x86_64.rpm

# sudo rpm -vi filebeat-5.6.4-x86_64.rpm
# cd /etc/filebeat/

```

```
open
# vi filebeat.yml

tags: ["ap-southeast-1"]
fields:
globo_environment: production 
* comment all elestic search line.

#----------------------------- Logstash output --------------------------------
output.logstash:
# The Logstash hosts
hosts: ["13.229.50.243:5044"]

:wq!

```

```
# cd /etc/filebeat/


curl -H 'Content-Type: application/json' -XPUT 'http://52.221.196.45:9200/_template/filebeat' -d@/etc/filebeat/filebeat.template.json

# sudo /etc/init.d/filebeat start


```


```

In kibana

http://54.169.238.188:5601

we have to create pattern "filebeat-*" by timestap@

 Then,Create

* Discover
* Visualization
* Dash board
```

[FileBeat Refs Link](https://www.elastic.co/guide/en/beats/filebeat/5.1/filebeat-installation.html)