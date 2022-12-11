# PROVA_BD
 PROVA BANCO DE DADOS
 ### aluno: Pedro Cauã Rodrigues Saraiva
 
## Criando o Banco de Dados

```
create database provabd
```

## Criando as Tabelas

#### Criando a tabela 'tb_aluno'

```
create table tb_aluno( 

codigo_aluno integer primary key, 

nome_aluno varchar(60) not null, 

ano_nascimento int, 

email varchar(60), 

sexo varchar not null )  
```
#### Criando a tabela 'tb_curso'

```
create table tb_curso( 

codigo_curso integer primary key, 

nome_curso varchar(60) not null ) 
```
#### Criando a tabela 'tb_matricula'

```
create table tb_matricula( 

codigo_curso integer, 

codigo_aluno integer) 


alter table tb_matricula

add constraint fk_codigo_curso foreign  key (codigo_curso) references tb_curso(codigo_curso) 

add constraint fk_codigo_aluno foreign  key (codigo_aluno) references tb_aluno(codigo_aluno) 
```
## Inserindo os dados

#### Inserindo os dados da tabela 'tb_aluno'

```
insert into tb_aluno (codigo_aluno, nome_aluno, ano_nascimento, email, sexo) 

values (3, 'João Pedro', 1979, 'joao@provasql.com.br', 'M') 
```

#### Inserindo os dados da tabela 'tb_curso'

```
insert into tb_curso (codigo_curso, nome_curso) 

values (1, ‘MEDICINA’) 
```

#### Inserindo os dados da tabela 'tb_matricula

```
insert into tb_matricula (codigo_curso, codigo_aluno)  

values (1, 1) 
```
 
## Resolução da Prova Prática Banco de Dados

### 1ª Questão
Faça um comando SQL para matricular o aluno "Pedro César" no  curso de informática. Os dados devem ser inseridos na tabela TB_MATRÍCULA.

```sql
select * from tb_aluno
insert into tb_aluno(codigo_aluno, nome_aluno, ano_nasc, email, sexo)
values ('4', 'Pedro César', '1995-06-04', 'pedro@provaSQL.com.br', 'M')
select * from tb_matricula
insert into tb_matricula(codigo_curso, codigo_aluno)
values ('4', '4')
```
###  Resultado 

![q1](https://user-images.githubusercontent.com/114403979/206186429-af1a1a67-b402-4d8d-9c29-eb38b7826505.png)
<br/>
![q1](https://user-images.githubusercontent.com/114403979/206186442-0047b5c9-f95d-4b70-99e5-2033b8503a11.png)


### 2ª Questão
Escreva um comando SQL que retorne os nomes dos alunos e do(s) cursos em que estão matriculados. Os dados deverão estar ordenados pelo nome do curso.  

```sql
select tb_aluno.nome_aluno, tb_curso.nome_curso
from tb_aluno
inner join tb_matricula
on tb_aluno.codigo_aluno = tb_matricula.codigo_aluno
inner join tb_curso
on tb_curso.codigo_curso = tb_matricula.codigo_curso
```
###  Resultado 

![q2](https://user-images.githubusercontent.com/114403979/206186499-aa04cc46-34ac-4e64-b51f-1843522f754f.png)


###  3ª Questão
Crie um comando SQL que retorne o e-mail de todos os alunos maiores de idade.

```sql
select email
from tb_aluno where 2022 - ano_nasc >= 18
```
### Resultado 

![q3](https://user-images.githubusercontent.com/114403979/206186533-a190cc9f-05e8-4611-a4ea-f29c2c64f3d8.png)


###  4ª Questão
Desenvolva um comando SQL que mostre o total de alunos.

```sql
select count(codigo_aluno)
from tb_aluno
```
###  Resultado 

![q4](https://user-images.githubusercontent.com/114403979/206186568-aa8d2e99-5bd3-437c-a59c-e5c1cbec1640.png)


###  5ª Questão
Escreva um comando SQL para listar o total de alunos matriculados em cada curso.

```sql
alter table tb_matricula
add codigo_matricula serial primary key 

select count(codigo_matricula) as totalalunos from tb_matricula
```
###  Resultado 


![q5](https://user-images.githubusercontent.com/107321701/206524000-e43546ba-6096-4e5a-88ec-e16d01ca6712.png)

###  6ª Questão
Desenvolva um comando SQL que retorne o nome de todos os alunos maiores que 18 anos.

```sql
select nome_aluno
from tb_aluno where 2022 - ano_nasc >= 18
```
###  Resultado 

![g6](https://user-images.githubusercontent.com/105735037/206178292-be49f604-890b-494c-9a4b-07f093e433c1.PNG)

###  7ª Questão
Faça um comando SQL que retorne o nome de todas as mulheres. 

```sql
select nome_aluno, sexo
from tb_aluno where sexo = 'F'
```
###  Resultado 

![q7](https://user-images.githubusercontent.com/114403979/206186706-6570fca1-5caa-41d0-8a2f-c71fc50761dd.png)


###  8ª Questão
Faça um comando SQL que retorne o nome de todas as mulheres matriculadas no curso de Medicina.

```sql
select tb_aluno.nome_aluno as mulheres_em_medicina
from tb_aluno
inner join tb_matricula
on tb_matricula.codigo_aluno = tb_aluno.codigo_aluno
and tb_matricula.codigo_curso = 1
and tb_aluno.sexo = 'F'
```
###  Resultado 

![q8](https://user-images.githubusercontent.com/114403979/206186751-fd47532f-a7c7-4ba0-ac4a-5aa069914f5b.png)


###  9ª Questão
Faça um comando SQL que retorne os nomes dos cursos ordenados por ordem alfabética.

```sql
select nome_curso
from tb_curo order by nome_curso asc
```
###  Resultado 

![q9](https://user-images.githubusercontent.com/114403979/206186768-c63918de-50f1-41da-a721-61b891b4f73e.png)

###  10ª Questão
Crie o enunciado de uma consulta SQL que utiliza "junção" (com resposta).

```sql
select tb_aluno.nome_aluno, tb_curso.nome_curso from tb_aluno 
inner join tb_matricula on tb_aluno.codigo_aluno = tb_matricula.codigo_aluno
inner join tb_curso on tb_curso.codigo_curso = 1
```
###  Resultado 
![g10](https://user-images.githubusercontent.com/107321701/206525295-9e2ca16f-8dd5-4949-95af-5f47d9ee129b.png)

## Resolução da Prova Teórica

###  1ª Questão
### Defina: SQL.
![praticaQ1](https://user-images.githubusercontent.com/107321701/206526788-92bb93c9-6c7f-4bd1-a4ef-2afaf2505407.png)

SQL (Structured Query Language) é a linguagem padrão universal para manipular bancos de dados relacionais através dos SGBDs. Isso significa que todos os SGBDRs (Sistema de Gerenciamento de Banco de Dados Relacionais) oferecem uma interface para acessar o banco de dados utilizando a linguagem SQL, embora com algumas variações. A "Linguagem Estruturada de Consultas" (SQL, traduzida para o português) é utilizada para interagir com o SGBD e executar várias tarefas como inserir e alterar registros, criar objetos no banco de dados, gerenciar usuário, consultar informações, controlar transações, etc. Todas as operações realizadas no banco de dados podem ser solicitadas ao SGBD utilizando esta linguagem.

### 2ª Questão
### Faça um relacionamento cronológico sobre SQL.

A linguagem SQL surgiu em meados da década de 1970 como trabalho de E. F. Codd, membro do IBM Research Laboratory em San Jose, Califórnia. O foco desta pesquisa é desenvolver uma linguagem que acomode o modelo relacional. Os primeiros sistemas de banco de dados baseados em SQL foram comercializados no final dos anos 70 junto com outros sistemas de banco de dados relacionais. O sucesso da linguagem SQL foi tão grande que obrigou o ANSI (American National Standards Institute) a padronizar a implementação da linguagem, então agora a maioria dos BDs segue essa padronização com muito cuidado e pode haver algumas mudanças, mais Não afeta o global padronização da linguagem, facilitando a portabilidade se os DBAs a seguirem corretamente. Em 1982, foi lançada a primeira versão padronizada da linguagem SQL. Com seu desenvolvimento e aprimoramento contínuo, tornou-se a mais poderosa ferramenta para definição e operação de bancos de dados. Atualmente é utilizada na maioria dos bancos de dados existentes, como MySQL, SQLServer, Firebird entre outros.

![praticaQ2](https://user-images.githubusercontent.com/107321701/206527818-dc154127-26b4-409a-8b39-b65683bdc9a5.png)

### 3ª Questão
### Liste as principais características de SQL.
SQL é uma linguagem padrão para trabalhar com bancos de dados relacionais. É uma linguagem declarativa que não requer conhecimento profundo de programação para começar a escrever consultas. A linguagem SQL é utilizada de forma relativamente semelhante nos principais bancos de dados relacionais do mercado: Oracle, MySQL, MariaDB, PostgreSQL, Microsoft SQL Server e muitos outros. Cada um tem suas próprias características, e o MySQL e o PostgreSQL são muito populares porque possuem versões gratuitas e de código aberto.

![image](https://user-images.githubusercontent.com/107321701/206531691-cd79b20c-efd6-427b-8176-97129f954648.png)


### Questão 4:
### Descreva a sintaxe do comando SQL: SELECT. Quais cláusulas são obrigatórias e quais são opcionais?
O comando SELECT é usado para extrair dados de tabelas no banco de dados. Ele pode extrair dados de uma ou mais tabelas ao mesmo tempo, executar consultas simples a comandos mais complexos, realizar pesquisas, junções, comparações, filtragem, classificação e muitos outros itens. Além disso ele permite recuperar os dados de um objeto do banco de dados, como uma tabela, view e, em alguns casos, uma stored procedure (alguns bancos de dados permitem a criação de procedimentos que retornam valor). A sintaxe mais básica do comando é: definindo as colunas da tabela que queremos retornar com SELECT e o nome da tabela com FROM.

### Questão 5:
### Qual a importância da linguagem SQL no desenvolvimento de softwares atualmente? Justifique.
O SQL Server, criado pela Microsoft, é amplamente conhecido e utilizado no mercado. A linguagem utilizada por esta ferramenta é o T-SQL, que disponibiliza recursos avançados e diferenciados para facilitar a atualização dos dados e o armazenamento seguro e confiável das informações. O SQL Server trabalha com sistema de criptografia integrado, permitindo que a visualização ou alteração das informações seja feita apenas pelos responsáveis, o que garante mais segurança e tranquilidade aos usuários e lojistas. É uma alternativa comumente utilizada em lojas online, órgãos governamentais, bancos e indústrias de todos os portes. Quem quer trabalhar com desenvolvimento de softwares precisa aprender a SQL, pois a maioria dos sistemas de informação interage com banco de dados, e essa é a linguagem universal para fazer qualquer coisa nos bancos de dados relacionais (o tipo de banco de dados mais utilizado na industria). Pode haver pequenas variações na linguagem dependendo do SGBD, mas a sintaxe dos comandos são muito parecidas.
