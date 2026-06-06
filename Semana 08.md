# Semana 8 — Subconsultas (Subqueries)

Nesta semana, vamos aprender sobre **Subconsultas (Subqueries)**.

Uma subconsulta é uma consulta SQL que fica dentro de outra consulta. Ela permite utilizar o resultado de uma consulta para ajudar na execução de outra.

As subqueries são muito utilizadas quando precisamos:

* Comparar registros com médias ou totais.
* Filtrar dados utilizando informações de outra consulta.
* Criar tabelas temporárias para realizar análises.
* Construir consultas mais avançadas.

---

## Subquery no WHERE

A subquery é utilizada para criar condições de filtragem.

Exemplo:

```sql
SELECT *
FROM tabela
WHERE valor >
(
    SELECT AVG(valor)
    FROM tabela
);
```

Nesse caso, a subconsulta calcula a média dos valores e a consulta principal retorna apenas os registros acima dessa média.

---

## Subquery no SELECT

A subquery pode ser utilizada para adicionar informações calculadas diretamente no resultado da consulta.

Exemplo:

```sql
SELECT
    produto,
    (
        SELECT AVG(preco)
        FROM produtos
    ) AS media_geral
FROM produtos;
```

---

## Subquery no FROM (Tabela Derivada)

Também é possível utilizar o resultado de uma consulta como se fosse uma tabela temporária.

Exemplo:

```sql
SELECT *
FROM
(
    SELECT produto,
           SUM(vendas) AS total_vendas
    FROM vendas
    GROUP BY produto
) AS vendas_produto;
```

Essa técnica é conhecida como **tabela derivada**.

---

# Prática

## 1 - Encontrar pedidos com valor acima da média de pagamentos

```sql
SELECT
    order_id,
    payment_value
FROM olist_order_payments_dataset
WHERE payment_value >
(
    SELECT AVG(payment_value)
    FROM olist_order_payments_dataset
);
```

Resultado: A consulta retornou os pedidos cujo valor de pagamento é superior à média dos pagamentos registrados na base de dados.

![Resultado prática 1](https://github.com/ThamaraCrispim/panda-sql-study-group/blob/main/Imagem/Semana%2008.png)

---

## 2 - Calcular o total de vendas por produto e a porcentagem de participação de cada produto nas vendas

```sql
SELECT
    product_id,
    SUM(price) AS total_vendas,
    ROUND(
        SUM(price) * 100 /
        (
            SELECT SUM(price)
            FROM olist_order_items_dataset
        ),
        2
    ) AS participacao_percentual
FROM olist_order_items_dataset
GROUP BY product_id
ORDER BY total_vendas DESC;
```

Resultado: A consulta calculou o valor total vendido por produto e a participação percentual de cada produto em relação ao faturamento total.

![Resultado prática 3](https://github.com/ThamaraCrispim/panda-sql-study-group/blob/main/Imagem/Semana%2008%20P2.png)
---

## 3 - Utilizar uma subconsulta como tabela temporária para analisar pedidos ou pagamentos

```sql
SELECT *
FROM
(
    SELECT
        product_id,
        SUM(price) AS total_vendas
    FROM olist_order_items_dataset
    GROUP BY product_id
) vendas
WHERE total_vendas > 1000
ORDER BY total_vendas DESC;
```

Resultado: Foi criada uma tabela temporária contendo o total vendido por produto. Em seguida, foram selecionados apenas os produtos com vendas superiores a R$ 1.000.

![Resultado prática 3](https://github.com/ThamaraCrispim/panda-sql-study-group/blob/main/Imagem/Semana%2008.P3.png)

