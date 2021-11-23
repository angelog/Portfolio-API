# PostifolioAPI
Portfólio com os projetos desenvolvidos em cada semestre destacando as contribuições individuais

## OPERAÇÃO LAVA BOT - 1º Semestre de Banco de Dados FATEC/SJC 2019/2.

O objetivo do projeto é que um grupo de alunos desenvolva uma aplicação em que
seja utilizado um WebBot desenvolvido pelo grupo, usando o na solução de um
problema proposto pelo grupo.

### Objetivo

Desenvolver um web bot que faça uma raspagem de dados em um site, coletando dados
referentes as despesas gastas por políticos de cargo eletivo, coletando informações
que serão arquivadas, onde as mesmas serão desmembradas em quanto cada tipo de despesa
consumiu do valor pago em impostos pelo contribuinte.

### Público Alvo

As informações podem ser acessadas pela imprensa, com fim de divulgação
em seus veículos de comunicação, por associações que fazem um trabalho independente
de fiscalização dos órgãos públicos e pela população em geral, com o intuito de
cobrar atitudes mais corretas de políticos que tiverem despesas excessivas.

### Finalidade

Tornar mais acessível a população informações que podem ajudá-los a
pressionar os políticos a trabalharem em causas de interesse popular e colaborar
com órgãos de segurança pública, como a polícia federal e o judiciário por exemplo,
a identificar possíveis crimes vinculados a corrupção que podem ser identificados
através de valores anormais ou alguma outra irregularidade, como improbidade administrativa
e lavagem de dinheiro.

### Requisitos

- Desenvolver um programa em linguagem Python que faça a coleta de dados em um site
que disponibilize as informações necessarias;
- Reunir os valores coletados em um banco de dados ou em forma de tabelas;
- Organizar as informações em categorias a serem definidas.
- Listar os dados de forma estatística com o objetivo de identificar os principais
focos de onde se precisa trabalhar para que os recursos públicos sejam utilizados
de forma mais eficiente.

### Desenvolvimento

### Front End

- Programa desenvolvido nas linguagens Html, Css e Javascript
- A estrutura do Html será utilizada para criar a interface que será utilizada pelo usuário
- Alguns recursos de Css serão utilizados para melhorar a aparência da página e definir o alinhamento e tamanho de fonte do que será mostrado pela aplicação
- Os recursos do Javascript terão funções de redirecionamento no clique dos botões ou na escolha de alguma opção e de associar essa escolha à parte correspondente do programa

### Back End

- Programa desenvolvido em linguagem Python
- A biblioteca request fará a raspagem de dados através da api do site dos dados abertos da câmara dos deputados
- As informações obtidas na raspagem serão armazenadas em um arquivo csv
- utilizamos a biblioteca pandas para o tratamento do arquivo, sendo ordenados e aparecerem para o usuário de acordo com o critério de pesquisa que ele escolher
- Os recursos da biblioteca Matplotlib serão utilizados para que o usuário possa visualizar os dados em forma de gráfico.

### Para executar o projeto

- Para começar, entre na pasta do projeto "operacao-lava-bot" e execute o seguinte comando:

    ```bash
    pip install -r requirements.txt
    ```

- O comando acima importará as bibliotecas "request" e "os" utilizadas no projeto
- Execute o primeiro codigo (DEPESAS_SCRAPING.py)
- Este codigo fara a raspagem dos dados e a criação dos arquivos para analise
- Posteriormente importe as bibliotecas pandas e matplotlib e execute o segundo codigo (ANALISE_DAS_DESPESAS.py)
- Este é o codigo que fara o tratamento e a impressão dos dados ao usuario, instruções são exibidas durante a execução.

### Back End:

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

### Disciplinas:

- Engenharia de Software - Profº Giuliano Bertoti.
- Linguagem de Programação I - Profª Adriana Jacinto.
- Laboratório de Desenvolvimento em Banco de Dados II - Profª Adriana Jacinto.
- Arquitetura e Modelagem de Banco de Dados - Profº Emanuel Mineda.

### Equipe:

[Felipe Santos](https://gitlab.com/felipefsc)

[Gabriel Angelo](https://gitlab.com/Angelog)

[Nathan Nascimento](https://gitlab.com/N4htan)

### LEVANTAMENTO DE REQUISITOS

![image](https://user-images.githubusercontent.com/19509794/142543911-364a1b41-8d61-49fe-9a67-ff16a37f4f69.png)
![image](https://user-images.githubusercontent.com/19509794/142544009-4a450d42-4ff8-4277-a6b8-bc685ce68148.png)
![image](https://user-images.githubusercontent.com/19509794/142544119-a947b6e8-79cb-4f0e-99c9-2ef4d93bdf82.png)
![image](https://user-images.githubusercontent.com/19509794/142544251-9cdff6f8-1ab9-45d5-8626-2c6dc379f2af.png)
![image](https://user-images.githubusercontent.com/19509794/142544366-f5ce6f29-30ff-4b9f-8432-4cf12504dbdd.png)
![image](https://user-images.githubusercontent.com/19509794/142544598-4b5538c3-1497-4c20-83db-2a802ddbc0db.png)
![image](https://user-images.githubusercontent.com/19509794/142544746-4aa3199f-d5e1-43c1-8f62-37924ca0d87d.png)
![image](https://user-images.githubusercontent.com/19509794/142544824-b87e6776-637a-4e5f-8249-fa1c0b9d0473.png)
![image](https://user-images.githubusercontent.com/19509794/142545011-3b3bacf2-08ac-4426-805c-0f342012d944.png)
![image](https://user-images.githubusercontent.com/19509794/142545099-a7dd88b6-d263-4e86-ae0f-4934d11b2da3.png)
![image](https://user-images.githubusercontent.com/19509794/142545187-5505337a-3d31-46e1-9ac1-0b07080e4e3c.png)

### Como Instalar o git na máquina:


- Abra o terminal clicando dentro de uma pasta com o botão direito e selecione a opção git bash here
- Utilize a função git clone https://gitlab.com/projeto-II/OEP.git para instalar os arquivos no seu computador

### Referências


- Editor Html: www.w3schools.com/html/tryit.asp?filename=tryhtml_default
- Diagramas Gantt:
https://frappe.io/gantt
https://developers.google.com/chart/interactive/docs/gallery/ganttchart

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

<p align="center">O projeto integrador consiste na criação de uma aplicação web com dashboard. </p>

<p align="center">
   <a href="#-entregas">Entregas</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-sobre">Sobre o projeto</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-instalacao">Instalação e execução</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-tecnologias">Tecnologias</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-requisitos">Requisitos</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  
</p



### :heavy_check_mark: Entregas e Vídeos <a name="-entregas"/></a>


|  DATA  | SPRINT | Link do vídeo|
|--------|--------|--------------|
|  27-09 |   0    |       -       |
|  18-10 |   1    |[Video](https://www.youtube.com/watch?v=hSxAHHQWt9Q&feature=youtu.be)              |
|  08-11 |   2    |[Video](https://www.youtube.com/watch?v=6RoibaiDX_k&feature=youtu.be)              |
|  29-11 |   3    |[Video](https://youtu.be/us_hd_7H2kc)     |
|  14-12 |   4    |[Video](https://youtu.be/pS3nGC5DPVQ)|



### :page_with_curl: Sobre o projeto <a name="-sobre"/></a>

> É proposto o desenvolvimento de um Sistema de Recompensas dentro de uma aplicação do cliente. O cliente busca otimizar seu negócio através de uma dashbord, com as informações mais atrativas e impactantes para seus clientes. O cliente pode acompanhar seus respectivos dados de maneira segura e organizada, e caso necessário, e tomar a decisões a partir delas.

O objetivo do trabalho é reinventar a forma de aproximação do usuário da plataforma. Não consistindo na criação web de apenas consultas, mas sim em uma aplicação utilizando o sistema de recompensas, na qual o usuário poderá utiliza-los dentro da aplicação com o que o cliente poderá fornecer. As recompensas foram demostradas através de cursos que poderão auxiliar o usuário com a própria gestão financeira. 


### :memo: Referências <a name="-tecnologias"/></a> 

```
- Java, Html, Css, JavaScript
- frameworks: Spring Boot, Boostrap 
- banco de dados relacional: MySQL
```

### :memo: Levantamento de Requisitos <a name="-requisitos"/></a> 


> Criação de uma aplicação web com dashbord estatistica, com a linguagem principal utilizada sendo o Java.

> A aplicação deve conter um login. As informações apresentadas devem ser intuitivas pois trata-se de um ambiente com assuntos financeiros, ou seja, deve agregar pessoas bancarizadas e não bancarizadas. 

> A aplicação precisa agregar valor a um sistema já em andamento. A aproximação do cliente/usuário será realizada atraves da utilização de pontos e utilizar na "loja" virtual ambientalizada dentro do login de cada usuário.



### Requisitos Funcionais

| Requisitos funcionais               |Código|Descrição                                             | Prioridade | Sprint|
|-------------------------------------|------|------------------------------------------------------|------------|-------|
|Acesso ao score e dashboard          |RF05  |Acesso dos usuários o score gerado                    | 01         | 18/10 |
|Acesso ao sistema de pontos          |RF06  |Acesso a recompensa conforme variação do score        | 01         | 18/10 |
|Tratamento de dados                  |RF02  |Organização dos dados forneceidos                     | 02         | 08/11 |
|Comunicação com o Banco de dados     |RF07  |Comunicação com o dataset fornecido pelo cliente      | 02         | 08/11 |
|Sistema de Recompenas                |RF03  |Disponibilidade de recursos da recompensas de pontos  | 03         | 29/11 |
|Modificar informações pontos         |RF04  |Alteração de pontos pelo sistema de recompensas       | 03         | 29/11 |
|Cadastro de usuários                 |RF01  |Registro de novos usuários (Pessoa juridica e física) | 02         | 08/11 |



### Requisitos não funcionais

| Requisitos não funcionais           |Código|Descrição                                                                    | 
|-------------------------------------|-------|----------------------------------------------------------------------------|
|Documentação do produto              |RNF01  | Documentação do código/Utilização das informações                          |
|Autenticação de usuário              |RNF02  |Verificar autenticidade do usuário                                          |
|Usabilidade                          |RNF03  |Estética e Design minimalista (aplicação web)                               |
|Visibilidade do status do sistema    |RNF04  |As informações serão apresentadas de forma organizadas, intuitiva e amigável|
|Consistência e padrões               |RNF05  |Consistência e padrões na apresentação das informações                      |    
|Portabilidade                        |RNF06  |A consulta deve estar disponivel nos principais navegadores disponíveis     |
|Acesso de segurança                  |RNF07  |Acesso seguro das informações                                               |     
|Responsividade                       |RNF08  |Velocidade de resposta e tempo de atualização de tela                       |      


### :computer: Instalação e execução <a name="-instalacao"/></a>
1. Clonar a aplicação
2. Abrir a aplicação na IDE que desejar (Eclipse, IntelliJ, Spring Tool) 
3. Ajustar as configurações do banco de dados na Application.properties.
3. Rodar como JavaApplication
4. Abrir localhost:8080

Você também pode acompanhar através desse [link](https://gitlab.com/ferpsalles/kind-of-pi/-/blob/master/bd/MANUAL_PARA_RODAR_O_PROJETO_PELA_PRIMEIRA_VEZ.pdf)

### :computer: Visões do Usuário <a name="-visao"/></a>

1. Tela de login

![image](https://user-images.githubusercontent.com/19509794/142551407-77e48041-f2ab-479a-ac65-84deed0ac78a.png)

2. Tela de Cadastro

![image](https://user-images.githubusercontent.com/19509794/142551439-66b4ca89-3c29-4ee3-ac1c-8456bd337f1e.png)

3. Home View

![image](https://user-images.githubusercontent.com/19509794/142551465-aa3e6428-9c3a-4274-a3f9-1eafdc8c3703.png)

### :computer: Referências <a name="-referencias"/></a> 
1. https://spring.io/projects/spring-boot
2. https://www.chartjs.org/
3. https://www.mysql.com/



### :email: Contato
- Fernanda Ramos - [Gitlab](https://gitlab.com/ferpsalles) - [Linkedin](https://www.linkedin.com/in/fernanda-ramos-de-padua-salles-44329b157/)

- Gabriel Angelo - [Gitlab](https://gitlab.com/Angelog)- [Linkedin](https://www.linkedin.com/in/gabriel-angelo-a4b251116/)

- Nathan Nascimento - [Gitlab](https://gitlab.com/n4htan)- [Linkedin](https://www.linkedin.com/in/n4htan/)

- Vitor Daniel Silva - [Gitlab](https://gitlab.com/VitorDan)- [Linkedin](https://www.linkedin.com/in/vitor-daniel-9343bb150/)


### Agradecimentos

Agradecemos aos professores pelo suporte oferecido para o progresso do projeto.

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


## Instruções de implementação </br> <a name="-instrucao"/></a>

 > Crie o banco de dados 
 1. Utilizar o script SQL que está na pasta "API-Loading/projetointegrador/bd/bd.sql" para ter o modelo do banco.
 
 > Como rodar a aplicação:
 1. Alterar as configurações do banco de dados nos arquivos "bd.py" e "app.py"
 2. Para [configurar e executar o ambiente virtual](https://www.youtube.com/watch?v=hA2l0TgaZhM), a pasta do ambiente virtual criado para este projeto se encontra na pasta "venv" 
 4. Com o ambiente virtual ativado execute o arquivo "app.py"
 5. Recomendamos que utilize o software [Postman](https://www.postman.com/downloads/) para testar a rotas disponiveis no projeto.

# Requisitos</br> <a name="-requisitos"/></a>
## Requisitos Funcionais</br>

· Criar interface de submissão de currículos que recebam, de forma padronizada e adequada ao processo, os candidatos; </br>
· Busca de candidatos por vagas; </br>
· Utilizar filtros configuráveis nas buscas de cada vaga; </br>


## Requisitos Não Funcionais</br>
· Arquitetura do BD;</br>
· Desempenho;</br>
· Segurança (Safety);</br>
· Documentação específica;</br>


## Rotas Disponíveis <a name="-rotas"/></a>

|  ROTAS  CRUD | METHOD | RESPOSTA |
|--------|----------|----------|
| "/insertUsuario" | "POST" | Criação de usuários que são capazes de criar vagas |
| "/insertVaga | "POST" | Inserção de vaga no banco de dados|
| "/updateVaga/informe o id" | "PUT" | Update das descrições da vaga |
| "/dropVaga/informe o id"| "DELETE" | Deletar Vaga |
| "/filterVaga/informe o id" | "GET" | Filtrar as informações da vaga |
| "/filterVaga" | "GET" | Listar todas as vagas disponíveis | 
| "/filterVagaPeso/informe o id" | "GET" | Filtro da vaga retornando os candidatos | 
| "/insertCandidato" | "POST" | Inserir candidatos |
| "/updateCandidato/informe o cpf" | "PUT" | Atualização dos dados do candidato |
| "/dropCandidato/informe o cpf"| "DELETE" | Deletar candidato |
| "/filterCandidato/cep=informe o cep" | "GET" | Filtra candidatos |
| "/filterCandidato" | "GET" | Filtrar todos os candidatos | 

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
