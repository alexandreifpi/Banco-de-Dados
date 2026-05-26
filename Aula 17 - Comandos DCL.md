# Comandos DCL

---

## DCL

- DCL (Data Control Language): linguagem usada para controlar o acesso aos dados em um banco de dados
- Faz parte da SQL (Structured Query Language)
- Permite conceder e remover permissões de usuários

---

## Função principal:

- Controlar quem pode acessar ou manipular os dados
- Garantir a segurança das informações

---

## Características:

- Complementa:
-- DDL (Data Definition Language)
-- DML (Data Manipulation Language)
- Considerada uma das partes mais simples da SQL

---

## Criação e gerenciamento de usuários

**Listar usuários no MySQL**

- Comando para listar os usuários de um banco de dados no MySQL.

```sql
SELECT user, host FROM mysql.user;
```

---

## Criação e gerenciamento de usuários

**Criar um novo usuário.**

- Cria um usuário com login e senha para acesso ao banco.

```sql
CREATE USER 'userName'@'localhost' IDENTIFIED BY 'senha';
```

---

## Criação e gerenciamento de usuários

**Criar usuário acessando de qualquer host**

- Permite que o usuário acesse de qualquer máquina.

```sql
CREATE USER 'userName'@'%' IDENTIFIED BY 'senha';
```

---

## Alterar senha do usuário

- Atualiza a senha de um usuário existente.

```sql
ALTER USER 'userName'@'localhost' IDENTIFIED BY 'nova_senha';
```

---

## Remover um usuário

- Exclui um usuário do banco de dados.

```sql
DROP USER 'userName'@'localhost';
```

---

## Verificar permissões do usuário

- Mostra quais privilégios um usuário possui.

```sql
SHOW GRANTS FOR 'userName'@'localhost';
```

---

## Uso pelos administradores:

- Definir permissões de acesso
- Ajustar privilégios conforme necessidade
- Controlar segurança do banco

---

## Principais comandos:

- GRANT: concede permissões
- REVOKE: remove permissões

---

## Objetivo geral:

- Permitir ou negar acesso para:
-- Consultar dados
-- Inserir, atualizar ou excluir informações

---

## GRANT

- GRANT é um comando usado para conceder acesso ou privilégios sobre objetos do banco de dados aos usuários.

**SYNTAX**

```sql
GRANT PRIVILEGES ON OBJECT TO USER;
```

---

## Privilégios

- SELECT, INSERT, DELETE,INDEX, CREATE, ALTER, DROP, ALL, UPDATE, GRANT.

---

## Permitir SELECT em uma tabela

- Concede permissão de leitura (SELECT) em uma tabela para um usuário.

```sql
GRANT SELECT ON tableName TO 'userName'@'localhost';
```

---

## Conceder múltiplas permissões

- Permite várias ações ao mesmo tempo (SELECT, INSERT, DELETE, UPDATE).

```sql
GRANT SELECT, INSERT, DELETE, UPDATE ON tableName TO 'userName'@'localhost';
```

---

## Conceder permissão para todos os usuários

- Aplica uma permissão específica para todos os usuários.

```sql
GRANT SELECT ON tableName TO '*'@'localhost';
```

---

## Revoke

- Usado para remover permissões concedidas anteriormente.
- Pode remover qualquer combinação de: SELECT, INSERT, UPDATE, DELETE, REFERENCES, ALTER ou ALL.

```sql
REVOKE privileges ON object FROM user;
```

---

## Remover permissão DELETE

- Remove a permissão de exclusão de um usuário em uma tabela.

```sql
REVOKE DELETE ON tableName FROM userName;
```

---

## Remover todas as permissões

- Remove completamente o acesso do usuário à tabela.

```sql
REVOKE ALL ON tableName FROM userName;
```

---

## ROLES (Papéis de acesso)

- São grupos de permissões
- Facilitam o gerenciamento de acesso
- Evitam repetir comandos GRANT para vários usuários

## Ciar uma role

- Cria um papel com nome específico.

```sql
CREATE ROLE 'roleName';
```

---

## Conceder permissões à role

- Define o que a role pode fazer.

```sql
GRANT SELECT, INSERT ON tableName TO 'roleName';
```

---

## Associar role a um usuário

- Atribui a role a um usuário.

```sql
GRANT 'roleName' TO 'userName'@'localhost';
```

---

## Ativar uma role (quando necessário)

- Alguns SGBDs exigem ativação da role na sessão.

```sql
SET ROLE 'roleName';
```

---

## Remover role de um usuário

- Retira a role do usuário

```sql
REVOKE 'roleName' FROM 'userName'@'localhost';
```

---



