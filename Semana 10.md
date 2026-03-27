# Semana 10 — Criação e Alteração de Estruturas (DDL)

Nesta semana, vamos aprender a **criar e modificar estruturas do banco de dados**, utilizando comandos de definição (DDL).

Esses comandos são utilizados para:
- Criar tabelas
- Definir regras (constraints)
- Alterar estruturas existentes
- Remover tabelas

---

## CREATE TABLE

O comando `CREATE TABLE` é utilizado para criar novas tabelas.

### Estrutura básica:

```sql
CREATE TABLE tabela (
    coluna1 tipo,
    coluna2 tipo
);
```

---

### Constraints (Restrições)

As constraints garantem integridade dos dados.

Principais:

- `NOT NULL` → não permite valores nulos  
- `UNIQUE` → não permite valores duplicados  
- `DEFAULT` → define valor padrão  

### Exemplo:

```sql
CREATE TABLE clientes (
    id INT PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    email VARCHAR(100) UNIQUE,
    estado VARCHAR(2) DEFAULT 'SP'
);
```

---

## PRIMARY KEY e FOREIGN KEY

### PRIMARY KEY

Identifica unicamente cada registro.

```sql
id INT PRIMARY KEY
```

---

### FOREIGN KEY

Cria relacionamento entre tabelas.

```sql
FOREIGN KEY (coluna)
REFERENCES outra_tabela(coluna)
```

---

## ALTER TABLE

Permite modificar tabelas existentes.

### Adicionar coluna:

```sql
ALTER TABLE tabela
ADD coluna tipo;
```

---

### Remover coluna:

```sql
ALTER TABLE tabela
DROP COLUMN coluna;
```

---

### Modificar coluna:

```sql
ALTER TABLE tabela
ALTER COLUMN coluna TYPE novo_tipo;
```

---

## DROP TABLE

Remove uma tabela do banco de dados.

### Estrutura:

```sql
DROP TABLE tabela;
```

👉 Remove completamente a tabela e seus dados

---

## ⚠️ Cuidados importantes

- DROP TABLE remove tudo permanentemente  
- Sempre valide antes de alterar estruturas  
- PRIMARY KEY não pode ter valores duplicados ou nulos  
- FOREIGN KEY depende da existência da tabela relacionada  
- Alterações estruturais podem impactar outras consultas  

---

## Prática



Esses conceitos são fundamentais para modelagem e construção de bancos de dados.
