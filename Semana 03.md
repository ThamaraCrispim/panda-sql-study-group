# Semana 3 — Ordenação, Limites e Valores Nulos

Nesta semana, vamos aprender a **organizar, limitar e tratar dados**, tornando as consultas mais úteis para análise.

Esses conceitos são essenciais quando trabalhamos com grandes volumes de dados, pois permitem:
- Ordenar resultados
- Visualizar apenas parte dos dados
- Lidar com valores ausentes (nulos)

---

## ORDER BY (Ordenação)

O comando `ORDER BY` é utilizado para ordenar os resultados de uma consulta.

Por padrão, a ordenação é crescente (`ASC`), mas também pode ser decrescente (`DESC`).

### Estrutura básica:

```sql
SELECT coluna
FROM tabela
ORDER BY coluna ASC;
```

### Explicação:
- `ORDER BY` → define a ordenação  
- `ASC` → ordem crescente (padrão)  
- `DESC` → ordem decrescente  

---

## LIMIT (Limitar resultados)

O comando `LIMIT` é utilizado para restringir a quantidade de linhas retornadas.

### Estrutura:

```sql
SELECT *
FROM tabela
LIMIT 10;
```

👉 Retorna apenas os 10 primeiros registros

---

## OFFSET (Pular registros)

O comando `OFFSET` é utilizado para pular uma quantidade de registros antes de começar a retornar resultados.

### Estrutura:

```sql
SELECT *
FROM tabela
LIMIT 10 OFFSET 5;
```

👉 Pula os 5 primeiros registros e retorna os próximos 10

---

## IS NULL e IS NOT NULL (Valores nulos)

Valores nulos representam a ausência de informação.

Para verificar esses valores, utilizamos:

### Estrutura:

```sql
WHERE coluna IS NULL
```

```sql
WHERE coluna IS NOT NULL
```

---

## COALESCE (Substituir valores nulos)

O comando `COALESCE` permite substituir valores nulos por um valor padrão.

### Estrutura:

```sql
SELECT COALESCE(coluna, valor_padrao)
FROM tabela;
```

👉 Se a coluna for NULL, será substituída pelo valor definido

---

## ⚠️ Cuidados importantes

- `ORDER BY` sempre vem após o `WHERE`
- `LIMIT` é aplicado após a ordenação
- `NULL` não pode ser comparado com `=` (use IS NULL)
- `COALESCE` é muito útil para análise e relatórios

---

## Prática

Utilizando o dataset **Brazilian E-Commerce Public Dataset by Olist**, realize as seguintes consultas:
### 1 - Ordenar pedidos do mais recente para o mais antigo

```sql
SELECT order_id, order_purchase_timestamp
FROM olist_orders_dataset
order by order_purchase_timestamp desc
```

Resultado:

A consulta retorna os pedidos ordenados do mais recente para o mais antigo, permitindo analisar o comportamento de compras ao longo do tempo.

![Resultado semana 03](https://github.com/ThamaraCrispim/panda-sql-study-group/blob/main/Imagem/semana%2003%20parte%201.png)

### 2 - Listar apenas uma quantidade limitada de registros


```sql
Select * 
from olist_customers_dataset
order by customer_zip_code_prefix desc
limit 10
```

Resultado:

A consulta ordena os clientes pelo código de CEP em ordem decrescente e retorna apenas os 10 primeiros registros, utilizando ORDER BY e LIMIT para restringir e organizar os dados.

![Resultado semana 03P1](https://github.com/ThamaraCrispim/panda-sql-study-group/blob/main/Imagem/Semana%2003%20parte%202.png)

### 3 - Pular um conjunto de registros e retornar os próximos


```sql
SELECT *
FROM olist_customers_dataset
limit 10 offset 5
```

Resultado:

![Resultado semana 03P1](https://github.com/ThamaraCrispim/panda-sql-study-group/blob/main/Imagem/semana%2003%20parte%203..png)


### 4 - Identificar colunas que possuem valores nulos


```sql
SELECT *
FROM olist_products_dataset
WHERE product_photos_qty IS NULL;
```

Resultado:

Como a consulta não retornou resultados, podemos afirmar que não existem valores nulos nessa coluna.

![Resultado semana 03P1](https://github.com/ThamaraCrispim/panda-sql-study-group/blob/main/Imagem/semana%2003%20parte%204.png)

### 5 - Substituir valores nulos por valores padrão

```sql
SELECT *
FROM olist_products_dataset
WHERE product_photos_qty IS NULL;
```

Resultado:

A análise mostra que a quantidade total de registros é igual à quantidade de valores não nulos, indicando que não existem valores nulos na coluna product_category_name.

![Resultado semana 03P1](https://github.com/ThamaraCrispim/panda-sql-study-group/blob/main/Imagem/semana%2003%20parte%205.png)

