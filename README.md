# PROVA_BD
 PROVA BANCO DE DADOS
# Resolução da Prova Prática Banco de Dados

## 1ª Questão
Faça um comando SQL para matricular o aluno "Pedro César" no  curso de informática. Os dados devem ser inseridos na tabela TB_MATRÍCULA.

```sql
select * from tb_aluno
insert into tb_aluno(codigo_aluno, nome_aluno, ano_nasc, email, sexo)
values ('4', 'Pedro César', '1995-06-04', 'pedro@provaSQL.com.br', 'M')
select * from tb_matricula
insert into tb_matricula(codigo_curso, codigo_aluno)
values ('4', '4')
```
## Resultado 

![q1](https://user-images.githubusercontent.com/114403979/206186429-af1a1a67-b402-4d8d-9c29-eb38b7826505.png)
<br/>
![q1](https://user-images.githubusercontent.com/114403979/206186442-0047b5c9-f95d-4b70-99e5-2033b8503a11.png)


## 2ª Questão
Escreva um comando SQL que retorne os nomes dos alunos e do(s) cursos em que estão matriculados. Os dados deverão estar ordenados pelo nome do curso.  

```sql
select tb_aluno.nome_aluno, tb_curso.nome_curso
from tb_aluno
inner join tb_matricula
on tb_aluno.codigo_aluno = tb_matricula.codigo_aluno
inner join tb_curso
on tb_curso.codigo_curso = tb_matricula.codigo_curso
```
## Resultado 

![q2](https://user-images.githubusercontent.com/114403979/206186499-aa04cc46-34ac-4e64-b51f-1843522f754f.png)


## 3ª Questão
Crie um comando SQL que retorne o e-mail de todos os alunos maiores de idade.

```sql
select email
from tb_aluno where 2022 - ano_nasc >= 18
```
## Resultado 

![q3](https://user-images.githubusercontent.com/114403979/206186533-a190cc9f-05e8-4611-a4ea-f29c2c64f3d8.png)


## 4ª Questão
Desenvolva um comando SQL que mostre o total de alunos.

```sql
select count(codigo_aluno)
from tb_aluno
```
## Resultado 

![q4](https://user-images.githubusercontent.com/114403979/206186568-aa8d2e99-5bd3-437c-a59c-e5c1cbec1640.png)


## 5ª Questão
Escreva um comando SQL para listar o total de alunos matriculados em cada curso.

```sql
alter table tb_matricula
add codigo_matricula serial primary key 

select count(codigo_matricula) as totalalunos from tb_matricula
```
## Resultado 


![q5](https://user-images.githubusercontent.com/114403979/206186607-70f17862-97dd-4c9e-8318-ca044ccb31a5.png)

## 6ª Questão
Desenvolva um comando SQL que retorne o nome de todos os alunos maiores que 18 anos.

```sql
select nome_aluno
from tb_aluno where 2022 - ano_nasc >= 18
```
## Resultado 

![g6](https://user-images.githubusercontent.com/105735037/206178292-be49f604-890b-494c-9a4b-07f093e433c1.PNG)

## 7ª Questão
Faça um comando SQL que retorne o nome de todas as mulheres. 

```sql
select nome_aluno, sexo
from tb_aluno where sexo = 'F'
```
## Resultado 

![q7](https://user-images.githubusercontent.com/114403979/206186706-6570fca1-5caa-41d0-8a2f-c71fc50761dd.png)


## 8ª Questão
Faça um comando SQL que retorne o nome de todas as mulheres matriculadas no curso de Medicina.

```sql
select tb_aluno.nome_aluno as mulheres_em_medicina
from tb_aluno
inner join tb_matricula
on tb_matricula.codigo_aluno = tb_aluno.codigo_aluno
and tb_matricula.codigo_curso = 1
and tb_aluno.sexo = 'F'
```
## Resultado 

![q8](https://user-images.githubusercontent.com/114403979/206186751-fd47532f-a7c7-4ba0-ac4a-5aa069914f5b.png)


## 9ª Questão
Faça um comando SQL que retorne os nomes dos cursos ordenados por ordem alfabética.

```sql
select nome_curso
from tb_curo order by nome_curso asc
```
## Resultado 

![q9](https://user-images.githubusercontent.com/114403979/206186768-c63918de-50f1-41da-a721-61b891b4f73e.png)

## 10ª Questão
Crie o enunciado de uma consulta SQL que utiliza "junção" (com resposta).

```sql
select ano_nasc,tb_curso.nome_curso,tb_aluno.nome_aluno
from tb_aluno
inner join tb_curso
on tb_aluno.cod_aluno = tb_curso.cod_curso
order by nome_curso asc 
```
## Resultado 
![g10](https://user-images.githubusercontent.com/104003510/206247087-8d9edbac-8794-418b-b4c2-034bb61a5c69.jpg)

# Resolução da Prova Teórica

## 1ª Questão
### Defina: SQL.
#### SQL significa “Structured Query Language”, ou “Linguagem de Consulta Estruturada”, em português. É uma linguagem de computador para trabalhar com conjuntos de fatos e as relações (baseado em tabelas) entre eles.

## 2ª Questão
### Faça um relacionamento cronológico sobre SQL.
#### A linguagem SQL surgiu em meados da década de 1970 como trabalho de E. F. Codd, membro do IBM Research Laboratory em San Jose, Califórnia. O foco desta pesquisa é desenvolver uma linguagem que acomode o modelo relacional. Os primeiros sistemas de banco de dados baseados em SQL foram comercializados no final dos anos 70 junto com outros sistemas de banco de dados relacionais. O sucesso da linguagem SQL foi tão grande que obrigou o ANSI (American National Standards Institute) a padronizar a implementação da linguagem, então agora a maioria dos BDs segue essa padronização com muito cuidado e pode haver algumas mudanças, mais Não afeta o global padronização da linguagem, facilitando a portabilidade se os DBAs a seguirem corretamente. Em 1982, foi lançada a primeira versão padronizada da linguagem SQL. Com seu desenvolvimento e aprimoramento contínuo, tornou-se a mais poderosa ferramenta para definição e operação de bancos de dados. Atualmente é utilizada na maioria dos bancos de dados existentes, como MySQL, SQLServer, Firebird entre outros.

## 3ª Questão
### Liste as principais características de SQL.
#### SQL é uma linguagem padrão para trabalhar com bancos de dados relacionais. É uma linguagem declarativa que não requer conhecimento profundo de programação para começar a escrever consultas. A linguagem SQL é utilizada de forma relativamente semelhante nos principais bancos de dados relacionais do mercado: Oracle, MySQL, MariaDB, PostgreSQL, Microsoft SQL Server e muitos outros. Cada um tem suas próprias características, e o MySQL e o PostgreSQL são muito populares porque possuem versões gratuitas e de código aberto.

## Questão 4:
### Descreva a sintaxe do comando SQL: SELECT. Quais cláusulas são obrigatórias e quais são opcionais?
#### O comando SELECT é usado para extrair dados de tabelas no banco de dados. Ele pode extrair dados de uma ou mais tabelas ao mesmo tempo, executar consultas simples a comandos mais complexos, realizar pesquisas, junções, comparações, filtragem, classificação e muitos outros itens.

## Questão 5:
### Qual a importância da linguagem SQL no desenvolvimento de softwares atualmente? Justifique.
#### O SQL Server, criado pela Microsoft, é amplamente conhecido e utilizado no mercado. A linguagem utilizada por esta ferramenta é o T-SQL, que disponibiliza recursos avançados e diferenciados para facilitar a atualização dos dados e o armazenamento seguro e confiável das informações. O SQL Server trabalha com sistema de criptografia integrado, permitindo que a visualização ou alteração das informações seja feita apenas pelos responsáveis, o que garante mais segurança e tranquilidade aos usuários e lojistas. É uma alternativa comumente utilizada em lojas online, órgãos governamentais, bancos e indústrias de todos os portes.
