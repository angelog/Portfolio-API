# PostifolioAPI
Portfólio com os projetos desenvolvidos em cada semestre destacando as contribuições individuais

## OPERAÇÃO LAVA BOT - 1º Semestre de Banco de Dados FATEC/SJC 2019/2.

### Objetivo

Desenvolver um web bot que faça uma raspagem de dados em um site, coletando dados
referentes as despesas gastas por políticos de cargo eletivo, coletando informações
que serão arquivadas, onde as mesmas serão desmembradas em quanto cada tipo de despesa
consumiu do valor pago em impostos pelo contribuinte.

### Requisitos

- Desenvolver um programa em linguagem Python que faça a coleta de dados em um site
que disponibilize as informações necessarias;
- Reunir os valores coletados em um banco de dados ou em forma de tabelas;
- Organizar as informações em categorias a serem definidas.
- Listar os dados de forma estatística com o objetivo de identificar os principais
focos de onde se precisa trabalhar para que os recursos públicos sejam utilizados
de forma mais eficiente.

### Desenvolvimento

- Programa desenvolvido em linguagem Python.
- Uma solicitação de biblioteca faz a raspagem de dados através da API do site de dados abertos da câmara dos deputados.
- As informações incluídas na raspagem serão armazenadas em um arquivo csv.
- Utiliza uma biblioteca de pandas para tratamento de arquivo, sendo ordenada e exibida para o usuário de acordo com o critério de pesquisa que ele escolheu.
- Os recursos da biblioteca Matplotlib serão utilizados para que o usuário possa visualizar os dados em forma de gráfico.

## Atribuição Individual
### Request
```bash
    import requests
    import os

    URL = 'https://dadosabertos.camara.leg.br/api/v2/deputados'
    RESP = requests.get(URL).json()

    PASTA_RAIZ = './GASTOS_INDIVIDUAIS'
    os.mkdir(PASTA_RAIZ)
    FILE_CSV = open('NOME_ID_TOTAL.csv', 'w')  # criando arquivo csv para escrever nome, ID, e total de gastos de cada deputado

    CONTADOR = 2
    GUIA_SOMA = 2
    politicos = {}

    while CONTADOR <= 9:

        PASTA_MES = './GASTOS_INDIVIDUAIS/MES_' + str(GUIA_SOMA)
        os.mkdir(PASTA_MES)

        for INFO in RESP['dados']: # for usado para buscar nome, id e as diversas despesas de cada deputado
            NOME_DEPUTADO = str(INFO['nome'])
            ID_DEPUTADO = str(INFO['id'])
            PARTIDO_DEPUTADO = str(INFO['siglaPartido'])
            UF_DEPUTADO = str(INFO['siglaUf'])
            URL = 'https://dadosabertos.camara.leg.br/api/v2/deputados/' + ID_DEPUTADO + '/despesas?ano=2019&mes=0' + str(GUIA_SOMA) + '&ordem=ASC&ordenarPor=ano'
            POST = requests.get(URL).json()
            print(POST)

    # criando arquivo txt para escrever as diversas despesas de cada deputado
        FILE_TXT = open('./GASTOS_INDIVIDUAIS/MES_'+ str(GUIA_SOMA) + '/GASTOS_' + NOME_DEPUTADO + '_' + ID_DEPUTADO + '.txt', 'w')

```
### Tratamento
```bash
  if NOME_DEPUTADO in politicos:
            politicos[NOME_DEPUTADO].append(SOMA)
        else:
            politicos[NOME_DEPUTADO] = [NOME_DEPUTADO, ID_DEPUTADO, PARTIDO_DEPUTADO, UF_DEPUTADO, SOMA]
  
  for politico in politicos:
    dados = (';'.join(map(str, politicos[politico])))
    print(dados)
    FILE_CSV.writelines('\n' + dados)
```
# _____________________________________________
## MEGA DEV - 2º Semestre de Banco de Dados FATEC/SJC 2020/1.

O principal objetivo do projeto é desenvolver um sistema para a Visão Estratégica de Projetos,
o sistema sera desenvolvido para facilitar o planejamento de projetos de uma empresa.

## Atribuição Individual
### LOGIN
```bash
<!DOCTYPE html>
<html>
<head>
	<title>Login</title>
	<link rel="stylesheet" href="../css/bootstrap.min.css">
	<link rel="stylesheet" type="text/css" href="../css/login.css">
</head>
<body>
	<img src="../img/fundo2.jpg" class="card-img" id="imagem_fundo">
	<div class="card-img-overlay" id="card" style="text-align: center">
		<div class="card-body" style="color:black;" >
			<img src="../img/logo.jpg" width="100" height="100">
			<div style="text-align: left;" class="mx-3">
				<label><b>Usuário</b></label>
				<input class="form-control border-primary "type="text" id="usuario" placeholder="Usuário" >
				<label><b>Senha</b></label>
				<input class="form-control border-primary "type="password" id="senha" placeholder="Senha" >
			</div>
		</div>
		<div class="card-footer">
			<button class="btn btn-primary w-25 border border-dark rounded-pill" id="va" onclick="validar()"><b>Entrar</b></button> 
		</div>
	</div>
</body>
<script type="text/javascript" src="../js/jquery-3.5.1.slim.min.js"></script>
<script type="text/javascript">
	function validar(){
		if ($("#usuario").val().toUpperCase()!= "ADMIN" || $("#senha").val()!= "megadev2020") {
			return alert("Usuário ou Senha invalido");
		}
		window.location.href="index.html";

	}
	$("#usuario, #senha").keypress(function(event){
		if (event.keyCode == 13) {
			validar()
		}
	})
</script>
</html>
```
# ____________________________________________
## KIND OF - 3º Semestre de Banco de Dados FATEC/SJC 2020/2.

### Criação de uma aplicação web com dashboard.
> É proposto o desenvolvimento de um Sistema de Recompensas dentro de uma aplicação do cliente. O cliente busca otimizar seu negócio através de uma dashbord, com as informações mais atrativas e impactantes para seus clientes. O cliente pode acompanhar seus respectivos dados de maneira segura e organizada, e caso necessário, e tomar a decisões a partir delas.

O objetivo do trabalho é reinventar a forma de aproximação do usuário da plataforma. Não consistindo na criação web de apenas consultas, mas sim em uma aplicação utilizando o sistema de recompensas, na qual o usuário poderá utiliza-los dentro da aplicação com o que o cliente poderá fornecer. As recompensas foram demostradas através de cursos que poderão auxiliar o usuário com a própria gestão financeira. 


### :memo: Referências <a name="-tecnologias"/></a> 

```
- Java, Html, Css, JavaScript
- frameworks: Spring Boot, Boostrap 
- banco de dados relacional: MySQL
```

## Atribuição Individual
### Login
```bash

  <!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml"
      xmlns:th="http://www.thymeleaf.org">

<head>
    <title>Login - Projeto Integrador</title>
    <link rel="stylesheet" type="text/css" th:href="@{/css/login.css}"/>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.1/jquery.min.js"></script>
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
</head>

<body>

<div style="background: white; height: 40px"></div>

<div align="center">
    <img th:src="@{/images/logoSVG.svg}" class="img-responsive" width="200" height="200" alt="Logo"/>
</div>

<div style="background: white; height: 50px"></div>

<div align="center" class="container">
    <form th:action="@{/login}" method="POST" class="form-signin">
        <h3 th:text="Login"></h3>

        <input type="text" id="user_name" name="user_name" placeholder="CPF"
               class="form-control"/> <br/>

        <input type="password" th:placeholder="Senha"
               id="password" name="password" class="form-control"/><br/>

        <div align="center" th:if="${param.error}">
            <p style="font-size: 20; color: #FF1C19;">Usuário ou Senha inválidos!</p>
        </div>

        <button class="btn btn-lg btn-success btn-block" name="Submit" value="Login" type="Submit" th:text="Login"></button>
    </form>

    <br/>

    <form th:action="@{/registration}" method="get">
        <button class="btn btn-lg btn-warning btn-block" type="Submit">Criar Usuário</button>
    </form>
</div>
</body>
</html>
```
### Cadastro
```bash
<!DOCTYPE html>
<html lang="en" xmlns="http://www.w3.org/1999/xhtml"
      xmlns:th="http://www.thymeleaf.org">
<head>
    <title>Cadastre-se - Projeto Integrador</title>
    <link rel="stylesheet" type="text/css" th:href="@{/css/registration.css}"/>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.1/jquery.min.js"></script>
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
</head>
<body>

<div style="background: white; height: 40px"></div>

<div align="center">
    <img th:src="@{/images/logoSVG.svg}" class="img-responsive" width="200" height="200" alt="Logo"/>
</div>

<div style="background: white; height: 60px"></div>

<div align="center" class="container">
    <form autocomplete="off" action="#" th:action="@{/registration}"
          th:object="${user}" method="post" role="form">
        <h3 class="form-signin-heading" th:text="Cadastre-se"></h3>

        <input type="text" th:field="*{name}" placeholder="Nome"
               class="form-control"/><br/>
        <label th:if="${#fields.hasErrors('name')}" th:errors="*{name}"
               class="validation-message"></label>

        <input type="text" th:field="*{lastName}"
               placeholder="Sobrenome" class="form-control"/><br/>
        <label th:if="${#fields.hasErrors('lastName')}" th:errors="*{lastName}"
               class="validation-message"></label>

        <input type="text" th:field="*{email}" placeholder="Email"
               class="form-control"/><br/>
        <label th:if="${#fields.hasErrors('email')}" th:errors="*{email}"
               class="validation-message"></label>

        <input type="text" th:field="*{userName}" placeholder="CPF"
               class="form-control"/><br/>
        <label th:if="${#fields.hasErrors('userName')}" th:errors="*{userName}"
               class="validation-message"></label>

        <input type="password" th:field="*{password}"
               placeholder="Senha" class="form-control"/><br/>
        <label th:if="${#fields.hasErrors('password')}" th:errors="*{password}"
               class="validation-message"></label>

        <div style="height: 20px"></div>

        <button type="submit" class="btn btn-lg btn-primary btn-block">Criar Usuário</button>

        <h2><span class="text-success" th:utext="${successMessage}"></span></h2>
    </form>

    <form th:action="@{/}" method="get">
        <button class="btn btn-lg btn-success btn-block" type="Submit">Voltar ao Login</button>
    </form>

</div>
</body>
</html>
```
### Home Page
```bash
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml"
      xmlns:th="http://www.thymeleaf.org">

<head>
	<meta charset="UTF-8">
	<title>Home - Projeto Integrador</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css">
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.1.1/jquery.min.js"></script>
    <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/js/bootstrap.min.js"></script>
	<style>
	ul { list-style-type: none; margin: 0; padding: 0; overflow: hidden; border-top-style: solid; border-width: 1px; border-color: #CFCFCF;}
	li { float: right;}
	li a {display: block; text-align: center; padding: 14px 16px; text-decoration: none; color: #9C9C9C;}
	p{ font-size: 15px;	padding-top: 2px;}
	</style>
</head>

<body>

<div>
	<form th:action="@{/logout}" method="get">
		<button style="float: right; margin-top: 3px; margin-bottom: 3px; margin-right: 3px; margin-left: 3px;" class="btn btn-sm btn-danger" name="registration"
				 type="Submit">Sair
		</button>
	</form>
</div>

<div style="font-size: 14px; float: right; margin-top: 6px; margin-bottom: 0px; margin-right: 3px; margin-left: 3px; align" >
	<span th:utext="${userName}" ></span>
</div>

<div>
	<img th:src="@{/images/logoSVG.svg}" class="rounded" style="height: 30px; margin-top: 3px; margin-bottom: 3px; margin-right: 3px; margin-left: 3px;">
</div>

<div>
	<nav>
		<ul>
			<li><a th:href="@{/admin/loja}">Home</a></li>
			<li><a href="#">Histórico de pagamento</a></li>
			<li><a href="#">Histórico Liberado</a></li>
			<li><a href="#">Consulte seu CPF</a></li>
			<li><a href="#">Empresas Suspensas</a></li>
			<li><a href="#">Contestações</a></li>
		</ul>
	</nav>
</div>
<div class="container">
	</div>
		<div style="position: absolute; margin-left: 70%; margin-top: 100px;" class="col-sm">
			<div style="font-size: 40px;" class="Score"><span th:utext="${userScore}" ></span></div>
			<div style="font-size: 40px;" class="Points"><span th:utext="${userPontos}" ></span></div>
			<a class="pointstore" th:href="@{/admin/rewards}">O que fazer com seus pontos?</a>
		</div>
		<div class="container" >
			<div class="row">
				<div class="col-sm">
					<div class="LineChart" style="height: 300px; width: 600px;">
					<canvas id="myLineChart"></canvas>
					<script src="https://cdn.jsdelivr.net/npm/chart.js@2.8.0"></script>
					<script>
						var ctx = document.getElementById('myLineChart').getContext('2d');
						var chart = new Chart(ctx, {
							type: 'line',
							data: {
								labels: ['Janeiro', 'Fevereiro', 'Março', 'Abril', 'Maio',
								'Junho', 'Julho', 'Agosto', 'Setembro', 'Outubro', 'Novembro', 'Dezembro'],
								datasets: [{
								label: 'Score',
								borderColor: 'rgba(10, 99, 132)',
									backgroundColor: 'rgba(0, 0,0,0)',
									pointBackgroundColor: 'rgba(10, 99, 132)',
									pointRadius: 5,
									data: [500, 610, 555, 732, 520, 830, 545, 234, 535, 745, 856, 646]
								}]
							},
							options: {}
						});
					 </script>
					</div>
					<div style="height: 300px; width: 600px;" class="BarChart">
						<canvas id="myBarChart"></canvas>
						<script src="https://cdn.jsdelivr.net/npm/chart.js@2.8.0"></script>
						<script>
							var ctx2 = document.getElementById('myBarChart').getContext('2d');
							var barChart = new Chart(ctx2,{
								type: 'bar',
								data: {
									labels: ['Janeiro', 'Fevereiro', 'Março', 'Abril', 'Maio',
									'Junho', 'Julho', 'Agosto', 'Setembro', 'Outubro', 'Novembro', 'Dezembro'],
									datasets: [{
										label: 'Gasto (R$)',
										backgroundColor: 'rgba(10, 99, 132)',
										maxBarLength: 10,
										minBarLength: 2,
										data: [1000, 1610, 2555, 1732, 1520, 1830, 2545, 1234, 1535, 1745, 1856, 1646],
										fill: false
									}],

								},
								options: {
									scales:{
										yAxes: [{
											ticks:{
												beginAtZero: true
											}
										}]
									}
								}
							});
						</script>
					</div>
				</div>

			</div>
		</div>

		<script src="https://code.jquery.com/jquery-3.5.1.slim.min.js" integrity="sha384-DfXdz2htPH0lsSSs5nCTpuj/zy4C+OGpamoFVy38MVBnE+IbbVYUew+OrCXaRkfj" crossorigin="anonymous"></script>
		<script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.1/dist/umd/popper.min.js" integrity="sha384-9/reFTGAW83EW2RDu2S0VKaIzap3H66lZH81PoYlFhbGU+6BZp6G7niu735Sk7lN" crossorigin="anonymous"></script>
		<script src="https://cdn.jsdelivr.net/npm/bootstrap@4.5.3/dist/js/bootstrap.min.js" integrity="sha384-w1Q4orYjBQndcko6MimVbzY0tgp4pWB4lZ7lr30WKz0vr/aWKhXdBNmNb5D92v7s" crossorigin="anonymous"></script>
				</div>
			</div>
		</div>
</body>
</html>
```
#__________________________________________
## App-Loading 4º Semestre de Banco de Dados 


## Visão do Projeto</br> <a name="-visao"/></a>
O projeto realizado está na área de recrutamento de candidatos, na qual consiste na criação de uma api web simples para criação de vaga e busca do candidato, com foco na otimização da seleção. A estruturação de um eficiente processo de recrutamento facilita a seleção de talentos e competências necessárias para a continuidade e o sucesso das instituições.
</br></br>

## Funcionalidade </br>

O usuário poderá selecionar candidato atráves de filtros, sendo ele: pcd, conhecimento, idioma, vale transporte (vt), nível de escolaridade. Os filtros foram alinhados juntamente com o cliente, sendo fixado o vt < 3 quilômetros da instituição como vt =0. Todos os filtros são ordenados conforme necessidade e relevancia do usuário para a busca do candidado "ideal". Ao criar uma vaga, a mesma irá trazer os candidatos, assim como, a pesquisa isolada dos candidatos também será permitido. 

## Tecnologias Utilizadas</br> <a name="-tecnologias"/></a>
•    [Python 3.9](https://www.python.org/)</br>
•    [MySQL](https://www.mysql.com/)</br>
•    [Flask 2.0](https://flask.palletsprojects.com/en/2.0.x/)</br>
•    [Postman](https://www.postman.com/)</br>


As escolhas das tecnologias foram baseadas em performance e redução de complexidade. A escolha de um banco relacional MySQL possibilitou a criação de indices que aumentaram a performance do próprio banco com um número volumoso de dados, assim como o MySQL se tornou o mais popular banco de dados Open Source do mundo.

## Bibliotecas Utilizadas</br> <a name="-bibliotecas"/></a>
•    requests </br>
•    ast</br>
•    flask_mysqldb</br>
•    sqlalchemy</br>

As bibliotecas utilizadas facilitaram na comunicação com o banco de dados, assim como cálculos de localização e aproximação dos candidatos. 


## Atribuição Individual
### - Conecção com o DataBase
```bash
from flask import Flask
from flask_mysqldb import MySQL

app = Flask("JETSOFT")
app.config['MYSQL_HOST'] = 'localhost'
app.config['MYSQL_USER'] = 'root'
app.config['MYSQL_PASSWORD'] = '97855818'
app.config['MYSQL_DB'] = 'mydb'
app.config['MYSQL_CURSORCLASS'] = 'DictCursor'
mysql = MySQL(app) 

class DatabaseManager:

    def Insert_Drop(self,query):
        cursor = mysql.connection.cursor()
        cursor.execute(query)
        cursor.connection.commit()

    def Filtrar(self,query):
        cursor=mysql.connection.cursor()
        cursor.execute(query)
        return cursor.fetchall()
```
### - Candidato
```bash

from db import DatabaseManager
from cepCoords import cepCoord
from flask import jsonify

class CandidatoDatabase:

#INSERT
    def insertCandidato(self, lat, long, vars):
        database = DatabaseManager()
        
        query="INSERT INTO candidato (nomeCandidato, cpfCandidato, dataNascimentoCandidato, emailCandidato, pcdCandidato, cepCandidato, latitudeCandidato, longitudeCandidato, telResCandidato, telCelCandidato, nivelEscolaridade) VALUES ('{}', '{}', {}, '{}', {}, '{}', {}, {}, {}, {}, '{}')".format(vars["nomeCandidato"], vars["cpfCandidato"], vars["dataNascimentoCandidato"], vars["emailCandidato"], vars["pcdCandidato"], vars["cepCandidato"], lat, long, vars["telResCandidato"], vars["telCelCandidato"], vars["nivelEsc"])
        database.Insert_Drop(query)
        
        for c in vars:
            if c == "conhecimento":
                for i in range(len(vars[c])):
                    query ="INSERT INTO candidato_conhecimento (idConhecimento, cpfCandidato) VALUES ({}, '{}')".format(vars[c][i], vars["cpfCandidato"])
                    database.Insert_Drop(query)

        for c in vars:
            if c == "idioma":
                for i in range(len(vars[c])):
                    query ="INSERT INTO candidato_idioma (idIdioma, cpfCandidato) VALUES ({}, '{}')".format(vars[c][i], vars["cpfCandidato"])
                    database.Insert_Drop(query)

        for c in vars:
            if c == "experiencia":
                for i in range(len(vars[c])):
                    query ="INSERT INTO experiencia_profissional (empresa, cargo, cpfCandidato, tempo) VALUES ('{}', '{}', '{}', {})".format(vars[c][i]["empresa"], vars[c][i]["cargo"], vars["cpfCandidato"], vars[c][i]["tempo"])
                    database.Insert_Drop(query)

        return True

#DROP
    def dropCandidato (self, cpf):
        query = "DELETE FROM candidato WHERE cpfCandidato = '{}'".format(cpf)
        database = DatabaseManager()
        database.Insert_Drop(query)

#FILTER
    def filtrarCandidato(self,latuser,longuser,vars):
        item = 1    
        query="select candidato.nomeCandidato,candidato.emailCandidato,(6371 * acos(cos(radians({})) * cos(radians(candidato.latitudeCandidato)) * cos(radians({}) - radians(candidato.longitudeCandidato)) + sin(radians({})) * sin(radians(candidato.latitudeCandidato)) )) AS distance from candidato".format(latuser, longuser, latuser)
        for x in vars:
            if x == "conhecimento":
                query = query + " inner join conhecimento on conhecimento.descConhecimento = '{}' inner join candidato_conhecimento on candidato_conhecimento.cpfCandidato = candidato.cpfCandidato and candidato_conhecimento.idConhecimento = conhecimento.idConhecimento".format(vars[x])
            if x == "idioma":
                query = query + " inner join idioma on idioma.descIdioma = '{}' inner join candidato_idioma on candidato_idioma.cpfCandidato = candidato.cpfCandidato and candidato_idioma.idIdioma = idioma.idIdioma".format(vars[x])
            order = []
            where = []
            if x == "nivelEsc":
                item = " where candidato.nivelEscolaridade = '{}'".format(vars[x])
                item = 0
            if x == "pcd":
                if item == 0:
                    item = " and candidato.pcdCandidato = {}".format(c["pcd"])
                    query = query + item
                else:
                    item = " where candidato.pcdCandidato = {}".format(c["pcd"])
                    query = query + item
                    print(query)
            if x == "vt":
                if vars[x] == 0:
                    query = query + " having distance <= 3"
                else:
                    query = query + " having distance > 3"
            if x == "order":
                for c in x:
                    order.append(vars[c][x]) 
                order = ','.join(order)
                query = query + "order by "+ order

        database = DatabaseManager()
        result = database.Filtrar(query)
        print(result)
        return jsonify(result=result)

    def listaCandidato(self):
        database = DatabaseManager()
        query = "select * from candidato"
        result = database.Filtrar(query)
        return jsonify(result = result)

#UPDATE
    def updateCandidato (self, vars, cpf):
        database = DatabaseManager()
        
        for c in vars:
            if c == "conhecimento":
                for i in range(len(vars[c])):
                    query ="INSERT INTO candidato_conhecimento (idConhecimento, cpfCandidato) VALUES ({}, '{}')".format(vars[c][i], cpf)
                    database.Insert_Drop(query)

        for c in vars:
            if c == "idioma":
                for i in range(len(vars[c])):
                    query ="INSERT INTO candidato_idioma (idIdioma, cpfCandidato) VALUES ({}, '{}')".format(vars[c][i], cpf)
                    database.Insert_Drop(query)

        for c in vars:
            if c == "experiencia":
                for i in range(len(vars[c])):
                    query ="INSERT INTO experiencia_profissional (empresa, cargo, cpfCandidato, tempo) VALUES ('{}', '{}', '{}', {})".format(vars[c][i]["empresa"], vars[c][i]["cargo"], cpf, vars[c][i]["tempo"])
                    database.Insert_Drop(query)

        for c in vars:
            if c == "nomeCandidato":
                query="UPDATE candidato SET nomeCandidato = '{}' WHERE cpfCandidato = '{}'".format(vars[c], cpf)
                database.Insert_Drop(query)

        for c in vars:
            if c == "dataNascimentoCandidato":
                query="UPDATE candidato SET dataNascimentoCandidato = {} WHERE cpfCandidato = '{}'".format(vars[c], cpf)
                database.Insert_Drop(query)

        for c in vars:
            if c == "emailCandidato":
                query="UPDATE candidato SET emailCandidato = '{}' WHERE cpfCandidato = '{}'".format(vars[c], cpf)
                database.Insert_Drop(query)

        for c in vars:
            if c == "pcdCandidato":
                query="UPDATE candidato SET pcdCandidato = {} WHERE cpfCandidato = '{}'".format(vars[c], cpf)
                database.Insert_Drop(query)

        for c in vars:
            if c == "cepCandidato":
                buscep= cepCoord(vars["cepCandidato"])
                lat = buscep[0]
                long = buscep[1]
                query="UPDATE candidato SET cepCandidato = '{}', latitudeCandidato = {}, longitudeCandidato = {}  WHERE cpfCandidato = '{}'".format(vars[c], lat, long, cpf)
                database.Insert_Drop(query)

        for c in vars:
            if c == "telResCandidato":
                query="UPDATE candidato SET telResCandidato = '{}' WHERE cpfCandidato = '{}'".format(vars[c], cpf)
                database.Insert_Drop(query)

        for c in vars:
            if c == "telCelCandidato":
                query="UPDATE candidato SET telCelCandidato = '{}' WHERE cpfCandidato = '{}'".format(vars[c], cpf)
                database.Insert_Drop(query)

        for c in vars:
            if c == "nivelEscolaridade":
                query="UPDATE candidato SET nivelEscolaridade = '{}' WHERE cpfCandidato = '{}'".format(vars[c], cpf)
                database.Insert_Drop(query)
```
