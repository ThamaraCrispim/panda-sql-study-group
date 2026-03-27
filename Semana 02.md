# Semana 2 — Consultas Básicas e Filtragem

SQL permite não apenas visualizar dados, mas também **filtrar e refinar informações**, retornando apenas aquilo que é relevante para a análise.

Nesta etapa, começamos a trabalhar com condições, permitindo responder perguntas específicas, como:
- Quais clientes são de um determinado estado?
- Quais pedidos têm valor acima de um limite?
- Quais registros seguem um padrão específico?

---

## SELECT, FROM e AS (Alias)

O comando `SELECT` continua sendo utilizado para escolher as colunas que queremos visualizar, enquanto o `FROM` indica a tabela de onde os dados serão retirados.

O `AS` permite renomear colunas, facilitando a leitura dos resultados.

### Estrutura básica:

```sql
SELECT coluna1, coluna2 AS apelido
FROM tabela;
```

### Explicação:
- `SELECT` → define quais colunas serão exibidas  
- `FROM` → define a tabela  
- `AS` → renomeia colunas (alias)

---

## WHERE (Filtragem de Dados)

O comando `WHERE` é utilizado para filtrar os dados, retornando apenas as linhas que atendem a uma condição.

### Estrutura básica:

```sql
SELECT *
FROM tabela
WHERE condição;
```

---

## Operadores de Comparação

Os operadores permitem comparar valores dentro do `WHERE`.

Principais operadores:

- `=` igual  
- `<>` diferente  
- `>` maior que  
- `<` menor que  
- `>=` maior ou igual  
- `<=` menor ou igual  

### Estrutura:

```sql
WHERE coluna > valor
```

---

## AND, OR e NOT

Esses operadores permitem combinar condições.

### AND

Utilizado quando todas as condições devem ser verdadeiras.

```sql
WHERE condição1 AND condição2
```

---

### OR

Utilizado quando pelo menos uma condição deve ser verdadeira.

```sql
WHERE condição1 OR condição2
```

---

### NOT

Utilizado para negar uma condição.

```sql
WHERE NOT condição
```

---

## LIKE (Busca por padrão)

O operador `LIKE` é utilizado para buscar padrões em textos.

Símbolos:
- `%` representa qualquer sequência de caracteres

### Estrutura:

```sql
WHERE coluna LIKE 'valor%'
```

---

## IN (Lista de valores)

O operador `IN` permite verificar se um valor está dentro de uma lista.

### Estrutura:

```sql
WHERE coluna IN (valor1, valor2, valor3)
```

---

## BETWEEN (Intervalo)

O operador `BETWEEN` filtra valores dentro de um intervalo.

### Estrutura:

```sql
WHERE coluna BETWEEN valor1 AND valor2
```

---

## ⚠️ Cuidados importantes

- Textos devem estar entre aspas `' '`
- `BETWEEN` inclui os valores extremos
- Cuidado ao misturar `AND` e `OR`
- Sempre revise a lógica do filtro

---

## Prática

Utilizando o dataset **Brazilian E-Commerce Public Dataset by Olist**, realize as seguintes consultas:

### Filtrar clientes por estado

```sql
SELECT *
FROM olist_geolocation_dataset
WHERE geolocation_state IN ('SP', 'RJ');

```

- Buscar produtos de uma categoria específica
- Filtrar pedidos entre dois valores ou datas
- Encontrar padrões em nomes de cidades ou categorias
