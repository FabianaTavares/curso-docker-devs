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