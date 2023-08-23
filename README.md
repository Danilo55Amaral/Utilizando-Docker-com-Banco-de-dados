<h1>
     <img align="center" width="40px" src="https://1000logos.net/wp-content/uploads/2021/11/Docker-Logo.png">
    <span> Rodando Banco de Dados com Docker</span>
</h1>

O Docker é uma forma de virtualização que utiliza imagens mantendo aplicações de forma 
isolada, o Docker permite o envio, execução e o desenvolvimento de aplicaçãos, 
utilizando o Docker é possível gerenciar infraestrutura da mesma forma que se gerencia 
aplicações. 

É possível empacotar e executar um banco de dados ou servidor por exemplo, em um 
ambiente totalmente isolado que é conhecido como contêiner. É possível também executar 
vários contêineres ao mesmo tempo sem causar conflitos entre eles. 

O Contêiner Docker compartilha recursos da máquina assim como o Kernel, isso evita 
redundância e reduz o uso de recursos desnecessários, como os contêineres rodam de 
forma isolada isso trás mais segurança, a utilização de contêineres Docker permite 
também uma melhor otimização de recursos de hardware da propria máquina.


## Criando Imagem do MySQL no Docker

Caso não possua o Docker instalado em sua máquina você pode acessar o site oficial 
do Docker e seguir os passos para a instalação. 
```bash
    https://www.docker.com
```
Após a instalação do Docker podemos utilizar comandos via terminal para criação e 
gerênciamento dos contêineres, a seguir vou utilizar alguns desses comandos para criar 
um contêiner com uma imagem do MySQL.

Abra o Windows PowerShell e nele executamos os comandos necessários para a criação do 
Contêiner com o MySQL.

Verificando se o Docker está instalado:
```bash
    docker -v
```
Caso esteja ele irá retornar a versão do Docker que foi instalada.

![docker-post03.PNG](https://github.com/Danilo55Amaral/Utilizando-Docker-com-Banco-de-dados/blob/main/docker-post03.PNG)

## DockerHub 
O dockerHub é um repositório de imagens do Docker e pode ser acessado através do link
a seguir:
```bash
    https://hub.docker.com
```
Imagens no Docker são scripts que são preconfigurados para executar coisas como banco 
de dados, servidores e outras aplicações, para executar esses serviços usamos imagens no Docker, através do Dockerhub é possivel baixar imagens como a do MySQL para rodar 
diretamente no Docker.

O comando a seguir vai puxar a imagem do MySQL para o Docker:
```bash
    docker pull mysql
```
Esse comando vai buscar a versão mais recente do MySQL e instalar tudo que for 
necessário para rodar dentro do Docker. 

![docker02.PNG](https://github.com/Danilo55Amaral/Utilizando-Docker-com-Banco-de-dados/blob/main/docker02.PNG)

Após baixar a imagem é possivel criar um contêiner que vai rodar a imagem do MySQL,
para criar o contêiner basta rodar o seguinte comando:
```bash
    docker run -p 3306:3306 --name mysql_potencia_tech -e MYSQL_ROOT_PASSWORD=root -d mysql
```

O -p vai ser para indicar a porta em que o Mysql vai rodar, --name serve para colocar 
o nome do banco de dados, -e serve para passar a senha para o root, -d é utilizado 
para indicar qual a imagem que será utilizada no contêiner. 

Para verificar quais contêineres estão rodando é utilizado o seguinte comando:
```bash
    docker ps
```

Também é possivel de utilizar em ambiente Windows a interface gráfica do Docker e 
verificar, manipular esses contêineres. 

![docker-post01.PNG](https://github.com/Danilo55Amaral/Utilizando-Docker-com-Banco-de-dados/blob/main/docker-post01.PNG)

Na opção actions do contêiner é possível abrir o terminal de execução dentro do Docker 
e assim poder acessar e manipular o banco de dados diretamente via terminal no Docker, para
acessar o Shell do contêiner e testar o MySQL rode o seguinte comando:
```bash
    mysql -uroot -p 
```
Após fazer isso ele irá pedir a senha do root para poder acessar o banco de dados.
Após efetuar a conexão pode utilizar o comando seguinte para testar e listar os bancos.
```bash
    SHOW DATABASES;
```

![docker-post02.PNG](https://github.com/Danilo55Amaral/Utilizando-Docker-com-Banco-de-dados/blob/main/docker-post02.PNG)

## Conectando o contêiner ao MySQL Workbench

É necessário instalar o MySQL Workbench na máquina porém não é necessário instalar 
o MySQL pois vamos utilizar o MySQL que está rodando dentro do contêiner do Docker.

Após instalar o MySQL Workbench basta criar uma conexão utilizando o método de conexão 
padrão (TCP/IP), em seguida passar o Hostname e a porta que o nosso Contêiner Mysql 
está rodando, a senha passada para a conexão é a mesma senha que passamos quando 
criamos o contêiner com a imagem do MySQL.

![workebenc-post01.PNG](https://github.com/Danilo55Amaral/Utilizando-Docker-com-Banco-de-dados/blob/main/workebenc-post01.PNG)

## Criando Imagem do PostgreSQL no Docker

Aqui eu utilizo uma imagem do bitnami/postgresql mas fica a critério, também 
pode ser utilizada a 
imagem oficial do PostgresSQL, basta ir ao DockerHub e seguir os passos de 
criação da imagem oficial do PostgresSQL.

Para criar o contêiner utilizando a imagem do bitnami/postgresql rodamos o seguinte comando.
```bash
    docker run --name api-solid-pg -e POSTGRESQL_USERNAME=root -e POSTGRESQL_PASSWORD=root -e POSTGRESQL_DATABASE=apisolid -p 5432:5432 bitnami/postgresql
```
Após fazer isso ele vai subir o banco de dados PostgresSQL criado ao contêiner 
do Docker.

Note que ao abrir a interface do Docker eu posso ver os dois Contêineres com os 
dois bancos de dados.

![docker-post01.PNG](https://github.com/Danilo55Amaral/Utilizando-Docker-com-Banco-de-dados/blob/main/docker-post01.PNG)

## Alguns comandos do Docker 

Para rodar o contêiner via terminal basta rodar o comando start passando o id ou o nome do contêiner:
```bash
    docker start nome-do-conteiner
```
Para parar de rodar o contêiner basta rodar o comando stop:
```bash
    docker stop nome-do-conteiner
```
Para deletar um contêiner basta rodar o comando rm:
```bash
    docker rm nome-do-conteiner
```
Para ver logs do contêiner:
```bash
    docker logs nome-do-conteiner
```
Para ficar monitorando os logs basta utilizar o -f:
```bash
    docker logs nome-do-conteiner -f
```