# NodeJS
- É um interpretador de javascript que não possui vinculo com o navegador
- Vantagens: é leve, usa pouca memoria ram e tem um melhor aproveitamento da cpu

# Como instalar o NODEJS:

- Abra o navegador e acesse o site da NODEJS: https://nodejs.org/pt

- Para verficar se foi feita a instalação, abra o cmd e execute o comando: node -v ou npm -v

- Faça a instalação de um editor de texto: https://code.visualstudio.com, https://www.sublimetext.com/download, https://atom-editor.cc (recomendado Visual Studio Code)

# Uso de NODEJS
- Crie uma pasta e acesse o editor de codigo

- Crie uma linha de comando, por exemplo: console.log("Hello, World")

- Para a execução do codigo, acesse o terminal do Visual Studio Code com o atalho Ctrl + Shift + ', e coloque o comando no terminal: node nome_do_arquivo.js

# Como acessar a biblioteca do NODEJS
 - module.exports = variavel

![](soma.PNG) 
![](sub.PNG) 
![](multi.PNG) 
![](calc.PNG)

- Para acessar vc cria uma nova variavel e usa o require como a imagem acima.

# Criação de um servidor:

- var http = require("http")

- http.createServer().listen(3000)

###### //Mandar uma mensagem no cmd
- console.log("O servidor esta rodando")

![](/img/http2.png)

### Para mandar algo para o site

- var http = require("http")

- http.createServer(function(req, res){
    res.end("Ola")
}).listen(3000)

- console.log("O servidor esta rodando")

![](/img/http1.png)

### Para acessar o site coloque na url: localhost:3000

![](/img/http3.PNG)

# Como instalar o express:

- npm install express ou npm i express

### Utilização do express:

#### Começamos fazendo uma importação do express com o seguinte comando:

- const express = require("express")

#### Depois colocamos o express em uma variavel

- const app = express()

#### Agora fazemos o seguinte codigo:

- app.get("/", function(req, res){
    res.send("mensagem")
})

#### Explicação

- Rotas Definidas com app.get: O código usa várias rotas definidas pelo método app.get() para lidar com requisições GET:

### Linha 4-6: Rota principal ("/")

#### Quando acessada (http://localhost:3001/), responde com "Olá".

### Linha 8-10: Rota "/sobre"

#### Quando acessada (http://localhost:3001/sobre), responde com "Minha página sobre".

### Linha 12-14: Rota "/blog"

#### Quando acessada (http://localhost:3001/blog), responde com "Bem vindo ao meu blog!".

### Linha 16-18: Rota com parâmetros dinâmicos /ola/

Esta rota usa parâmetros de URL (denotados por :cargo, :nome, :cor) para capturar dados da URL e incluí-los na resposta.
Exemplo de uso: Se acessar a URL http://localhost:3001/ola/LLL/parenteses/green, a resposta seria:
- Ola parenteses
- Seu cargo é: LLL
- Sua cor favorita é: green

#### Linha 20-22: Inicia o Servidor

app.listen(3001, function(){console.log("Servidor rodando na url http://localhost:3001")})

### O h1, h2 e h3 não é necessário pois é uma linguagem de marcação utilizada no html.

![](/img/ex.PNG)

![](/img/get.PNG)

# API
#### Para começar temos que solicitar o express com o seguinte comando:

- const express = require("express")

#### Para acessar o banco de dados temos que criar uma variavel e usar o require, como o exemplo a seguir:
- const mysql = require("mysql2/promise")

#### Depois criamos uma nova variavel para a nossa conexão com informações do nosso banco de dados e da maquina, veja o exemplo a seguir:

- const conexão = mysql.createPool({

    database:"adflix",

    host:"localhost",

    password:"senai",

    user:"root"

})

#### Agora temos que criar uma variavel para armazenar o express:

- const app = express()

#### Criação da porta do servidor, ou uma chamada:

- app.listen(3000)

#### Criação de um novo caminho na url, usando as informações do banco de dados fazendo um print no navegador.

- app.get("/filmes",async function(req, res){

    var dados = await conexao,query("select * from filmes")

    console.log(dados[0])

    res.send(dados[0])

})

![](/img/api.jfif)

# Mysql

## Comandos

### Acessa o banco de dados, exigindo uma senha.

* mysql -u root -p

### Mostra os bancos de dados.

* show databases;

### Cria um banco de dados

* create database nome_do_banco;

### Entra no banco de dados

use nome_do_banco;

### Mostra as tabelas criadas

show tables;

### Comando para criar tabela

create table generos (
idgenero int not null auto_increment,
nome varchar(30) not null,
primary key (idgenero)
)
;

### Mostra as informações da tabela

- describe nome_da_tabela;

### Comando para inserir dados na tabela

- insert into nome_da_tabela(colocar os que estão sem auto_increment) value('valores');

#### Exemplo:
- insert into atores(nome, sobrenome, nascimento, historico) value('parenteses', 'LLL', '2023-06-15', 'Primo do Aspas, leão do diamante);

### Mostra todas as informações inseridas na tabela

- select * from nome_da_tabela;

### Atualizando dados na tabela

- UPDATE nome_da_tabela SET coluna = 'valor autalizado" WHERE condição

### Exemplo:

- UPDATE atores SET nome = 'aspas' where id = 1

### Exclui dados na tabela

- delete from nome_da_tabela where chave_primaria = linha;


#### Exemplo:

- delete from atores where atorid = 4;

### Adiciona uma chave estrangeira

- alter table nome_tabela add constraint fk_nome_da_chave_estrangeira foreign key (nome_do_item_da_tabela) references generos(nome_do_item_da_tabela);

#### Exemplo:

- alter table filmes add constraint fk_filmes_generos foreign key (generoid) references generos(idgenero);

### Exclui o ligamento da chave

- alter table nome_da_tabela drop constraint nome_da_chave