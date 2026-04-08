# Semana 5 — Agregação e Agrupamento

Nesta semana, vamos aprender a **resumir e analisar dados**, utilizando funções de agregação e agrupamentos.

Esses conceitos são fundamentais para responder perguntas como:
- Quantos registros existem?
- Qual a média de valores?
- Qual grupo possui mais ocorrências?

---

## Funções de Agregação

As funções de agregação permitem resumir dados em um único valor.

### Principais funções:

- `COUNT` → conta registros  
- `SUM` → soma valores  
- `AVG` → calcula média  
- `MIN` → menor valor  
- `MAX` → maior valor  

### Estrutura:

```sql
SELECT COUNT(*)
FROM tabela;
```

```sql
SELECT SUM(coluna)
FROM tabela;
```

```sql
SELECT AVG(coluna)
FROM tabela;
```

```sql
SELECT MIN(coluna)
FROM tabela;
```

```sql
SELECT MAX(coluna)
FROM tabela;
```

---

## GROUP BY (Agrupamento)

O comando `GROUP BY` é utilizado para agrupar dados com base em uma ou mais colunas.

### Estrutura:

```sql
SELECT coluna, COUNT(*)
FROM tabela
GROUP BY coluna;
```

👉 Agrupa os dados e aplica a função para cada grupo

---

## Diferença entre WHERE e HAVING

- `WHERE` → filtra linhas **antes** do agrupamento  
- `HAVING` → filtra grupos **depois** do agrupamento  

### Estrutura:

```sql
SELECT coluna, COUNT(*)
FROM tabela
WHERE condição
GROUP BY coluna;
```

```sql
SELECT coluna, COUNT(*)
FROM tabela
GROUP BY coluna
HAVING condição;
```

---

## HAVING (Filtro de agrupamento)

O `HAVING` é utilizado para filtrar resultados após o agrupamento.

### Estrutura:

```sql
SELECT coluna, COUNT(*)
FROM tabela
GROUP BY coluna
HAVING COUNT(*) > valor;
```


---

## Prática

## 1.Contar quantos pedidos existem no banco

```sql
SELECT COUNT(*) AS total_pedidos
FROM olist_orders_dataset;
```

Resultado:Essa métrica representa o volume total de pedidos realizados, sendo um indicador importante para análise do negócio.

![Resultado semana 05](https://github.com/ThamaraCrispim/panda-sql-study-group/blob/main/Imagem/semana%2005.png)


## 2.Calcular quantidade de clientes por estado


```sql
SELECT 
  geolocation_state,
  COUNT(*) AS total_registros
FROM olist_geolocation_dataset
GROUP BY geolocation_state
ORDER BY total_registros DESC;
```

Resultado:A consulta agrupa os dados por estado utilizando GROUP BY e conta a quantidade de registros em cada um com a função COUNT, permitindo analisar a distribuição geográfica dos dados.

![Resultado semana 05.P1](https://github.com/ThamaraCrispim/panda-sql-study-group/blob/main/Imagem/Semana%2005.P1.png)

## 3.Calcular média de valor de pagamento


```sql
SELECT 

```

Resultado:

![Resultado semana 05.P1]()

## 4.Identificar categorias com maior número de produtos

## 5.Filtrar agrupamentos com base em condições específicas
