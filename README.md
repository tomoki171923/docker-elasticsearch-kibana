# docker elasticstack

## Version 

Elastic Search : 7.6.2

Kibana : 7.6.2

APM Server : 7.6.2


## Start

~~~
docker-compose up -d
~~~

(it'll take some time.)

access http://localhost:5601/app/kibana

login

Username : esroot
Password : esroot123

## Stop

~~~
docker-compose down
~~~

## APM server

if you use the apm , set the following param in your apm agents.

~~~
server_url: 'http://apm-server:8200'
~~~
