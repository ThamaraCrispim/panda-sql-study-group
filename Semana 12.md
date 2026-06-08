# Projeto Final — Análise de Dados do E-commerce Olist (Parte 2)

## Introdução

Na Parte 1 do projeto foram definidas perguntas de negócio para compreender melhor o comportamento dos clientes, produtos e vendas da plataforma Olist.

Nesta etapa, utilizaremos SQL para responder essas perguntas e gerar insights que possam auxiliar a tomada de decisão da empresa.

---

# Análise 1 — Estados com mais clientes

## Pergunta

Quais estados possuem mais clientes cadastrados?

## Consulta SQL

```sql
SELECT
    customer_state,
    COUNT(*) AS quantidade_clientes
FROM olist_customers_dataset
GROUP BY customer_state
ORDER BY quantidade_clientes DESC;
```

## Resultado

![Resultado prática 1](https://github.com/ThamaraCrispim/panda-sql-study-group/blob/main/Imagem/Captura%20de%20tela%202026-06-08%20103701.png)

## Insight


A análise mostra que São Paulo é o estado com mais clientes cadastrados na plataforma, seguido por Rio de Janeiro e Minas Gerais. 
Os resultados indicam uma forte concentração de clientes na região Sudeste, que representa uma parcela importante da base de consumidores da Olist.

# Análise 2 — Cidades com mais clientes

## Pergunta

Quais cidades possuem mais clientes cadastrados?

## Consulta SQL

```sql
SELECT
    customer_city,
    COUNT(*) AS quantidade_clientes
FROM olist_customers_dataset
GROUP BY customer_city
ORDER BY quantidade_clientes DESC
LIMIT 10;
```

## Resultado

(Adicionar print)

## Insight

A análise permite identificar os principais centros consumidores da plataforma.

---

# Análise 3 — Categorias com mais produtos

## Pergunta

Quais categorias possuem mais produtos cadastrados?

## Consulta SQL

```sql
SELECT
    product_category_name,
    COUNT(*) AS quantidade_produtos
FROM olist_products_dataset
GROUP BY product_category_name
ORDER BY quantidade_produtos DESC;
```

## Resultado

(Adicionar print)

## Insight

Categorias com maior quantidade de produtos tendem a possuir maior variedade para os consumidores.

---

# Análise 4 — Produtos mais vendidos

## Pergunta

Quais produtos apresentam maior quantidade de vendas?

## Consulta SQL

```sql
SELECT
    product_id,
    COUNT(*) AS quantidade_vendas
FROM olist_order_items_dataset
GROUP BY product_id
ORDER BY quantidade_vendas DESC
LIMIT 10;
```

## Resultado

(Adicionar print)

## Insight

Os produtos mais vendidos podem servir como referência para estratégias de estoque e recomendações.

---

# Análise 5 — Valor médio dos pagamentos

## Pergunta

Qual é o valor médio dos pagamentos realizados?

## Consulta SQL

```sql
SELECT
    ROUND(AVG(payment_value),2) AS media_pagamentos
FROM olist_order_payments_dataset;
```

## Resultado

(Adicionar print)

## Insight

O ticket médio ajuda a compreender o comportamento de compra dos clientes.

---

# Análise 6 — Estados com maior ticket médio

## Pergunta

Quais estados possuem o maior ticket médio?

## Consulta SQL

```sql
SELECT
    c.customer_state,
    ROUND(AVG(p.payment_value),2) AS ticket_medio
FROM olist_customers_dataset c
INNER JOIN olist_orders_dataset o
    ON c.customer_id = o.customer_id
INNER JOIN olist_order_payments_dataset p
    ON o.order_id = p.order_id
GROUP BY c.customer_state
ORDER BY ticket_medio DESC;
```

## Resultado

(Adicionar print)

## Insight

Estados com ticket médio elevado representam mercados de maior valor para a empresa.

---

# Análise 7 — Categorias com maior faturamento

## Pergunta

Quais categorias geram mais receita?

## Consulta SQL

```sql
SELECT
    p.product_category_name,
    ROUND(SUM(oi.price),2) AS faturamento
FROM olist_products_dataset p
INNER JOIN olist_order_items_dataset oi
    ON p.product_id = oi.product_id
GROUP BY p.product_category_name
ORDER BY faturamento DESC;
```

## Resultado

(Adicionar print)

## Insight

A análise identifica quais categorias possuem maior impacto no faturamento da empresa.

---

# Análise 8 — Evolução das vendas ao longo do tempo

## Pergunta

Como as vendas se comportam ao longo do tempo?

## Consulta SQL

```sql
SELECT
    YEAR(order_purchase_timestamp) AS ano,
    MONTH(order_purchase_timestamp) AS mes,
    COUNT(*) AS quantidade_pedidos
FROM olist_orders_dataset
GROUP BY ano, mes
ORDER BY ano, mes;
```

## Resultado

(Adicionar print)

## Insight

A análise permite identificar tendências de crescimento e possíveis sazonalidades.

---

# Conclusão

Através das consultas SQL foi possível transformar dados brutos em informações relevantes para o negócio. Foram identificados padrões de comportamento dos clientes, desempenho dos produtos e características das vendas.

Essas análises demonstram como SQL pode ser utilizado para apoiar decisões estratégicas e gerar valor para empresas que trabalham com grandes volumes de dados.

