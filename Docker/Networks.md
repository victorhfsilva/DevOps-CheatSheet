# Docker

## Redes

### Listando Redes

```
docker network ls
```

### Inspecionando uma das redes

```
docker network inspect <rede>
```

Exemplo:

```
docker network inspect bridge
```

### Criando uma rede

```
docker network create <rede>
```

Exemplo:

```
docker network create home-lab
docker run -dti --name Ubuntu-A --network home-lab ubuntu
docker run -dti --name Ubuntu-B --network home-lab ubuntu
```

 