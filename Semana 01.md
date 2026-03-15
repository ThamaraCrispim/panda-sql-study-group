##  Semana 1 — Introdução e Ambiente

**SQL (Structured Query Language)** é uma linguagem utilizada para **consultar, manipular e gerenciar dados armazenados em bancos de dados relacionais**.

Os **bancos de dados relacionais** organizam as informações em **tabelas**, compostas por **linhas (registros)** e **colunas (atributos)**. Essas tabelas podem se relacionar entre si por meio de **chaves**, permitindo conectar diferentes informações, como clientes, pedidos e produtos.

Para realizar consultas SQL é necessário utilizar um **Sistema Gerenciador de Banco de Dados (SGBD)** e uma ferramenta que permita executar os comandos.

Neste grupo de estudos foi escolhido o **MySQL** como banco de dados para realizar as práticas. 

Após configurar o ambiente, o próximo passo é **conectar ao banco de dados** e começar a executar consultas.

O primeiro comando geralmente aprendido em SQL é o **`SELECT`**, que é utilizado para **consultar dados armazenados nas tabelas**.

Exemplo de consulta básica:

```sql
SELECT * FROM olist_products_dataset
```
Resultando:

![Descrição da tabela employees](https://github.com/ThamaraCrispim/panda-sql-study-group/blob/main/Imagem/semana%20.png)

## Classificação das Variáveis

Podemos observar que a tabela `olist_products_dataset` possui diferentes tipos de variáveis. Essas variáveis podem ser classificadas em qualitativas e quantitativas, de acordo com o tipo de informação que representam.

### Variáveis qualitativas (categóricas)

As variáveis qualitativas representam categorias ou identificadores e não possuem significado numérico direto.

- **product_id**  
  Variável qualitativa nominal utilizada como identificador único do produto. Essa variável pode ser utilizada como chave primária ou para relacionar tabelas através de operações de `JOIN`.

- **product_category_name**  
  Variável qualitativa nominal que representa a categoria à qual o produto pertence, como por exemplo *perfumaria*, *bebes* e *esporte_lazer*.

---

### Variáveis quantitativas discretas

As variáveis quantitativas discretas representam contagens, ou seja, valores inteiros que indicam quantidade de algo.

- **product_name_lenght**  
  Quantidade de caracteres presentes no nome do produto.

- **product_description_lenght**  
  Quantidade de caracteres presentes na descrição do produto.

- **product_photos_qty**  
  Quantidade de fotos associadas ao produto.

---

### Variáveis quantitativas contínuas

As variáveis quantitativas contínuas representam medidas físicas dos produtos.

- **product_weight_g** — peso do produto em gramas  
- **product_length_cm** — comprimento do produto em centímetros  
- **product_height_cm** — altura do produto em centímetros  
- **product_width_cm** — largura do produto em centímetros
