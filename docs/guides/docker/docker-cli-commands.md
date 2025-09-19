# Guia de Comandos Essenciais do Docker CLI

Este guia apresenta uma lista dos comandos mais comuns do Docker, organizados por categoria para facilitar a consulta e o aprendizado.

## Gerenciamento de Imagens

Comandos para construir, baixar, listar e remover imagens Docker.

- **`docker build`**: Constrói uma imagem a partir de um Dockerfile.

  ```bash
  # Constrói uma imagem a partir do Dockerfile no diretório atual e a nomeia (tag) como 'minha-imagem'
  docker build -t minha-imagem .
  ```

- **`docker images`**: Lista todas as imagens Docker locais.

  ```bash
  docker images
  ```

- **`docker pull`**: Baixa uma imagem ou um repositório de um registro (como o Docker Hub).

  ```bash
  # Baixa a versão mais recente (latest) da imagem do Ubuntu
  docker pull ubuntu:latest
  ```

- **`docker push`**: Envia uma imagem ou um repositório para um registro.

  ```bash
  # Envia a imagem 'meu-usuario/minha-imagem' para o Docker Hub
  docker push meu-usuario/minha-imagem
  ```

- **`docker rmi`**: Remove uma ou mais imagens locais.

  ```bash
  # Remove a imagem com o ID especificado
  docker rmi <ID_DA_IMAGEM>
  ```

- **`docker tag`**: Cria uma tag que referencia uma imagem existente. Útil para nomear versões ou preparar para o push.

  ```bash
  # Adiciona a tag 'meu-usuario/minha-imagem:v1' à imagem 'minha-imagem:latest'
  docker tag minha-imagem:latest meu-usuario/minha-imagem:v1
  ```

## Gerenciamento de Contêineres

Comandos para criar, executar, parar, listar e interagir com contêineres.

- **`docker run`**: Cria e inicia um novo contêiner a partir de uma imagem.

  ```bash
  # Executa um contêiner em segundo plano (-d), mapeia a porta 8080 do host para a 80 do contêiner (-p) e o nomeia como 'meu-app'
  docker run -d -p 8080:80 --name meu-app nginx
  ```

- **`docker ps`**: Lista os contêineres em execução.

  ```bash
  # Lista todos os contêineres (em execução e parados)
  docker ps -a
  ```

- **`docker stop`**: Para um ou mais contêineres em execução.

  ```bash
  # Para o contêiner chamado 'meu-app'
  docker stop meu-app
  ```

- **`docker start`**: Inicia um ou mais contêineres parados.

  ```bash
  # Inicia o contêiner chamado 'meu-app'
  docker start meu-app
  ```

- **`docker restart`**: Reinicia um contêiner.

  ```bash
  docker restart meu-app
  ```

- **`docker rm`**: Remove um ou mais contêineres.

  ```bash
  # Remove o contêiner com o ID especificado (deve estar parado)
  docker rm <ID_DO_CONTÊINER>

  # Força a remoção de um contêiner em execução
  docker rm -f <ID_DO_CONTÊINER>
  ```

- **`docker logs`**: Exibe os logs de um contêiner.

  ```bash
  # Exibe os logs do contêiner 'meu-app' e continua mostrando novas saídas (-f)
  docker logs -f meu-app
  ```

- **`docker exec`**: Executa um comando dentro de um contêiner em execução.
  
  ```bash
  # Abre um shell interativo (-it) dentro do contêiner 'meu-app'
  docker exec -it meu-app /bin/bash
  ```

## Gerenciamento de Redes

Comandos para gerenciar as redes do Docker.

- **`docker network ls`**: Lista as redes.
- **`docker network create`**: Cria uma nova rede.
- **`docker network inspect`**: Exibe informações detalhadas sobre uma ou mais redes.
- **`docker network rm`**: Remove uma ou mais redes.
- **`docker network connect`**: Conecta um contêiner a uma rede.
- **`docker network disconnect`**: Desconecta um contêiner de uma rede.

## Gerenciamento de Volumes

Comandos para gerenciar volumes de dados.

- **`docker volume ls`**: Lista os volumes.
- **`docker volume create`**: Cria um novo volume.
- **`docker volume inspect`**: Exibe informações detalhadas sobre um ou mais volumes.
- **`docker volume rm`**: Remove um ou mais volumes.

## Limpeza do Sistema

Comandos para limpar recursos não utilizados.

- **`docker system prune`**: Remove todos os contêineres parados, redes não utilizadas, imagens pendentes (dangling) e cache de build.

```bash
# Remove recursos não utilizados
docker system prune

# Remove também todos os volumes não utilizados
docker system prune --volumes

# Remove tudo, incluindo imagens não utilizadas (não apenas as pendentes)
docker system prune -a
```

## Docker Hub / Registry

Comandos para interagir com registros de imagens.

- **`docker login`**: Autentica em um registro Docker.
- **`docker logout`**: Desconecta de um registro Docker.