# Semana 6 — Relacionamentos e JOINs (Parte 1)

Nesta semana, vamos aprender a **relacionar tabelas**, um dos conceitos mais importantes em bancos de dados relacionais.

Na prática, os dados raramente estão em uma única tabela. Por isso, precisamos conectar informações como:
- Clientes
- Pedidos
- Pagamentos

---

## Chave Primária e Estrangeira

### 💡 Ideia principal

As tabelas se conectam através de **chaves**.

- **Chave Primária (Primary Key)** → identifica unicamente cada registro  
- **Chave Estrangeira (Foreign Key)** → faz a ligação com outra tabela  

### Exemplo conceitual:

- Tabela `customers`
  - `customer_id` (chave primária)

- Tabela `orders`
  - `customer_id` (chave estrangeira)

👉 Isso permite relacionar pedidos com clientes

---

## INNER JOIN

O `INNER JOIN` retorna apenas os registros que possuem correspondência em ambas as tabelas.

### Estrutura:

```sql
SELECT *
FROM tabela1
INNER JOIN tabela2
ON tabela1.coluna = tabela2.coluna;
```

👉 Retorna apenas dados que existem nas duas tabelas

---

## LEFT JOIN

O `LEFT JOIN` retorna todos os registros da tabela da esquerda, mesmo que não haja correspondência na tabela da direita.

### Estrutura:

```sql
SELECT *
FROM tabela1
LEFT JOIN tabela2
ON tabela1.coluna = tabela2.coluna;
```

👉 Retorna todos da tabela principal + correspondências (ou NULL)

---


## Prática

Utilizando o dataset **Brazilian E-Commerce Public Dataset by Olist**, realize as seguintes consultas:

## 1 - Relacionar clientes com seus pedidos


## 2 - Relacionar pedidos com informações de pagamento

## 3 - Identificar pedidos que possuem clientes cadastrados


## 4 - Listar todos os clientes, incluindo aqueles que não possuem pedidos

