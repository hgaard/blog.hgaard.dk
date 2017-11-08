+++
author = "Jakob Højgaard"
date = 0001-01-01T00:00:00Z
description = ""
draft = true
slug = "untitled"
title = "(Untitled)"

+++

## The case was on win 7

## SQL server

* install Docker toolbox
* create a new docker machine w enough memory for sql server (3.2)

Delete default

```
docker-machine rm default
```
Create new (remember proxy settings)

```
docker-machine create -d virtualbox --virtualbox-cpu-count=2 --virtualbox-memory=4096 --engine-env HTTP_PROXY=http://172.29.32.10:8080/  --engine-env HTTPS_PROXY=https://172.29.32.10:8080/ default
```

check end in machine

```docker 
docker-machine env default
```

restart docker machine

Run latest sql server

```
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=yourStrong(!)Password' -p 1433:1433 -d microsoft/mssql-server-linux:2017-latest
```

connect from teaminal

```
sqlcmd -S localhost -U SA -P 'yourStrong(!)Password'
```

```
docker exec -it aefe29c5ce3d /opt/mssql-tools/bin/sqlcmd -S localhost -U sa -P yourStrong(!)Password
```