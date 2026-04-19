# Semana 7 — JOINs (Parte 2) e Operações de Conjunto

Nesta semana, vamos aprofundar o uso de JOINs e aprender **operações de conjunto**, que permitem combinar resultados de diferentes consultas.

Esses conceitos são úteis para:
- Comparar tabelas
- Unir resultados
- Encontrar diferenças entre conjuntos de dados

## RIGHT JOIN

O `RIGHT JOIN` retorna todos os registros da tabela da direita, mesmo que não haja correspondência na tabela da esquerda.

### Estrutura:

```sql
SELECT *
FROM tabela1
RIGHT JOIN tabela2
ON tabela1.coluna = tabela2.coluna;
```

👉 Mantém todos os dados da tabela da direita

---

## FULL JOIN

O `FULL JOIN` retorna todos os registros das duas tabelas, combinando quando há correspondência.

### Estrutura:

```sql
SELECT *
FROM tabela1
FULL JOIN tabela2
ON tabela1.coluna = tabela2.coluna;
```

👉 Retorna tudo das duas tabelas (com NULL quando não há correspondência)

---

## UNION

O `UNION` combina resultados de duas consultas, removendo duplicatas.

### Estrutura:

```sql
SELECT coluna
FROM tabela1

UNION

SELECT coluna
FROM tabela2;
```

👉 Une os resultados sem repetir valores

---

## UNION ALL

Semelhante ao UNION, mas mantém duplicatas.

### Estrutura:

```sql
SELECT coluna
FROM tabela1

UNION ALL

SELECT coluna
FROM tabela2;
```

👉 Mantém todos os registros, inclusive repetidos

---

## INTERSECT

O `INTERSECT` retorna apenas os valores que estão presentes em ambas as consultas.

### Estrutura:

```sql
SELECT coluna
FROM tabela1

INTERSECT

SELECT coluna
FROM tabela2;
```

👉 Retorna apenas os dados em comum

---

## EXCEPT

O `EXCEPT` retorna os valores da primeira consulta que não estão na segunda.

### Estrutura:

```sql
SELECT coluna
FROM tabela1

EXCEPT

SELECT coluna
FROM tabela2;
```

Retorna diferenças entre conjuntos

---

##  Cuidados importantes

- Para usar UNION, INTERSECT e EXCEPT, as consultas devem ter o mesmo número de colunas
- Os tipos de dados devem ser compatíveis
- UNION remove duplicatas automaticamente
- UNION ALL é mais performático quando duplicatas não são problema
- Nem todos os bancos suportam INTERSECT e EXCEPT (ex: MySQL)

---

## Prática

##1 - Comparar resultados obtidos com diferentes tipos de JOIN

```sql
SELECT 
    c.customer_id,
    o.order_id
FROM olist_customers_dataset c
INNER JOIN olist_orders_dataset o
    ON c.customer_id = o.customer_id; 
  
```

![Resultado filtro estado](https://github.com/ThamaraCrispim/panda-sql-study-group/blob/main/Imagem/Semana%2007.1.1.png)


```sql
SELECT 
    c.customer_id,
    o.order_id
FROM olist_customers_dataset c
LEFT JOIN olist_orders_dataset o
    ON c.customer_id = o.customer_id; 
  
```

![Resultado filtro estado](https://github.com/ThamaraCrispim/panda-sql-study-group/blob/main/Imagem/Semana%2007.1.2.png)

Resultado: O INNER JOIN retorna apenas os clientes que possuem pedidos, enquanto o LEFT JOIN retorna todos os clientes, incluindo aqueles sem pedidos (com valores NULL). 

##2 - Unir resultados de diferentes consultas de clientes

```sql
SELECT customer_id, customer_state
FROM olist_customers_dataset
WHERE customer_state = 'SP'

UNION

SELECT customer_id, customer_state
FROM olist_customers_dataset
WHERE customer_state = 'RJ';
```

Resultado: A consulta uniu os clientes dos estados de SP e RJ, removendo possíveis duplicidades entre os resultados.

![Resultado filtro estado](https://github.com/ThamaraCrispim/panda-sql-study-group/blob/main/Imagem/Semana%2007.1.png)

##3 - Identificar registros presentes em uma tabela e ausentes em outra

```sql
SELECT 
    c.customer_id
FROM olist_customers_dataset c
LEFT JOIN olist_orders_dataset o
    ON c.customer_id = o.customer_id
WHERE o.order_id IS NULL;
```

Resultado: Foram identificados os clientes que não possuem pedidos cadastrados, utilizando LEFT JOIN e filtrando os registros sem correspondência (NULL)

![Resultado filtro estado](https://github.com/ThamaraCrispim/panda-sql-study-group/blob/main/Imagem/Semana%2007.2.png)

##4 - Encontrar produtos que nunca apareceram em pedidos

```sql
SELECT 
    p.product_id,
    p.product_category_name
FROM olist_products_dataset p
LEFT JOIN olist_order_items_dataset oi
    ON p.product_id = oi.product_id
WHERE oi.product_id IS NULL;
```

Resultado: A consulta retornou os produtos que nunca foram vendidos, ou seja, que não aparecem na tabela de itens de pedidos.

![Resultado filtro estado](https://github.com/ThamaraCrispim/panda-sql-study-group/blob/main/Imagem/semana%2007.4.png)


