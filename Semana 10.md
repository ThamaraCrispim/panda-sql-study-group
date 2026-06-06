# Semana 10 — Criação e Alteração de Estruturas (DDL)

Nesta semana, vamos estudar **DDL (Data Definition Language)**.

Diferente do DML, que manipula os dados dentro das tabelas, o DDL é usado para criar, alterar e excluir estruturas do banco de dados.

Os principais comandos estudados são:

* CREATE TABLE
* ALTER TABLE
* DROP TABLE
* PRIMARY KEY
* FOREIGN KEY
* Constraints como NOT NULL, UNIQUE e DEFAULT

---

## CREATE TABLE

O comando `CREATE TABLE` é utilizado para criar uma nova tabela no banco de dados.

Exemplo:

```sql
CREATE TABLE clientes (
    cliente_id INT,
    nome VARCHAR(100),
    cidade VARCHAR(100)
);
```

---

## Constraints

As constraints são regras aplicadas às colunas de uma tabela.

Alguns exemplos:

* `NOT NULL`: impede que a coluna receba valores nulos.
* `UNIQUE`: impede valores repetidos.
* `DEFAULT`: define um valor padrão.
* `PRIMARY KEY`: identifica de forma única cada registro.
* `FOREIGN KEY`: cria uma relação entre tabelas.

---

## ALTER TABLE

O comando `ALTER TABLE` é utilizado para alterar a estrutura de uma tabela já existente.

Exemplo para adicionar uma coluna:

```sql
ALTER TABLE clientes
ADD telefone VARCHAR(20);
```

Exemplo para remover uma coluna:

```sql
ALTER TABLE clientes
DROP COLUMN telefone;
```

---

## DROP TABLE

O comando `DROP TABLE` remove uma tabela do banco de dados.

Exemplo:

```sql
DROP TABLE clientes;
```

⚠️ Esse comando deve ser usado com cuidado, pois apaga a estrutura da tabela e seus dados.

---

# Prática

## 1 - Modelar um sistema inspirado no banco Olist

Nesta prática, foi criado um modelo simples inspirado no banco de dados da Olist.

O sistema possui três tabelas principais:

* clientes
* produtos
* pedidos

A ideia é representar clientes que realizam pedidos contendo produtos.

---

## 2 - Criar tabela de clientes

```sql
CREATE TABLE clientes_ddl (
    cliente_id INT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    cidade VARCHAR(100),
    estado CHAR(2) NOT NULL,
    data_cadastro DATE DEFAULT (CURRENT_DATE)
);
```

Resultado: Foi criada a tabela `clientes_ddl`, contendo informações básicas dos clientes.

---

## 3 - Criar tabela de produtos

```sql
CREATE TABLE produtos_ddl (
    produto_id INT PRIMARY KEY,
    nome_produto VARCHAR(100) NOT NULL,
    categoria VARCHAR(100),
    preco DECIMAL(10,2) NOT NULL
);
```

Resultado: Foi criada a tabela `produtos_ddl`, contendo informações dos produtos.

---

## 4 - Criar tabela de pedidos com chave estrangeira

```sql
CREATE TABLE pedidos_ddl (
    pedido_id INT PRIMARY KEY,
    cliente_id INT NOT NULL,
    produto_id INT NOT NULL,
    quantidade INT DEFAULT 1,
    data_pedido DATE DEFAULT (CURRENT_DATE),

    FOREIGN KEY (cliente_id) REFERENCES clientes_ddl(cliente_id),
    FOREIGN KEY (produto_id) REFERENCES produtos_ddl(produto_id)
);
```

Resultado: Foi criada a tabela `pedidos_ddl`, relacionando clientes e produtos por meio de chaves estrangeiras.

---

## 5 - Inserir alguns dados para testar as relações

```sql
INSERT INTO clientes_ddl (
    cliente_id,
    nome,
    cidade,
    estado
)
VALUES
(1, 'Cliente Teste 1', 'São Carlos', 'SP'),
(2, 'Cliente Teste 2', 'Rio de Janeiro', 'RJ');
```

```sql
INSERT INTO produtos_ddl (
    produto_id,
    nome_produto,
    categoria,
    preco
)
VALUES
(1, 'Produto Teste 1', 'eletronicos', 150.00),
(2, 'Produto Teste 2', 'moveis', 300.00);
```

```sql
INSERT INTO pedidos_ddl (
    pedido_id,
    cliente_id,
    produto_id,
    quantidade
)
VALUES
(1, 1, 1, 2),
(2, 2, 2, 1);
```

Resultado: Foram inseridos registros de teste nas tabelas criadas.

---

## 6 - Consultar os pedidos com clientes e produtos

```sql
SELECT
    p.pedido_id,
    c.nome AS nome_cliente,
    c.cidade,
    c.estado,
    pr.nome_produto,
    pr.categoria,
    p.quantidade,
    pr.preco,
    (p.quantidade * pr.preco) AS valor_total
FROM pedidos_ddl p
INNER JOIN clientes_ddl c
    ON p.cliente_id = c.cliente_id
INNER JOIN produtos_ddl pr
    ON p.produto_id = pr.produto_id;
```

Resultado: A consulta relacionou pedidos, clientes e produtos, mostrando o valor total de cada pedido.

---

## 7 - Alterar uma tabela para adicionar uma nova coluna

```sql
ALTER TABLE clientes_ddl
ADD email VARCHAR(100);
```

Resultado: Foi adicionada a coluna `email` na tabela de clientes.

---

## 8 - Alterar uma tabela para adicionar uma restrição UNIQUE

```sql
ALTER TABLE clientes_ddl
ADD CONSTRAINT unique_email UNIQUE (email);
```

Resultado: Foi adicionada uma restrição para impedir e-mails duplicados.

---

## 9 - Remover uma coluna da tabela

```sql
ALTER TABLE clientes_ddl
DROP COLUMN email;
```

Resultado: A coluna `email` foi removida da tabela de clientes.

---

## 10 - Remover as tabelas criadas

```sql
DROP TABLE pedidos_ddl;
DROP TABLE produtos_ddl;
DROP TABLE clientes_ddl;
```

Resultado: As tabelas criadas para teste foram removidas do banco de dados.

---


