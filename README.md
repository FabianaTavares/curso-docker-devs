# Docker para Desenvolvedores (com Docker Swarm e Kubernetes)
![GitHub Workflow Status](https://github.com/FabianaTavares/curso-docker-devs/workflows/Gerador%20de%20CHANGELOG/badge.svg)
![GitHub package.json version (subfolder of monorepo)](https://img.shields.io/github/package-json/v/FabianaTavares/curso-docker-devs?color=blue)

Curso Docker para Desenvolvedores (com Docker Swarm e Kubernetes) criado pelo Matheus Battisti, na plataforma Udemy. 2023

## Comandos utilizados ao longo do projeto.

### Seção 1 - Introdução

1. Instalação do Docker Desktop.
2. Verificar versão instalada:

```
docker version
```

3. Para rodar containers utilize:

```
docker run
```

### Seção 2 - Trabalhando com Containers

1. Executar uma imagem em um container:

```
docker run <imagem>
```

2. Verificar containers criado:

```
docker ps
```

3. Parar um container:

```
docker stop <id ou nome>
```

4. Remover um container:

```
docker -rm <id> -f (force)
```

5. Iniciar um container:

```
docker start <id ou nome>
```

6. Definir nome para um container:

```
docker run -d -p 80:80 --name <nome_desejado> nginx (apenas exemplo)
```

7. Acessar logs de um container:

```
docker logs <id>
```

### Seção 3 - Criando imagens e avançando em Containers

1. Fazer o build de uma imagem:

```
docker build <diretório da imagem>
```

2. Executar uma imagem:

```
docker run <imagem>
```

3. Verificar opções diponíveis de comandos:

```
docker run --help
```

4. Nomeando imagens:

```
docker tag <name>
```

```
docker tag <name>:<tag>
```

5. Removendo imagens:

```
docker rmi <imagem> -f (force)
```

6. Enviando imagens para o Hub:

```
docker push <imagem>
```

### Seção 4 - Introduzindo volumes aos nossos containers

1. Criar volumes nomeados:

```
docker run -v nomedovolume:/data
```

2. Verificar volumes nomeados criados:

```
docker volume ls
```

3. Bind mount:

```
docker run /dir/data:/data
```

4. Inspecionar Volumes:

```
docker volume inspect <nome>
```

5. Removendo Volumes:

```
docker volume rm <nome>
```

6. Removendo Volumes em massa (prune), serve também para imagens e containers:

```
docker volume prune
```

7. Volume com permissão apenas de leitura:

```
docker run -v volume:/data:ro
```

### Seção 5 - Conectando containers com Networks

1. Listando networks:

```
docker network ls
```

2. Criando networks:

```
docker network create <nome>
```

3. Removendo networks:

```
docker network rm <nome>
```

4. networks externos:

```
docker run -d -p 5000:5000 --name <nomecontainer> --rm <name>
```

5. networks maquina host:

```
docker run -d -p 5000:5000 --name <nomecontainer> --rm <namehost>
```

6. conexao entre containers:

```
docker network create <nome>
```

```
docker run -d -p 3306:3306 --name <nomedocontainer> --rm --network <nomedared> -e <variaveldeambiente> = True <nomedaimagemderede>
```

7. conexao entre um container e uma rede:

```
docker network connect <rede> <container>
```

8. Desconectar um container da rede:

```
docker network disconnect <rede> <container>
```

9. Inspecionando networks:

```
docker network inspect <nomedarede>
```


### Seção 7 - Gerenciando múltiplos containers com Docker Compose

1. Rodando o Compose:

```
docker-compose up
```

2. Rodando o Compose em background:

```
docker-compose up -d
```


3. Parando o Compose:

```
docker-compose down
```

4. Verificando serviços do Compose:

```
docker-compose ps
```

### Seção 8 - Docker Swarm para orquestração

1. Inicializando o Swarm

```
docker swarm init
```

2. Listando todos os Nodes

```
docker node ls
```

3. Adicionando máquinas no Swarm

```
docker swarm join --token <TOKEN><IP>:<PORTA>
```

4. Subindo serviço no Swarm

```
docker service create --name <nome> <imagem>
```

5. Verificando serviços rodando no Swarm

```
docker service ls
```

6. Removendo serviços

```
docker service rm <nome>
```

7. Replicando serviços

```
docker service create --name <nome> --replicas <NUMERO> </NUMERO><imagem>
```

8. Deixar o Swarm em um Node

```
docker swarm leave
```

9. Removendo um Node

```
docker node rm <ID>
```

10. Inspecionando serviços

```
docker service inspect <ID>
```

11. Verificar quais containers estão rodando

```
docker service ps <ID>
```

12. Atualizando um imagem no Swarm

```
docker service update --image <imagem> <SERVICO>
```

13. Criando redes para serviços do Swarm

```
docker network create --network <REDE>
```

14. Conectando serviços a uma rede já existente

```
docker service update --network <REDE> <nome>
```

### Seção 9 - Orquestração com Kubernetes

1. Inicializando o Minikube

```
minikube start --driver=<DRIVER>
```

2. Parando o Minikube

```
minikube stop --driver=<DRIVER>
```

3. Acessando o Dashboard

```
minikube dashboard OU minikube dashboard --url
```

4. Criando Deployment

```
kubectl create deployment <NOME> --image=<IMAGE>
```

5. Verificando Deployment

```
kubectl get deployments ou kubectl describe deployments
```

6. Criando um service

```
kubectl expose deployment <NOME> --type=<TIPO> --port=<PORT>
```

7. Gerando um IP para o Service

```
minikube service <NOME>
```

8. Detalhes dos Services

```
kubectl get services
```

9. Replicando aplicação

```
kubectl scale deployment/<NOME> --replicas=<NUMERO>
```

10. Verificando número de réplicas

```
kubectl get rs
```

11. Diminuindo o número de réplicas

```
kubectl scale deployment/<NOME> --replicas=<NUMERO_MENOR>
```

12. Atualizando a imagem do projeto

```
kubectl set image deployment/<NOME> <NOME_CONTAINER>=<NOVA_IMAGEM>
```

12. Desfazer alterações de Projeto

```
kubectl rollout status deployment/<NOME>
```

13. Deletando Services

```
minikube delete service <NOME>
```

14. Deletando Deployments

```
minikube delete deployment <NOME>
```

15. Parando o deployment

```
minikube delete -f <ARQUIVO>
```

16. Iniciando o Serviço

```
minikube apply -f <ARQUIVO>
```

```
minikube service <NOME>
```

17. Parando o Serviço

```
minikube delete -f <ARQUIVO>
```

