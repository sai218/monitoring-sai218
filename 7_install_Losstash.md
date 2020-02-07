

# Install Logstash

```
Lunch instant of Ubuntu 16.04 4gb ram
# apt-get update
# apt-get install openjdk-8-jre-headless
# wget -qO - https://packages.elastic.co/GPG-KEY-elasticsearch | sudo apt-key add -
# echo "deb https://artifacts.elastic.co/packages/5.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elasticsearch-5.x.list
# apt-get update && apt-get install logstash
# cd /usr/share/logstash 
Now execute below command and enter some value
# bin/logstash -e "input { stdin {} } output { stdout {} }" enter some value.

```

```
# service logstash status
# cd /etc/logstash/conf.d


# vi beats.conf
input {
   beats {
       port => "5044"
   }
}
output {
   elasticsearch {
       hosts => [ "54.255.170.251:9200" ]
       index => "%{[@metadata][beat]}-%{+YYYY.MM.dd}"
       document_type => "%{[@metadata][type]}"
   }
}

:wq!
```



```
# service logstash start
# cd /usr/share/logstash
# bin/logstash -f /etc/logstash/conf.d/

```

[Logstash refs Link](https://www.elastic.co/guide/en/logstash/current/installing-logstash.html)