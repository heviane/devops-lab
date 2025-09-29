# Exercicios

## Comandos Básicos do Docker

```bash
# Lista todos os comandos do Docker
docker --help
docker container --help
docker run --help

# Baixa a imagem do Ubuntu no registro Docker Hub (repositório oficial)
# Quando não especificado a versão, o Docker baixa a mais recente (latest)
docker pull ubuntu

# Lista as imagens locais do Docker
docker images

# Executa uma imagem Docker no container
docker run ubuntu           ## sintaxe antiga
docker container run ubuntu ## sintaxe nova

# Lista os contêineres em execução e todos os contêineres
docker ps              ## sintaxe antiga
docker ps -a
docker container ls
docker container ls -a ## sintaxe nova

# Executa uma imagem Docker no container por 30 segundos
docker run ubuntu sleep 1500

# Para um contêiner em execução pelo ID ou NAME
docker stop <ID_DO_CONTÊINER> # Pode usar somente os 3 primeiros caracteres do ID
docker stop <NAME_DO_CONTÊINER>

# Executa uma imagem Docker no container de forma iterativa
# Isso permite executar comandos dentro do contêiner, neste caso, dentro do ubuntu
docker run -it ubuntu

    cat /etc/os-release # Verifica a versão do ubuntu
    exit # Sai do ubuntu

# Executa uma imagem Docker no container em segundo plano (background) - Retorna um ID do contêiner
docker run -dit ubuntu

# Executa um comando dentro de um contêiner em execução
docker exec -it <ID_DO_CONTÊINER> /bin/bash
docker exec -it <NAME_DO_CONTÊINER> /bin/bash
ls # lista os diretórios do ubuntu
```

## Instalar programas no Ubuntu

```bash
# Dentro de um contêiner Ubuntu, sempre atualize a lista de pacotes antes de instalar algo novo.
apt update

# Opcional: atualiza os pacotes já instalados para suas versões mais recentes.
apt upgrade -y

# Agora, instale os pacotes que desejar.
apt install -y nano
apt install -y zip

exit # Sai do ubuntu
```

## Copiar arquivos para dentro do Container

```bash
# Executa um contêiner em segundo plano (-d), e de forma iterativa (-it), nomeia como "ubuntu" usando a imagem "ubuntu:latest"
docker run -dit --name ubuntu ubuntu
docker ps

# Acessa o container e acessa o bash do "ubuntu"
docker exec -it ubuntu /bin/bash

    # Dentro do container, podemos criar um diretório
    mkdir /tests # Cria o diretório /tests
    ls           # Lista o conteúdo para confirmar
    exit         # Sai do container

# Também podemos criar o diretório diretamente do host
docker exec ubuntu mkdir /tests
docker exec ubuntu ls

# Copia um arquivo do seu computador (host) para dentro do contêiner.
# O caminho do host deve estar entre aspas se tiver espaços.
docker cp "test1.txt" ubuntu:/tests # De dentro do diretório onde estão os arquivos
docker cp "test/test2.txt" ubuntu:/tests # De fora do diretório onde estão os arquivos

## OUTPUT: Successfully copied 2.05kB to ubuntu:/tests

# Para verificar se o arquivo foi copiado, podemos listar o conteúdo do diretório /tests dentro do contêiner
docker exec ubuntu ls /tests
docker exec ubuntu ls /tests -l

    # Dentro do container, vamos zipar os arquivos enviados
    cd /tests
    zip myzip.zip *.txt # Cria o arquivo myzip.zip a partir de todos os .txt
    ls # Lista o conteúdo para confirmar
    exit # Sai do container
```

## Copiar arquivos de dentro do Container para o Host

```bash
# Copia o arquivo gerado para o diretório ATUAL no seu computador (host)
docker cp ubuntu:/tests/myzip.zip .

# Para copiar para um diretório específico (ex: uma pasta chamada "test"),
# primeiro, certifique-se que o diretório existe no seu host:
mkdir test

# Depois, execute o comando de cópia especificando o diretório de destino:
docker cp ubuntu:/tests/myzip.zip test/

    # Dentro do container, vamos extrair o zip
    cd /tests # Entra no diretório /tests
    rm text1.zip # Exclui o arquivo text1.zip se ele já existir
    rm text2.zip # Exclui o arquivo text2.zip se ele já existir
    unzip myzip.zip # Extrai o arquivo myzip.zip para dentro do diretório atual
    ls # Lista o conteúdo para confirmar
    exit # Sai do container
```

## Executar comtainer com MySQL

Será necessário a utilização de algumas variáveis de ambiente para passar por parametro:

```bash
# Lista as imagens locais do Docker
docker images

# Executa uma imagem Docker no container
docker run -e MYSQL_ROOT_PASSWORD=123456 --name mysql -d -p 3306:3306 mysql

## -e para definir uma variável de ambiente.
## --name para nomear o container.
## -d para executar em background.
## -p para definir o mapeamento das portas do host e do container

docker ps

# Acessa o container e acessa o bash do "mysql"
docker exec -it mysql bash

    # Executar o banco de dados MySQL dentro do container
    mysql -u root -p --protocol=tcp

    # Executar comandos sql dentro do banco de dados MySQL
    CREATE DATABASE test;
    SHOW DATABASES; 
    USE test;
    
    CREATE TABLE users (id INT AUTO_INCREMENT PRIMARY KEY, name VARCHAR(255));
    SHOW TABLES;
    DESC users;
    INSERT INTO users (name) VALUES ("Heviane");
    SELECT * FROM users;
    exit; # exit do mysql


    exit; # exit do ubuntu

docker inspect mysql

# Com o MySQL Client podemos pegar o IP retornado no comando acima e conectar-se com o MySQL Server diretamente.

## Se parar ou reiniciar o container não perdemos os dados.
## Se excluir (rm) o container perde os dados
```

## Parar, Reiniciar e Excluir um container

```bash
# Se parar ou reiniciar um container, os dados permanecerão.
docker stop mysql
docker start mysql

# Se excluir um container, os dados serão perdidos
docker rm mysql # Não exclui se estiver em execução
docker rm -f mysql # Exclui mesmo que esteja em execução

```
