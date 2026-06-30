# Proxy Reverso com Nginx

Este projeto cria um container Docker com Nginx servindo uma página HTML estática.

## Pré-requisitos

- Docker instalado
- Git clone: 

```bash
git clone https://github.com/leonardorsolar/dockerfile-proxy-reverso.git
```


## Como construir a imagem

```bash
docker build -t meu-nginx .
```
é usado para criar uma imagem Docker a partir de um Dockerfile.
docker: chama o Docker.
build: informa ao Docker que ele deve construir (build) uma imagem.
A opção -t significa tag (nome da imagem).
meu-nginx: é o nome que será dado à imagem criada.
. O ponto (.) representa o contexto da construção.
Ele significa: "Utilize a pasta atual como contexto e procure nela o arquivo Dockerfile."
## Como executar o container

```bash
docker run -d -p 8080:80 --name meu-container meu-nginx
```

- `-d`: executa em segundo plano (detached)
- `-p 8080:80`: mapeia a porta 8080 do host para a porta 80 do container
- `--name meu-container`: nome do container

## Como acessar

Abra o navegador em: [http://localhost:8080](http://localhost:8080)

## Como parar e remover o container

```bash
docker stop meu-container
docker rm meu-container
```

## Estrutura do projeto

```
├── Dockerfile         # Define a imagem Nginx com o index.html customizado
├── index.html         # Página HTML servida pelo Nginx
└── README.md          # Este arquivo
```

## Funcionamento

O `Dockerfile` usa a imagem oficial `nginx` como base e copia o arquivo `index.html` para o diretório `/usr/share/nginx/html/`, que é o diretório padrão onde o Nginx serve arquivos estáticos.

Acessando `http://localhost:8080`, o Nginx responderá com o conteúdo do `index.html`.
