


![ELK](images/ELK.png)




# ElasticSearch
* Elasticsearch is a search engine based on the Lucene library.
* It provides a distributed, multitenant-capable full-text search engine  with an HTTP web interface and schema-free JSON documents. 
* Elasticsearch is developed in Java. 
* Following an open-core business model, parts of the software are licensed 
* Elasticsearch is the most popular enterprise search engine followed by Apache Solr, also based on Lucene.




## Installing ElasticSearch

```
Lunch the ubuntu 16 Server with 4gb ram,EIP. 

# apt-get update
# apt-get install openjdk-8-jre-headless
# wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-5.6.3.deb 
# dpkg -i elasticsearch-5.6.3.deb

```





```
open "vi /etc/elasticsearch/elasticsearch.yml"file, change as below. 

      cluster.name :  appworks-clustering
      Node.name : public DNS of Elasticsearch 
      Network.host :  private ip of elasticsearch
:wq!
```

```
For increase the memory map count by  
# sysctl -w vm.max_map_count=262144

Restart elasticsearch  services by

# service elasticsearch start 
      
To test elasticsearch by executing in browser

      http://<public ipadress>:9200 

* SG allow All traffic 
By default elasticsearch runs on port 9200


```




[Electic stack doc](https://www.elastic.co/products/)

[Elestic search refs   Link](https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html)