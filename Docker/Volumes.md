# Docker
## Volumes
### Configurando volumes

#### Bind Volume

Todos os dados do container serão salvos nesta pasta local. Para reutiliza-los basta criar outro container utilizando o mesmo volume. 

```
docker run -e MYSQL_ROOT_PASSWORD=<senha> --name <nome do container> -d -p <porta do servidor~>:<porta do container> mysql --volume=<pasta do servidor>:<pasta do container>
```

Exemplo:

```
docker run -e MYSQL_ROOT_PASSORD=password --name mysql-1 -d -p 3306:3306 mysql --volume=home/victor/data/mysql-1:/var/lib/mysql
```

Exemplo:
```
docker run --name apache-1 -d -p 80:80 --volume=/home/victor/data/apache-1:/usr/local/apache2/htdocs httpd
```

#### Named Volume

São volumes criados manualmente com o comando:

```
docker volume create <nome do volume>
```

Estes volumes são criados dentro de /var/lib/docker/volumes e podem ser referenciados utilizando o nome:

```
docker run -v <nome>:/<diretório do container> mysql
```

### Montando volumes

```
docker run -dti --mount type=<tipo de volume>,src=<pasta do volume>,dst=<destino do volume no container> <imagem>
```

Exemplo:

```
docker run -dti --mount type=bind,src=/home/victor/data/mysql-1,dst=/data mysql
```

Exemplo:
```
docker volume create data-debian-1

docker run -dti --name debian-1 --mount type=volume,src=data-debian-1,dst=/data debian
```


### Montando volumes somente de leitura

```
docker run -dti --mount type=<tipo de volume>,src=<pasta do volume>,dst=<destino do volume no container>,ro <imagem>
```

Exemplo:

```
docker run -dti --mount type=bind,src=/home/victor/data/mysql-1,dst=/data,ro mysql
```

### Listando os volumes 

```
docker volume ls
```

### Excluindo os volumes

```
docker volume rm <nome do volume>
```

Ou, para excluir todos os volumes:

```
docker volume prune
```