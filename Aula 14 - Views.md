# Views

## Contextualização

### Problemática

Uma empresa de e-commerce precisar compartilhar dados de pedidos com uma parceira logística responsável pelas entregas. No entanto, por questões de segurança e privacidade, nem todas as informações do banco de dados devem ser expostas, especialmente dados sensíveis dos clientes, como CPF e telefone.

### Solução

Para resolver isso, a empresa cria uma view que reúne apenas os dados necessários para a operação da parceira, como identificação do pedido, nome do cliente, endereço de entrega e status. Dessa forma, a empresa garante acesso controlado, simplifica a integração e protege informações confidenciais, fornecendo à parceira uma visão específica e segura dos dados.

## O que são?

- São consultas armazenadas em uma estrutura de fácil acesso baseadas num comando SELECT.
- Funciona como uma tabela virtual, similar a uma tabela real.

## Como funcionam?

- Não armazenam os dados.
- Os dados que são exibidos são gerados dinamicamente toda vez que a visão é referenciada.
- Seus dados derivam de uma ou mais tabelas existentes.
- Geralmente são utilizadas para simplificar consultas complexas, fornecer exibição personalizada ou limitar acesso aos dados.

<img width="1431" height="868" alt="image" src="https://github.com/user-attachments/assets/549462e3-b9a0-4b5d-931b-d1a340e42ae6" />

## Views Materializadas

- Semelhante a uma visão lógica, mas com capacidade de persistir uma cópia do resultado.
- É uma estratégia que aprimora o desempenho do banco de dados ao lidar com consultas complexas que envolvem muitas tabelas e cálculos.
- Funciona em bancos de dados como PostgreSQL e Oracle.
- Não funciona no MySQL.

<img width="1514" height="855" alt="image" src="https://github.com/user-attachments/assets/f73e9aaa-11e4-4e53-b5a8-15d97c657697" />

## Prática

### Como criar uma view?

```sql
CREATE VIEW nome_da_visao AS
SELECT  atributo1, atributo2
FROM nome_da_tabela1
WHERE condicao;
```

### Observação

- A visão aparece no esquema do banco de dados como se fosse uma tabela, podemos verificar isso através da instrução SHOW TABLES.

```sql
SHOW TABLES;
```

### Estrutura da View

- Utiliza-se o comando DESC para visualizar a estrutura de uma view.

```sql
DESC nome_da_visao
```

### Consultando dados da view

- Utiliza-se o select para consultar os dados de uma view.
- Você pode realizar filtros no SELECT da view.

```sql
SELECT * FROM nome_da_visao;
```

### Excluindo uma view

```sql
DROP VIEW nome_da_visao
```

## Modificando dados com views

- Em alguns casos é possível realizar a manipulação dos dados de uma view (inserção, atualização e deleção de dados).
- Isso é possível desde que a visão não tenha valores agregados, group by, distincts e nem possua joins.
- Também é necessário que a visão contenha todas as colunas que são obrigatórias na inserção dos dados.
- Na atualização de dados apenas os campos observados na view podem ser atualizados através dela.

## Joins

- Evita repetir JOINs complexos.
- Facilita consultas para usuários iniciantes.
- Funciona como uma “camada de abstração”.
- Padroniza consultas no sistema.
- Não permite inserção, atualização ou deleção.

### Usado quando

- Para criar relatórios.
- Precisa integrar dados de várias tabelas.
- Se quer expor dados para sistemas externos.
- É necessaŕio simplificar consultas frequentes.

### Sintaxe

```sql
CREATE VIEW nome_da_visao AS
SELECT 
    t1.coluna1,
    t2.coluna2
FROM tabela1 t1
JOIN tabela2 t2 ON t1.id = t2.id_tabela1;
```
