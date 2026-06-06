# Semana 8 — Subconsultas (Subqueries)

Nesta semana, estudamos **Subconsultas (Subqueries)**, que são consultas SQL executadas dentro de outras consultas.

As subqueries permitem criar análises mais avançadas, como comparar valores com médias, calcular participações percentuais e utilizar resultados intermediários como tabelas temporárias.

---

## Subquery no WHERE (IN, EXISTS)

Uma subconsulta pode ser utilizada para filtrar registros com base no resultado de outra consulta.

### Exemplo

```sql
SELECT *
FROM tabela
WHERE coluna IN (
    SELECT coluna
    FROM outra_tabela
);
```

---

## Subquery no SELECT

Permite adicionar valores calculados diretamente no resultado da consulta.

### Exemplo

```sql
SELECT
    coluna,
    (
        SELECT AVG(coluna)
        FROM tabela
    ) AS media
FROM tabela;
```

---

## Subquery no FROM (Tabela Derivada)

Permite utilizar uma consulta como uma tabela temporária.

### Exemplo

```sql
SELECT *
FROM (
    SELECT coluna
    FROM tabela
) AS subconsulta;
```

---

## Prática

### 1 - Encontrar pedidos com valor acima da média de pagamentos

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

Resultado: A consulta retornou os pedidos cujo valor de pagamento é superior à média dos pagamentos registrados na base.

![Resultado prática 1](COLE_AQUI_O_LINK_DA_IMAGEM)

---

### 2 - Calcular o total de vendas por produto e a porcentagem de participação de cada produto nas vendas

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

Resultado: A consulta calculou o valor total vendido por produto e sua participação percentual em relação ao faturamento total da base.

![Resultado prática 2](COLE_AQUI_O_LINK_DA_IMAGEM)

---

### 3 - Utilizar uma subconsulta como tabela temporária para analisar vendas por produto

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

Resultado: Foi criada uma tabela derivada contendo o total vendido por produto. Em seguida, foram filtrados apenas os produtos com faturamento superior a R$ 1.000.

![Resultado prática 3](COLE_AQUI_O_LINK_DA_IMAGEM)

---

## Conclusão

Nesta atividade foram utilizadas subconsultas em diferentes contextos. As subqueries permitiram comparar pagamentos com a média da base, calcular a participação de cada produto no faturamento total e criar tabelas temporárias para análise. Esses recursos são amplamente utilizados em análises de dados e consultas SQL mais avançadas.
