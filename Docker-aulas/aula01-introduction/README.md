# Primeiros Passos com Docker: Criando um Contêiner "Hello, World!"

Uma introdução prática ao Docker, guiando você na criação e execução do seu primeiro contêiner.

## Pré-requisitos

Antes de começar, certifique-se de que você tem o Docker instalado e em execução na sua máquina.

- [Docker Desktop](https://www.docker.com/products/docker-desktop/) (Windows, macOS, e Linux)
- Ou Docker Engine para servidores Linux.

Você pode verificar se o Docker está instalado corretamente executando:

```bash
docker --version
```

## Aula 01: Seu Primeiro Contêiner

Nesta aula, vamos construir uma imagem Docker que executa um script simples para imprimir "Hello, World!" e, em seguida, executar um contêiner a partir dessa imagem.

### Passo 1: Criar o `Dockerfile`

O `Dockerfile` é um arquivo de texto que contém todas as instruções para montar uma imagem Docker. Crie um arquivo chamado `Dockerfile` (sem extensão) no seu diretório de projeto com o seguinte conteúdo:

```dockerfile
# Use uma imagem base leve
FROM alpine:latest

# Defina o comando a ser executado quando o contêiner iniciar
CMD ["echo", "Hello, World!"]
```

**O que este arquivo faz?**

- `FROM alpine:latest`: Define a imagem base para a nossa construção. `alpine` é uma distribuição Linux mínima, ideal para criar imagens pequenas.
- `CMD ["echo", "Hello, World!"]`: Especifica o comando padrão que será executado quando um contêiner for iniciado a partir desta imagem.

### Passo 2: Construir a Imagem Docker

Agora, com o `Dockerfile` no seu diretório, vamos construir a imagem. Abra seu terminal nesse diretório e execute o comando abaixo:

```bash
docker build -t hello-world .
```

A flag **-t** (de tag) é usada para dar um nome à sua imagem, o que facilita na hora de executá-la.
O **.** no final do comando informa ao Docker para usar o diretório atual como o contexto de construção.

### 3. Executar o Contêiner

Use o comando docker run para executar o contêiner a partir da imagem definida e construída nos passos anteriores:

```bash
    docker run hello-world
```

Ao executar este comando, o Docker iniciará um contêiner a partir da sua imagem hello-world.
O contêiner executará a instrução `CMD ["echo", "Hello, World!"]` definida no seu Dockerfile, imprimirá "Hello, World!" no seu terminal e, em seguida, será finalizado.
