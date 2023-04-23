# Docker

## Comandos Básicos

### Instalando uma imagem

```
docker pull <imagem>
```

### Executando uma imagem

```
docker run <imagem>
```

#### Executando por determinado tempo

```
docker run <imagem> sleep <tempo em segundos>
```

#### Executando um tty da imagem

```
docker run --interactive --tty <imagem>

or 

docker run -ti <imagem>
```

#### Executando o container no background

```
docker run -dti <imagem>
```
-d stands for --detach* 
#### Nomeando a execução

```
docker run --name <nome> <imagem>
```

### Executando um programa dentro do container
```
docker exec -it <container id> <caminho do programa ou comando>
```

Exemplo:
```
docker exec -it fdbbadb85b1e /bin/bash
```

Exemplo:
```
docker exec -it ubuntu-1 echo Hello World
```
### Informações
#### Mostrando os containers em execução

```
docker ps
```

#### Mostra histórico de execução dos containers

```
docker ps -a
```

#### Mostrando informações do docker

```
docker info
```

#### Mostrando os logs de um container

```
docker container logs <container>
```
 
#### Mostrando os processos dentro de um container

```
docker container top <container>
```
### Copiando arquivos entre o container e o hospedeiro

#### Copiando arquivos para o container

```
docker cp <arquivo> <container>:<caminho>
```
Exemplo:
```
docker cp arquivo.txt ubuntu-1:/home
```

#### Copiando arquivos do container

```
docker cp <container>:<arquivo> <caminho>
```

### Parando a execução de um container

```
docker stop <container id or name>
```

### Deletando um container

```
docker rm <container id or name>
```

Para excluir todos os containers:

```
docker container prune
```

### Deletando imagem

Antes de executar este comando é necessário parar e excluir todos seus containers.

```
docker rmi <imagem>
```

### Recursos do Container

#### Consultando os Recursos

```
docker stats <nome do container>
```

#### Limitando os recursos

```
docker update <container> -m <memória> --cpus <porcentagem de processamento>
```

Exemplo:

```
docker update apache-1 --memory=128m --memory-swap=256m --cpus 0.2
```
