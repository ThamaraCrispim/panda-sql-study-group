# 🗓 Cronograma de Estudos — SQL

O cronograma do grupo foi estruturado em **12 semanas de estudo**, combinando teoria e prática utilizando o dataset **Brazilian E-Commerce Public Dataset by Olist**.

Cada semana aborda um conjunto de conceitos fundamentais de SQL e exercícios aplicados para fixação do conteúdo.

---

## Semana 1 — Introdução e Ambiente

**O que estudar:**

- O que é SQL e bancos de dados relacionais
- Instalação do PostgreSQL e DBeaver (ou outro ambiente SQL)
- Conectando ao banco de dados
- Primeiro `SELECT`

**Prática:**

- Instalar os softwares
- Baixar o dataset
- Importar as tabelas no banco de dados
- Explorar as tabelas para entender as colunas e dados disponíveis

---

## Semana 2 — Consultas Básicas e Filtragem

**O que estudar:**

- `SELECT`
- `FROM`
- `AS` (alias)
- `WHERE`
- Operadores (`=`, `<>`, `>`, `<`, `>=`, `<=`)
- `AND`, `OR`, `NOT`
- `LIKE`, `IN`, `BETWEEN`

**Prática:**

- Filtrar clientes por estado
- Buscar produtos de uma categoria específica
- Filtrar pedidos entre dois valores ou datas
- Encontrar padrões em nomes de cidades ou categorias

---

## Semana 3 — Ordenação, Limites e Valores Nulos

**O que estudar:**

- `ORDER BY`
- `LIMIT`
- `OFFSET`
- `IS NULL`
- `IS NOT NULL`
- `COALESCE`

**Prática:**

- Ordenar pedidos do mais recente para o mais antigo
- Listar apenas uma quantidade limitada de registros
- Pular registros utilizando offset
- Identificar colunas com valores nulos
- Substituir valores nulos por valores padrão

---

## Semana 4 — Funções de String, Data e Matemática

**O que estudar:**

- `UPPER`, `LOWER`
- `CONCAT`
- `SUBSTR`
- `LENGTH`
- `EXTRACT`
- `DATE_PART`
- `ROUND`
- `ABS`
- `CAST`
- `COALESCE` e `NULLIF`

**Prática:**

- Padronizar nomes de cidades ou categorias
- Calcular ano ou mês das compras
- Calcular diferenças entre datas de pedido e entrega
- Arredondar valores de pagamento

---

## Semana 5 — Agregação e Agrupamento

**O que estudar:**

- `COUNT`
- `SUM`
- `AVG`
- `MIN`
- `MAX`
- `GROUP BY`
- Diferença entre `WHERE` e `HAVING`

**Prática:**

- Contar quantos pedidos existem no banco
- Calcular quantidade de clientes por estado
- Calcular média de valor de pagamento
- Identificar categorias com maior número de produtos
- Filtrar agrupamentos com condições específicas

---

## Semana 6 — Relacionamentos e JOINs (Parte 1)

**O que estudar:**

- Conceito de chave primária
- Chave estrangeira
- `INNER JOIN`
- `LEFT JOIN`

**Prática:**

- Relacionar clientes com seus pedidos
- Relacionar pedidos com informações de pagamento
- Identificar pedidos que possuem clientes cadastrados
- Listar clientes que não possuem pedidos

---

## Semana 7 — JOINs (Parte 2) e Operações de Conjunto

**O que estudar:**

- `RIGHT JOIN`
- `FULL JOIN`
- `UNION`
- `UNION ALL`
- `INTERSECT`
- `EXCEPT`

**Prática:**

- Comparar resultados de diferentes tipos de JOIN
- Unir resultados de diferentes consultas
- Identificar registros presentes em uma tabela e ausentes em outra
- Encontrar produtos que nunca apareceram em pedidos

---

## Semana 8 — Subconsultas (Subqueries)

**O que estudar:**

- Subquery no `WHERE`
- `IN` e `EXISTS`
- Subquery no `SELECT`
- Subquery no `FROM`

**Prática:**

- Encontrar pedidos com valor acima da média
- Calcular participação de produtos nas vendas
- Utilizar subconsultas como tabelas temporárias

---

## Semana 9 — Manipulação de Dados (DML)

**O que estudar:**

- `INSERT`
- `UPDATE`
- `DELETE`

**Prática:**

- Criar uma tabela de testes
- Inserir novos registros
- Atualizar informações existentes
- Remover registros incorretos ou duplicados

---

## Semana 10 — Criação e Alteração de Estruturas (DDL)

**O que estudar:**

- `CREATE TABLE`
- `ALTER TABLE`
- `PRIMARY KEY`
- `FOREIGN KEY`
- `NOT NULL`, `UNIQUE`, `DEFAULT`
- `DROP TABLE`

**Prática:**

- Modelar um sistema simples inspirado no dataset
- Criar tabelas para clientes, produtos e pedidos
- Definir chaves primárias e estrangeiras
- Alterar tabelas adicionando novas colunas ou restrições

---

## Semana 11 — Projeto Final (Parte 1)

**Objetivo:**

- Entender o problema de negócio
- Explorar o banco de dados
- Identificar relações entre tabelas
- Definir perguntas de análise
- Planejar consultas SQL

---

## Semana 12 — Projeto Final (Parte 2)

**Objetivo:**

- Aplicar todos os conceitos aprendidos
- Finalizar consultas SQL
- Gerar análises sobre vendas, clientes e produtos
- Organizar os resultados
- Apresentar os insights encontrados
