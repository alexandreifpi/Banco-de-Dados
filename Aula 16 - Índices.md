# Índices
---

## O que são índices?

- São estruturas auxiliares associadas a uma tabela ou coleção de dados.
- Sua função é acelerar o tempo de acesso às linhas de uma tabela.
- Ele faz isso através da criação ponteiros para dados armazenados em colunas específicas.

---

## Analogia

- Um índice de banco de dados se assemelha a um índice de um livro.
- Em vez de percorrer todas as páginas para encontrar um tópico, você consulta o índice, que aponta diretamente para a página desejada.

---

## Como os Índices Funcionam?

- Os índices armazenam os valores de uma ou mais colunas de maneira organizada, geralmente em uma estrutura de dados chamada árvore-B.
- Apesar dos índices acelerarem as consultas, eles consomem espaço de armazenamento.
- Podem impactar inserções, atualizações e exclusões, pois precisam ser reajustados quando ocorrem mudança nos dados.

---

## Exemplo

- Imagine uma tabela com milhões de registros.
- Você deseja encontrar apenas alguns deles.
- Uma consulta sem índice pode demorar bastante, pois ocorrerá uma busca por toda a tabela.
- Com um índice, a busca se torna muito mais rápida, economizando tempo e recursos.

---

# Tipos de Índices

---

## Tipos de Índices

**Índices Simples**

- Fazem referência a uma única coluna.
- Melhoram buscas diretas por um único campo.

---

## Tipos de Índices

**Índices Simples**

```sql
CREATE INDEX idx_nome ON clientes(nome);
```

```sql
SELECT * FROM clientes WHERE nome = 'Alexandre';
```

---

## Tipos de Índices

**Índices Compostos**

- Fazem referência a mais de uma coluna.
- Útil em consultas que filtram dados por múltiplos critérios.
- A ordem das colunas é importante.

---

## Tipos de Índices

**Índices Compostos**

```sql
CREATE INDEX idx_nome_cidade ON clientes(nome, cidade);
```

```sql
SELECT * FROM clientes
WHERE nome = 'Alexandre' AND cidade = 'São Paulo';
```

---

## Tipos de Índices

**Índices Primários**

- Associado à chave primária da tabela, garante que os valores sejam únicos e ordenados.
- Cada tabela pode ter apenas um.

---

## Tipos de Índices

**Índices Primários**

- Associado à chave primária da tabela, garante que os valores sejam únicos e ordenados.
- Cada tabela pode ter apenas um.

---

## Tipos de Índices

**Índices Únicos**

- Similar ao índice primário, mas pode ser aplicado a qualquer coluna, desde que os valores sejam únicos.
- Uma tabela pode ter vários índices únicos.

---

## Tipos de Índices

**Índices Únicos**

```sql
CREATE UNIQUE INDEX idx_email ON clientes(email);
```

```sql
SELECT * FROM clientes WHERE email = 'teste@email.com';
```

---

# Boas Práticas com Índices

---

## Boas Práticas com Índices

**Não indexe todas as tabelas**

- Tabelas pequenas não requerem índices, pois uma varredura de tabela será mais eficiente do que procurar no índice e, em seguida, recuperar os dados da tabela.

---

## Boas Práticas com Índices

**Não indexe todas as colunas**

- A indexação de todas as colunas aumenta a sobrecarga para manter esses índices atualizados e torna mais lentas outras operações do banco de dados.
- Indexe as colunas nas quais você filtra (ou seja, use com frequência nas cláusulas WHERE).

---

## Boas Práticas com Índices

**Não indexe todas as colunas**

- A indexação de todas as colunas aumenta a sobrecarga para manter esses índices atualizados e torna mais lentas outras operações do banco de dados.
- Indexe as colunas nas quais você filtra (ou seja, use com frequência nas cláusulas WHERE).

---

## Boas Práticas com Índices

**Não indexe colunas grandes**

- Um campo grande em sua tabela resultará em um índice grande.

---

## Boas Práticas com Índices

**Indexe chaves estrangeiras**

- Isso melhora o desempenho dos JOINs.

---

## Boas Práticas com Índices

**Use Índices de várias colunas apenas quando for apropriado**

- Os índices compostos podem nos ajudar na melhoria de performance
- Entretanto, é preciso considerar a ordem das colunas dentro do índice.
- Devemos criar um índice sobre o nome e a cidade ou sobre a cidade e o nome? Esses são dois índices diferentes.
- Qual deles terá um desempenho mais eficiente?
- A resposta dependerá das consultas SQL.
- Em geral, um índice de coluna única é suficiente (e economiza tempo).

---

## Boas Práticas com Índices

**Use índices para pré-classificar dados**

- A classificação repetida de dados pode ser evitada quando um índice é adicionado com a ordem de classificação (ou seja, ascendente ou descendente).

---

## Referências

- https://clarify.com.br/blog/indices-sql-acelaram-consultas/
- https://learnsql.com.br/blog/guia-do-analista-de-dados-para-indexacao-sql-corrigir-consultas-lentas/#exemplo-n%c2%ba-2-de-indexa%c3%a7%c3%a3o-de-banco-de-dados

