# Triggers

- Comando automático que é executado pelo banco de dados quando certos eventos ocorrem em uma tabela, como:
  - INSERT (inserção);
  - UPDATE (atualização);
  - DELETE (remoção).
- São regras que reagem automaticamente a eventos que ocorrem em um banco de dados.

## Pra que serve uma trigger?

- Auditoria (registrar ações feitas no banco);
- Validação extra de dados;
- Atualizar outras tabelas automaticamente;
- Prevenir ações indevidas;
- Manter integridade de dados;
- Manter dados derivados.

## Exemplos do dia a dia

- Regras para a gestão de estoque de produtos;
- Regras para a aprovação de crédito para clientes;
- Regras para o cálculo das médias de alunos.

## Evento-Condição-Ação

### Evento

- São primitivas que reagem a mudanças de estado em BDs, **inserções**, **alterações** e **deleções**.

### Condição

- Pode ser tanto um predicado sobre o banco de dados quanto uma consulta.
- Um predicado (condição) deve retornar VERDADEIRO ou FALSO;
- No caso de uma condição expressa por meio de uma consulta, a consulta é interpretada como VERDADEIRO se ela contém ao menos uma tupla na resposta, e como FALSO, no caso contrário.

### Ação 

– É um procedimento qualquer de manipulação de dados. 
- Ela pode, inclusive:
  - ter comandos transacionais (como ROLLBACK)
  - ter comandos de manipulação de regras
  - ativar procedimentos externos ao BD

## Sintaxe Básica de uma Trigger

```mysql
CREATE TRIGGER nome_da_trigger
AFTER INSERT ON nome_da_tabela
FOR EACH ROW
BEGIN
 -- código que será executado
END;
```

## Tipos de Eventos de uma Trigger

- BEFORE INSERT: Antes de inserir;
- AFTER INSERT: Depois de inserir;
- BEFORE UPDATE: Antes de atualizar;
- AFTER UPDATE: Depois de atualizar;
- BEFORE DELETE: Antes de deletar;
- AFTER DELETE: Depois de deletar.

## Opções de Execução

1. A ação pode ser executada antes (BEFORE) ou depois (AFTER) do evento que disparou a regra.
2. A ação pode referenciar tanto os valores antigos quanto os novos valores das tuplas que serão incluídas, removidas ou alteradas pelo evento que disparou a ação.
3. Os eventos que podem ser monitorados são: INSERT, UPDATE e DELETE.
4. Nos eventos de alteração monitorados, podemos especificar um atributo particular ou um conjunto de atributos para monitorar.
5. Uma condição (opcional) pode ser especificada por meio da cláusula WHEN, e a ação só é executada se a regra é disparada e a condição é satisfeita quando o evento de disparo ocorre.

## Comandos com TRIGGER’s

- Excluir trigger:

```mysql
DROP TRIGGER IF EXISTS log_update_salario;
```

- Mostrar todas as triggers:

```mysql
SHOW TRIGGERS;
```

## Exemplo Prático

- Imagine que tenhamos um banco de dados de gerenciamento de empresa, e nesse banco nós temos uma tabela chamada funcionário. Foi pedido que a guardássemos as mudanças ocorridas nos salários dos funcionários, para isso criamos a seguinte tabela.

```mysql
CREATE TABLE log_salarios (
 id INT AUTO_INCREMENT PRIMARY KEY,
 funcionario_id INT,
 salario_antigo DECIMAL(10, 2),
 salario_novo DECIMAL(10, 2),
 alterado_em TIMESTAMP DEFAULT
CURRENT_TIMESTAMP
);
```

- No entanto, o simples fato de criar essa tabela não fará com que as informações que queremos sejam armazenadas, para que as informações de mudança de salário seja armazenada automaticamente após modificar o valor do salário, precisamos criar uma trigger.

```mysql
CREATE TRIGGER log_update_salario
BEFORE UPDATE ON funcionarios
FOR EACH ROW
BEGIN
 IF OLD.salario <> NEW.salario THEN
 INSERT INTO log_salarios (funcionario_id, salario_antigo,
salario_novo)
 VALUES (OLD.id, OLD.salario, NEW.salario) ;
 END IF;
END
```
