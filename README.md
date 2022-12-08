# PROVA_PG
 Prova Banco de Dados
# Resolução da Prova Prática Banco de Dados

## 1ª Questão
Execute um comando SQL para matricular o aluno "Pedro César" no curso de informática. Os dados devem ser inseridos na tabela TB_MATRICULA.

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
Digite um comando SQL que retorne os nomes dos alunos e os cursos em que estão matriculados. Os dados devem ser classificados por nome do curso.  

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
Crie um comando SQL que retorne os endereços de e-mail de todos os alunos maiores de idade.

```sql
select email
from tb_aluno where 2022 - ano_nasc >= 18
```
## Resultado 

![q3](https://user-images.githubusercontent.com/114403979/206186533-a190cc9f-05e8-4611-a4ea-f29c2c64f3d8.png)


## 4ª Questão
Desenvolva um comando SQL que exiba o número total de alunos.

```sql
select count(codigo_aluno)
from tb_aluno
```
## Resultado 

![q4](https://user-images.githubusercontent.com/114403979/206186568-aa8d2e99-5bd3-437c-a59c-e5c1cbec1640.png)


## 5ª Questão
Escreva um comando SQL para listar o número total de alunos matriculados em cada curso.

```sql
select tb_curso.nome_curso,
codigo_curso + codigo_aluno as numero_alunos
from tb_curso
inner join tb_aluno
on tb_aluno.codigo_aluno = tb_curso.codigo_curso
```
## Resultado 


![q5](https://user-images.githubusercontent.com/114403979/206186607-70f17862-97dd-4c9e-8318-ca044ccb31a5.png)

## 6ª Questão
Desenvolva uma comando SQL que retorne os nomes de todos os alunos com mais de 18 anos.

```sql
select nome_aluno
from tb_aluno where 2022 - ano_nasc >= 18
```
## Resultado 

![02](https://user-images.githubusercontent.com/105735037/206178292-be49f604-890b-494c-9a4b-07f093e433c1.PNG)

## 7ª Questão
Faça um comando SQL que retorne o nome de todas as mulheres. 

```sql
select nome_aluno, sexo
from tb_aluno where sexo = 'F'
```
## Resultado 

![q7](https://user-images.githubusercontent.com/114403979/206186706-6570fca1-5caa-41d0-8a2f-c71fc50761dd.png)


## 8ª Questão
Faça um comando SQL que exiba o nome de todas as mulheres matriculadas no curso de Medicina.

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
