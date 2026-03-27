# Semana 8 — Subconsultas (Subqueries)

Nesta semana, vamos aprender a utilizar **subconsultas**, que são consultas dentro de outras consultas.

As subqueries permitem criar análises mais avançadas, como:
- Comparar valores com médias
- Filtrar dados com base em outras consultas
- Criar tabelas temporárias para análise

---

## Subquery no WHERE (IN, EXISTS)

### 💡 Ideia principal

Utilizar o resultado de uma consulta para filtrar outra.

---

### IN

O `IN` verifica se um valor está dentro do resultado de uma subconsulta.

### Estrutura:

```sql
SELECT *
FROM tabela
WHERE coluna IN (
    SELECT coluna
    FROM outra_tabela
);
```

👉 Filtra registros com base em outra consulta

---

### EXISTS

O `EXISTS` verifica se a subconsulta retorna algum resultado.

### Estrutura:

```sql
SELECT *
FROM tabela t1
WHERE EXISTS (
    SELECT 1
    FROM outra_tabela t2
    WHERE t1.coluna = t2.coluna
);
```

👉 Retorna verdadeiro se houver correspondência

---

## Subquery no SELECT

Permite adicionar informações calculadas diretamente na consulta principal.

### Estrutura:

```sql
SELECT coluna,
       (SELECT função(coluna)
        FROM outra_tabela) AS resultado
FROM tabela;
```

👉 Adiciona um valor calculado como nova coluna

---

## Subquery no FROM (Tabela derivada)

Permite usar o resultado de uma consulta como se fosse uma tabela.

### Estrutura:

```sql
SELECT *
FROM (
    SELECT coluna, função(coluna)
    FROM tabela
) AS subconsulta;
```

👉 Cria uma "tabela temporária" para análise

---

## ⚠️ Cuidados importantes

- Subqueries podem impactar performance
- Sempre use alias em subqueries no FROM
- Prefira JOIN quando possível (em alguns casos é mais eficiente)
- EXISTS pode ser mais performático que IN dependendo do caso

---

## Prática


Esses conceitos são fundamentais para resolver problemas mais complexos em SQL e construir análises completas.
