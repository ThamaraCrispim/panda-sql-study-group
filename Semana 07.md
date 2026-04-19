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

##2 - Unir resultados de diferentes consultas de clientes

##3 - Identificar registros presentes em uma tabela e ausentes em outra

##4 - Encontrar produtos que nunca apareceram em pedidos
