# Docker
Docker é uma tecnologia de software que fornece contêineres, promovido pela empresa Docker, Inc. O Docker fornece uma camada adicional de abstração e automação de virtualização de nível de sistema operacional no Windows e no Linux.

# Criando novas imagens em containers

### SQL Server 

#Criar container com SQL Server usuário SA
```
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=SQLServerP@$$' \
   -p 1433:1433 --name mssql2017 \
   -d microsoft/mssql-server-linux:2017-latest
```
#Alterar Senha SQL Server usuário SA

```
docker exec -it sql1 /opt/mssql-tools/bin/sqlcmd \
   -S localhost -U SA -P '<YourStrong!Passw0rd>' \
   -Q 'ALTER LOGIN SA WITH PASSWORD="SQLServerP@$$"'
```
#

### RabbitMQ
Repositório: https://hub.docker.com/_/rabbitmq/

#Levantando com usuário "guest" e senha padrão "guest"

```
docker run -d --hostname rabbitmq-server --name rabbitmq-server -p 8091:15672 -p 8090:5672 rabbitmq:3-management
```

#Versão alterando o usuário padrão
```
docker run -d -p 8090:5672 -p 8091:15672 --hostname rabbit-mq-server --name rabbit-mq-server rabbitmq:3.7-management -e RABBITMQ_DEFAULT_USER=admin -e RABBITMQ_DEFAULT_PASS=password rabbitmq:3.7-management
```

- Solução para resolver a conexão com o rabbitmq em um container docker
https://groups.google.com/forum/#!topic/masstransit-discuss/bvmHfka5TVk

> Problem solved...I was making two instances!

> For those who are interested by any chance, you need to expose both ports 5672 and 15672
  
```
docker run -d -p 8090:5672 -p 8091:15672 --hostname rabbitmq-server --name rabbitmq-server -e RABBITMQ_DEFAULT_USER=admin -e RABBITMQ_DEFAULT_PASS=password rabbitmq:3-management
```

# Comando para parar e remover todos containers docker

```
docker stop $(docker ps -a -q)
docker rm $(docker ps -a -q)
```


# VEJA TAMBÉM
## Cursos baratos!
- [Meus cursos](https://olha.la/udemy)

## Novidades, cupons de descontos e cursos gratuitos
https://olha.la/ilovecode-receber-cupons-novidades

