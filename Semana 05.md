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

👉 Filtra grupos com base em condições agregadas


---

## Prática

## 1.Contar quantos pedidos existem no banco

## 2.Calcular quantidade de clientes por estado

## 3.Calcular média de valor de pagamento

## 4.Identificar categorias com maior número de produtos

## 5.Filtrar agrupamentos com base em condições específicas
