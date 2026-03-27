# Semana 9 — Manipulação de Dados (DML)

Nesta semana, vamos aprender a **modificar dados dentro do banco**, utilizando comandos de manipulação (DML).

Esses comandos permitem:
- Inserir novos registros
- Atualizar informações existentes
- Remover dados

---

## INSERT (Inserção de dados)

O comando `INSERT` é utilizado para adicionar novos registros em uma tabela.

### Estrutura básica:

```sql
INSERT INTO tabela (coluna1, coluna2)
VALUES (valor1, valor2);
```

---

### Inserindo múltiplos registros:

```sql
INSERT INTO tabela (coluna1, coluna2)
VALUES 
(valor1, valor2),
(valor3, valor4);
```

---

### Inserindo a partir de outra tabela:

```sql
INSERT INTO tabela_destino
SELECT *
FROM tabela_origem;
```

---

## UPDATE (Atualização de dados)

O comando `UPDATE` é utilizado para modificar dados existentes.

### Estrutura:

```sql
UPDATE tabela
SET coluna = valor
WHERE condição;
```

👉 Atualiza apenas os registros que atendem à condição

---

## DELETE (Remoção de dados)

O comando `DELETE` é utilizado para remover registros de uma tabela.

### Estrutura:

```sql
DELETE FROM tabela
WHERE condição;
```

👉 Remove apenas os registros filtrados

---

## ⚠️ Cuidados importantes

- Sempre utilize `WHERE` em UPDATE e DELETE  
- Sem WHERE, todos os registros serão afetados  
- Faça SELECT antes para validar a condição  
- Evite executar comandos diretamente em produção sem teste  
- Utilize subqueries para maior precisão em remoções  

---

## Prática


Esses comandos são essenciais para manutenção e manipulação de bancos de dados no dia a dia.
