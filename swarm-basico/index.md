# Swarm Basico



# Docker swarm

- Nativo no docker concorrente do kubernetes é dividido em 2 funções:
    - ***Manager :*** Gerenciamento do cluster
        - Necessario criar HA do manager 
        - sempre impar 51% de recursos minimo pra manter o cluster no ar 
        - sao diferenciados pelo token quando e feito o join no cluster
        

    - ***Worker :*** execução do container
        - E possivel colocar em modo manutencao similar esxi
        - Quando o host retorna ao cluster o containers nao sao executados novamente, necessario usar o comando de scale para distribuir a carga novamente

- ***Service:***
    - modos : 
        replicated



### Criando cluster Swarm

``` bash
docker node update --availability 
  #inicia o cluster 
  docker swarm init

  #inclui nodes no cluster
  docker swarm join --token \ SWMTKN-1-100_SEU_TOKEN SEU_IP_MASTER:2377


# lista os nodes 
 docker node ls

  
 # exibe o token
  docker swarm join-token manager

  docker swarm join-token worker

```
### Gerenciando cluster Swarm

```bash
#info sobre os nodes
  docker node inspect LINUXtips-02

# promove o node para manager
  docker node promote LINUXtips-03
# despromove o node
  docker node demote LINUXtips-03

# remove node do clsuter 
  docker swarm leave
# --force
  docker swarm leave --force


# deleta o node do cluster
  docker node rm LINUXtips-03
``` 

### Criando e Gerenciando service 

```bash
# cria serviço com o nome de webserver com 5 replicas usando a imagem do ngnix 
  docker service create --name webserver --replicas 5 -p 8080:80  nginx

# testar se o serviço esta no ar
  curl QUALQUER_IP_NODES_CLUSTER:8080

# lista o serviço
  docker service ls

# lista info em formato mais amigavel 
 docker service inspect www --pretty

# lita aonde os services estão rodando 
  docker service ps webserver

# info detalhadas dos service 
  docker service inspect webserver


# tail -f nos logs dos containers 
  docker service logs -f webserver

# remove o serviço
  docker service rm webserver

#cria service com mount de volume externo
  docker service create --name webserver --replicas 5 -p 8080:80 --mount type=volume,src=teste,dst=/app  nginx

  docker network create -d overlay giropops

  docker network ls

  docker network inspect giropops

  docker service scale giropops=5

  docker network rm giropops

  docker service create --name webserver --network giropops --replicas 5 -p 8080:80 --mount type=volume,src=teste,dst=/app  nginx

  docker service update <OPCOES> <Nome_Service> 
```

