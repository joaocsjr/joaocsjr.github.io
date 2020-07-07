# Docker Basico




### Instalação 
``` bash


 curl -fsSL https://get.docker.com/ | bash
 docker version
 docker container ls

```




### comandos docker registry e dockerhub
 - Comandos Utilizados:

``` bash



 docker image inspect debian
 docker history linuxtips/apache:1.0
 docker login
 docker login registry.suaempresa.com
 docker push linuxtips/apache:1.0
 docker pull linuxtips/apache:1.0
 docker image ls

 # criando registry local
 docker container run -d -p 5000:5000 --restart=always --name registry registry:2

 # tag na imagem
 docker tag IMAGEMID localhost:5000/apache
```




### Gerenciamento de Volumes

``` bash

 docker container run -ti --mount type=bind,src=/volume,dst=/volume ubuntu
 docker container run -ti --mount type=bind,src=/root/primeiro_container,dst=/volume ubuntu
 docker container run -ti --mount type=bind,src=/root/primeiro_container,dst=/volume,ro ubuntu
 docker volume create giropops
 docker volume rm giropops
 docker volume inspect giropops
 docker volume prune
 docker container run -d --mount type=volume,source=giropops,destination=/var/opa  nginx
 docker container create -v /data --name dbdados centos
 docker run -d -p 5432:5432 --name pgsql1 --volumes-from dbdados -e POSTGRESQL_USER=docker -e POSTGRESQL_PASS=docker -e POSTGRESQL_DB=docker kamui/postgresql
 docker run -d -p 5433:5432 --name pgsql2 --volumes-from dbdados -e  POSTGRESQL_USER=docker -e POSTGRESQL_PASS=docker -e POSTGRESQL_DB=docker kamui/postgresql
 docker run -ti --volumes-from dbdados -v $(pwd):/backup debian tar -cvf /backup/backup.tar /data

```



### DockerFile Exemplos

``` yaml

FROM debian

RUN apt-get update && apt-get install -y apache2 && apt-get clean
ENV APACHE_LOCK_DIR="/var/lock"
ENV APACHE_PID_FILE="/var/run/apache2.pid"
ENV APACHE_RUN_USER="www-data"
ENV APACHE_RUN_GROUP="www-data"
ENV APACHE_LOG_DIR="/var/log/apache2"

LABEL description="Webserver"

VOLUME /var/www/html/
EXPOSE 80
```


``` yaml
FROM debian

RUN apt-get update && apt-get install -y apache2 && apt-get clean
ENV APACHE_LOCK_DIR="/var/lock"
ENV APACHE_PID_FILE="/var/run/apache2/apache2.pid"
ENV APACHE_RUN_USER="www-data"
ENV APACHE_RUN_DIR="/var/run/apache2"
ENV APACHE_RUN_GROUP="www-data"
ENV APACHE_LOG_DIR="/var/log/apache2"

LABEL description="Webserver"

VOLUME /var/www/html/
EXPOSE 80

ENTRYPOINT ["/usr/sbin/apachectl"]
CMD ["-D", "FOREGROUND"]

```

``` yaml
FROM golang

WORKDIR /app
ADD . /app
RUN go build -o goapp
ENTRYPOINT ./goapp
```

``` yaml
FROM golang AS buildando

ADD . /src
WORKDIR /src
RUN go build -o goapp


FROM alpine:3.1

WORKDIR /app
COPY --from=buildando /src/goapp /app
ENTRYPOINT ./goapp
```





### Comando usandos no dockerfile

``` html
ADD => Copia novos arquivos, diretórios, arquivos TAR ou arquivos remotos e os adicionam ao filesystem do container;

CMD => Executa um comando, diferente do RUN que executa o comando no momento em que está "buildando" a imagem, o CMD executa no início da execução do container;

LABEL => Adiciona metadados a imagem como versão, descrição e fabricante;

COPY => Copia novos arquivos e diretórios e os adicionam ao filesystem do container;

ENTRYPOINT => Permite você configurar um container para rodar um executável, e quando esse executável for finalizado, o container também será;

ENV => Informa variáveis de ambiente ao container;

EXPOSE => Informa qual porta o container estará ouvindo;

FROM => Indica qual imagem será utilizada como base, ela precisa ser a primeira linha do Dockerfile;

MAINTAINER => Autor da imagem; 

RUN => Executa qualquer comando em uma nova camada no topo da imagem e "commita" as alterações. Essas alterações você poderá utilizar nas próximas instruções de seu Dockerfile;

USER => Determina qual o usuário será utilizado na imagem. Por default é o root;

VOLUME => Permite a criação de um ponto de montagem no container;

WORKDIR => Responsável por mudar do diretório / (raiz) para o especificado nele;

```



# Docker machine 

- Cria vm com o docker instalado, existem varios drivers para hypervisor e clouds


- Para fazer a instalação do Docker Machine no Linux, faça:

``` bash
 curl -L https://github.com/docker/machine/releases/download/v0.16.1
/docker-machine-`uname -s`-`uname -m` >/tmp/docker-machine
 chmod +x /tmp/docker-machine 
 sudo cp /tmp/docker-machine /usr/local/bin/docker-machine


Para seguir com a instalação no macOS:

 curl -L https://github.com/docker/machine/releases/download/v0.16.1
/docker-machine-`uname -s`-`uname -m` >/usr/local/bin/docker-machine 
 chmod +x /usr/local/bin/docker-machine

#Para seguir com a instalação no Windows caso esteja usando o Git bash:

 if [[ ! -d "$HOME/bin" ]]; then mkdir -p "$HOME/bin"; fi
 curl -L https://github.com/docker/machine/releases/download/v0.16.1
/docker-machine-Windows-x86_64.exe > "$HOME/bin/docker-machine.exe"
chmod +x "$HOME/bin/docker-machine.exe"


 #Para verificar se ele foi instalado e qual a sua versão, faça:

 docker-machine version
 docker-machine create --driver virtualbox linuxtips

 docker-machine ls

 docker-machine env linuxtips

 eval "$(docker-machine env linuxtips)"

 docker container ls

 docker container run busybox echo "LINUXTIPS, VAIIII"
 docker-machine ip linuxtips

 docker-machine ssh linuxtips

 docker-machine inspect linuxtips

 docker-machine stop linuxtips

 docker-machine ls 

 docker-machine start linuxtips

 docker-machine rm linuxtips

 eval $(docker-machine env -u)

```
# Secrets 

- Usado para armazenar informações senssiveis como senhas e usuarios para serem manipulados no container


``` bash

# criando arquivo de senha 
echo 'minha secret' | docker secret create 

docker secret create minha_secret minha_secret.txt

docker secret inspect minha_secret
docker secret ls

docker secret rm minha_secret
#criando serviço e consumindo secret 
docker service create --name app --detach=false --secret db_pass  minha_app:1.0

docker service create --detach=false --name app --secret source=db_pass,target=password,uid=2000,gid=3000,mode=0400 minha_app:1.0

ls -lhart /run/secrets/

docker service update --secret-rm db_pass --detach=false --secret-add source=db_pass_1,target=password app
``` 




