# Semana 4 — Funções de String, Data e Matemática

Nesta semana, vamos aprender a utilizar **funções do SQL** para manipular dados, transformar informações e realizar cálculos.

Essas funções são essenciais para:
- Limpar e padronizar dados
- Trabalhar com datas
- Realizar cálculos e ajustes em valores

---

## Funções de String

As funções de string permitem manipular textos.

### Principais funções:

- `UPPER` → transforma o texto em maiúsculo  
- `LOWER` → transforma o texto em minúsculo  
- `CONCAT` → concatena textos  
- `SUBSTR` → extrai parte de um texto  
- `LENGTH` → retorna o tamanho do texto  

### Estrutura:

```sql
SELECT UPPER(coluna)
FROM tabela;
```

```sql
SELECT LOWER(coluna)
FROM tabela;
```

```sql
SELECT CONCAT(coluna1, coluna2)
FROM tabela;
```

```sql
SELECT SUBSTR(coluna, início, tamanho)
FROM tabela;
```

```sql
SELECT LENGTH(coluna)
FROM tabela;
```

---

## Funções de Data

Essas funções permitem trabalhar com datas e extrair informações específicas.

### Principais funções:

- `EXTRACT` → extrai partes da data (ano, mês, dia)
- `DATE_PART` → semelhante ao EXTRACT (dependendo do banco)
- Cálculo de datas → diferença entre datas

### Estrutura:

```sql
SELECT EXTRACT(YEAR FROM data_coluna)
FROM tabela;
```

```sql
SELECT DATE_PART('month', data_coluna)
FROM tabela;
```

```sql
SELECT data_fim - data_inicio
FROM tabela;
```

---

## Funções Matemáticas

Utilizadas para realizar cálculos numéricos.

### Principais funções:

- `ROUND` → arredonda valores  
- `ABS` → valor absoluto  
- `CAST` → conversão de tipo  

### Estrutura:

```sql
SELECT ROUND(coluna, 2)
FROM tabela;
```

```sql
SELECT ABS(coluna)
FROM tabela;
```

```sql
SELECT CAST(coluna AS tipo)
FROM tabela;
```

---

## COALESCE e NULLIF

Essas funções são utilizadas para tratamento de valores nulos.

### COALESCE

Retorna o primeiro valor não nulo.

```sql
SELECT COALESCE(coluna, valor_padrao)
FROM tabela;
```

---

### NULLIF

Retorna NULL se dois valores forem iguais.

```sql
SELECT NULLIF(coluna1, coluna2)
FROM tabela;
```

---

## Prática

Utilizando o dataset **Brazilian E-Commerce Public Dataset by Olist**, realize as seguintes consultas:

## 1 - Padronizar nomes de cidades ou categorias

```sql
select geolocation_city,
upper(geolocation_city) as cidade_padronizada
from olist_geolocation_dataset;
```

Resultado: Após executar o comando, os nomes das cidades foram padronizados, passando a seguir o mesmo padrão de escrita.


![Resultado cidade padronizada estado](https://github.com/ThamaraCrispim/panda-sql-study-group/blob/main/Imagem/Semana%2004.png)

## 2 - Calcular ano ou mês das compras

```sql
SELECT 
  payment_value,
  ABS(payment_value - 100) AS diferenca
FROM olist_order_payments_dataset
ORDER BY diferenca DESC;
```

Resultado: A função ABS foi utilizada para garantir valores positivos. No entanto, como a base não possui valores negativos, não houve alteração nos resultados. Para tornar a análise mais relevante, foi aplicada a função para medir a diferença entre os valores de pagamento e um valor de referência.

![Resultado cidade padronizada estado](https://github.com/ThamaraCrispim/panda-sql-study-group/blob/main/Imagem/semana%2004.P1.png)

## 3 - Calcular diferenças entre datas de pedido e entrega

```sql
SELECT 
  order_purchase_timestamp,
  order_delivered_customer_date,
  DATEDIFF(order_delivered_customer_date, order_purchase_timestamp) AS dias_entrega
FROM olist_orders_dataset
WHERE order_delivered_customer_date IS NOT NULL;
```

Resultado: A consulta calcula a diferença entre a data de compra e a data de entrega utilizando a função DATEDIFF, permitindo analisar o tempo de entrega dos pedidos. Foram considerados apenas pedidos com data de entrega válida.

![Resultado cidade padronizada estado](https://github.com/ThamaraCrispim/panda-sql-study-group/blob/main/Imagem/semana%2004.P2.png)


## 4 - Arredondar valores de pagamento
