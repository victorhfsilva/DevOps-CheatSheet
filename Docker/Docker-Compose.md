# Docker 

## Docker Compose

Ajuda a definir e compartilhar aplicativos com vários containers.

* Prieramente é necessário criar um arquivo, docker-compose.yml.

### Exemplos

#### MySQL Adminer

```
version: "3.8"

services:

	mysqlsrv:
		image: mysql:5.7
		environment: 
		MYSQL_ROOT_PASSWORD:"password123"
		MYSQL_DATABASE: "dio"
		ports:
			- "3306:3306"
		volumes:
			- /home/victor/data/mysql-2:/var/lib/mysql
		networks:
			- minha-rede
			
	adminer:
		image: adminer
		ports: 
			- "8080:8080"
		networks:
			- minha-rede
			
networks:
	minha-rede:
		driver: bridge
```

Para executar o container:
```
docker-compose up -d
```

Para parar a execução:

```
docker-compose down
```


