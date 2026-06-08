# Semana 11 — Projeto Final (Parte 1)

## Introdução

A Olist é uma plataforma brasileira de e-commerce que conecta vendedores e consumidores por meio de marketplaces digitais.

Com milhares de pedidos realizados em diferentes regiões do Brasil, a empresa possui uma grande quantidade de dados sobre clientes, produtos, vendas, pagamentos e entregas.

O principal desafio de uma empresa desse porte é transformar dados em informações que auxiliem a tomada de decisão.

Neste projeto, o objetivo é explorar o banco de dados da Olist para entender melhor o comportamento dos clientes, o desempenho das vendas e as características dos produtos comercializados.

A partir dessa análise, será possível identificar oportunidades de melhoria e gerar insights para apoiar decisões estratégicas do negócio.

---

# Entendimento do Problema de Negócio

Imagine que você foi contratado como Analista de Dados da Olist.

A diretoria deseja entender melhor:

* Quem são os clientes da empresa.
* Quais produtos apresentam melhor desempenho.
* Como as vendas estão distribuídas pelo Brasil.
* Quais categorias possuem maior relevância para o negócio.
* Como os pagamentos estão se comportando.

Para responder essas perguntas, será necessário explorar o banco de dados e realizar análises utilizando SQL.

---

# Exploração Inicial das Tabelas

As principais tabelas utilizadas neste projeto são:

### Clientes

```sql
DESCRIBE olist_customers_dataset;
```

---

### Pedidos

```sql
DESCRIBE olist_orders_dataset;
```

---

### Produtos

```sql
DESCRIBE olist_products_dataset;
```

---

### Pagamentos

```sql
DESCRIBE olist_order_payments_dataset;
```

---

### Itens dos Pedidos

```sql
DESCRIBE olist_order_items_dataset;
```

---

# Relacionamento Entre as Tabelas

O banco de dados pode ser representado da seguinte forma:

```text
Clientes
    ↓
Pedidos
    ↓
Itens dos Pedidos
    ↓
Produtos

Pedidos
    ↓
Pagamentos
```

Principais chaves:

* customer_id
* order_id
* product_id

---

# Perguntas de Negócio

As perguntas abaixo serão respondidas na Semana 12 utilizando consultas SQL.

## 1. Quais estados possuem a maior quantidade de clientes?

Objetivo:

Identificar onde a Olist possui maior presença de clientes.

---

## 2. Quais cidades possuem mais clientes cadastrados?

Objetivo:

Entender a distribuição geográfica da base de clientes.

---

## 3. Quais categorias possuem mais produtos cadastrados?

Objetivo:

Identificar as categorias com maior variedade de produtos.

---

## 4. Quais produtos apresentam maior quantidade de vendas?

Objetivo:

Descobrir os produtos mais populares da plataforma.

---

## 5. Qual é o valor médio dos pagamentos realizados?

Objetivo:

Entender o comportamento geral dos pagamentos.

---

## 6. Quais estados possuem o maior ticket médio de compra?

Objetivo:

Identificar regiões que geram maior receita por cliente.

---

## 7. Quais categorias geram maior faturamento?

Objetivo:

Identificar os segmentos mais importantes para o negócio.

---

## 8. Quais meses apresentaram maior volume de vendas?

Objetivo:

Identificar possíveis sazonalidades no e-commerce.

---

## 9. Quais clientes realizaram mais pedidos?

Objetivo:

Identificar clientes com maior recorrência de compra.

---

## 10. Quais categorias possuem maior preço médio dos produtos?

Objetivo:

Entender quais segmentos possuem produtos de maior valor agregado.

---

# Planejamento da Semana 12

Na próxima etapa serão desenvolvidas consultas SQL para responder cada uma das perguntas de negócio apresentadas neste documento.

Além das consultas, serão gerados insights e interpretações dos resultados encontrados para apoiar a tomada de decisão.
