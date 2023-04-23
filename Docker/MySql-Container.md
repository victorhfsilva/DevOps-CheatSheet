# Docker
## MySql Container

### Instalação

```
docker pull mysql
```

### Executando a Imagem

```
docker run -e MYSQL_ROOT_PASSWORD=<senha> --name <nome do container> -d -p <porta do servidor~>:<porta do container> mysql
```

Exemplo:
```
docker run -e MYSQL_ROOT_PASSORD=password --name mysql-1 -d -p 3306:3306 mysql
```

### Executando o MySQL

```
mysql -u root -p --protocol=tcp
```


### Acessando de fora do container

Instalando o MySQL Client é possível acessar o MySql de fora do container.

```
sudo apt install mysql-client
```

