# httpapi-poc

> THIS SHOULD AND WILL NOT WORK AS A PRODUCTION READY ENVIRONMENT

## Prerequisites

* Docker
* Browser

## Zabbix environment with docker for testing

### Idea

The idea is to provide an local zabbix environment to test and prove the new ideas around httpapi implementation.
There are 3 ways to access the Zabbix Web - one direct and two over Traefik. The direct way over Port 8080 should be taken
to go around the access counts from traefik. Port 80 through traefik will count the access request and this way the
reduces api-calls from httpapi can be prooved. Port 81 with basic auth is the prove to show that httpapi calls work this way too.

### Start/Stop with docker

```bash

cd zabbix-environment

# Start environment
docker-compose up -d

# stop environment
docker-compose down 

# remove/clear environment
docker-compose down --remove-orphans --volumes

```

### Ports

* traefik
** Port: 80 = Zabbix Web
** Port: 81 = traefik API

* Zabbix Web (nginx)
** Port: 8080 = direct port without traefik
** Port: 8443 = direct port without traefik

* Zabbix Server
** Port: 10051

* Zabbix Proxy
** Port: 10061

* Zabbix Agent
** Port: 10050

* Zabbix Web Service
** Port: 10053

* PSQL / Timescale
** Port: not exposed

### Quick links

* Traefik Dashboard - http://localhost:89
* Traefik Metrics - http://localhost:89/metrics
* Zabbix Web (no traefik) - http://localhost:8080
* Zabbix Web (with traefik) - http://localhost
* Zabbix Web (with traefik & basic auth) - http://localhost:81
