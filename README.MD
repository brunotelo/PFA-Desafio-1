# PFA-Desafio-1

Este projeto faz parte do desafio do curso que estou fazendo
Crie um programa utilizando sua linguagem de programação favorita que faça uma listagem simples do nome de alguns módulos do curso Full Cycle os trazendo de um banco de dados MySQL. Gere a imagem desse container e a publique no DockerHub.

Gere uma imagem do nginx que seja capaz que receber as solicitações http e encaminhá-las para o container.

Crie um repositório no github com todo o fonte do programa e das imagens geradas.

Crie um arquivo README.md especificando quais comandos precisamos executar para que a aplicação funcione recebendo as solicitações na porta 8080 de nosso computador. Lembrando que NÃO utilizaremos Docker-compose nesse desafio.

## PASSO 2 - Criando a rede
Rode no seu terminal o seguinte comando:
```
docker network create -d bridge pfanet
```

## PASSO 1 - Rodando os containers:
Container do MySQL
```
docker run --network pfanet -d -p 3306:3306 --name db -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=pfa -e MYSQL_USER=pfa -e MYSQL_PASSWORD=pfa brunotelo/bd
```
Container do PHP
```
docker run --network pfanet -d --name php7.4 brunotelo/php7.4
```
Container do nginx
```
docker run --network pfanet -p 8080:80 -d --name nginx brunotelo/nginx
```

Agora, basta acessar o endereço ```http://localhost:8080```