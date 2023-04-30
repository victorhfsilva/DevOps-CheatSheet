# Docker

## Dockerfile

O Dockerfile é um arquivo de texto que contém um conjunto de instruções para construir uma imagem Docker. É usado para automatizar o processo de criação de imagens Docker, definindo os componentes e configurações da imagem de forma repetível e consistente.

### Construindo uma imagem

```
docker build <caminho do Dockerfile> -t <nome da imagem>
```

Exemplo:

```
docker build /home/victor/ubuntu-python/ -t ubuntu-python
```
**O nome da imagem deve ser Dockerfile caso deseja-se que ela seja executada sem explicitar o arquivo.*

### Exemplos de Dockerfiles

#### Ubuntu com um aplicativo python

```
FROM ubuntu

RUN apt update && apt install -y python3 && apt clean

COPY app.py /opt/app.py

CMD python3 /opt/app.py
```
Neste caso o arquivo app.py está no diretório do Dockerfile.

#### Debian com Apache

```
RUN apt-get update && apt-get install apache2 -y && apt-get clean

ENV APACHE_LOCK DIR=*var/lock*
ENV APACHE_PID_FILE="var/run/apache2.pid"
ENV APACHE_RUN_UER="www-data"
ENV APACHE_RUN_GROUP="www-data"
ENV APACHE_LOG_DIR="/var/log/apache2"

ADD site.tar /var/www/html

LABEL description = "Apache webserver 1.0"

VOLUME /var/www/html

EXPOSE 80

ENTRYPOINT ["/usr/sbin/apachectl"]

CMD ["-D", "FOREGROUND"]
```

Para construir a imagem:

```
docker image build . -t debian-apache:1.0
```

Para executar:

```
docker run -dti -p 80:80 --name apache-A debian-apache:1.0
```

#### Imagem de uma linguagem de Programação

##### Python

```
FROM python

WORKDIR /opt/app

COPY app.py /opt/app/app.py

CMD ["python", "./app.py"]
```

### Dockerfile Multi Estágio

#### Golang sobre Alpine

```
FROM golang as exec

COPY app.go /go/src/app/

ENV GO111MODULE=auto

WORKDIR /go/src/app/

RUN go build -o app.go .

FROM alpine

WORKDIR /appexec

COPY --from=exec /go/src/app /appexec

RUN chmod -R 755 /appexec

ENTRYPOINT ./app.go
```

