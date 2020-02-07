# Install winlogbeat on windows

```
https://artifacts.elastic.co/downloads/beats/winlogbeat/winlogbeat-5.6.3-windows-x86_64.zip

Extract into c://program files

```


```
open  
vi winlogbeat.yml
tags: ["ap-southeast-1"]
fields:
globo_environment: production

* Comment the elasticsearch all lines 

#----------------------------- Logstash output --------------------------------
output.logstash:
# The Logstash hosts
hosts: ["13.229.50.243:5044"]

:wq!
```


```
From powershell install winlogbeat template by using following command
open "power shell as addmin
cd /program files/winlogbeat


Invoke-WebRequest -Method Put -InFile winlogbeat.template.json -Uri  http://54.255.170.251:9200/_template/winlogbeat?pretty -ContentType application/json


From Powershell install winlogbeat service using following command .\install-service-winlogbeat.ps1

Start service 

by using go to start to service then
select "winlogbeat" click on start.

```

```
In kibana

http://54.169.238.188:5601

we have to create pattern "winlogbeat-*" by timestap@

 Then,Create

* Discover
* Visualization
* Dash board



```


[Winlogbeats Refs Link ](https://www.elastic.co/guide/en/beats/winlogbeat/1.1/winlogbeat-installation.html)