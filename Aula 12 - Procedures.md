# Procedure e Functions

- É um bloco de código SQL salvo no próprio banco de dados, que executa tarefas quando chamado.

- Semalhante a criação de um método em uma linguagem de programação, reutilizável.

---

## Função reutilizável, que:

- Pode receber parâmetros;

- Pode executar comandos complexos;

- Evita repetição de código;

- Melhora a segurança e a manutenção.

---

## Exemplos de utilização:

- Rotinas de limpeza no banco de dados;

- Correção de dados;

- Atualização de registros automaticamente;

- Etc.

---

## Sintaxe Básica

> Criar Procedure

```mysql
DELIMITER //
CREATE PROCEDURE nome_da_procedure(parametros)
BEGIN
  // bloco de código
END;//
DELIMITER ;
```

---

> Excluir Procedure

```mysql
DROP PROCEDURE nome_da_procedure;
```

---

> Chamar Procedure

```mysql
CALL nome_da_procedure();
```

---

## Parâmetros da Procedure

- São opicionais, quando não precisar de parâmetros, os parênteses permanecem vazios na declaração da procedure.

- A passagem de parâmetros deve respeitar a seguinte sintaxe:

  - (MODO nome_do_parametro TIPO)

---

### MODO

- Indica a forma que os parâmetros serão tratados, se é um dados de entrada, de saída ou ambos.

  - IN: Parâmetro apenas de entrada.
  - OUT: Parâmetro apenas de saída.
  - INOUT: Parâmetro de entrada e de saída.

---

### TIPO

- Indica qual é o tipo de determinado parâmetro (INT, VARCHAR, DECIMAL, ...).

---

### Procedure com parâmetro de entrada

```mysql
DELIMITER //
CREATE PROCEDURE listar_pacientes(IN limite INT)
BEGIN
  SELECT * FROM pacientes LIMIT limite;
END //
DELIMITER ;

CALL lista_pacientes(5);
```

---

### Procedure com parâmetro de saída

```mysql
DELIMITER //
CREATE PROCEDURE calcular_quantidade_pacientes(OUT quantidade INT)
BEGIN
  SELECT COUNT(*) INTO quantidade FROM pacientes;
END //
DELIMITER ;

CALL calcular_quantidade_pacientes(@quantidade);
SELECT @quantidade;
```

---

### Procedure com condicionais

```mysql
DELIMITER //
CREATE PROCEDURE procedure_condicional()
BEGIN
  IF condicao THEN
    SELECT 'Condição satisfeita';
  ELSE
    SELECT 'Condição insatisfeita';
END IF
END //
DELIMITER ;
```

---

## Atividades

1. Uma loja deseja padronizar o cadastro de clientes. Crie uma procedure chamada cadastrar_cliente que receba: nome e cidade e insira um novo cliente na tabela de clientes.
2. O sistema precisa registrar novos pedidos. Crie uma procedure chamada criar_pedido que receba: id do cliente e data do pedido e insira um novo registro na tabela de pedidos.
3. Após criar um pedido, é necessário adicionar produtos. Crie uma procedure chamada adicionar_item_pedido que receba: id do pedido, id do produto e quantidade e insira um item na tabela itens_pedido.
4. A loja deseja calcular automaticamente o valor total de um item. Crie uma procedure que: receba id do pedido, id do produto e quantidade busque o preço do produto calcule o valor total (preço × quantidade) e retorne esse valor.
5. O sistema deve evitar pedidos inválidos. Crie uma procedure que: receba um id_cliente verifique se o cliente existe se existir, crie o pedido caso contrário, retorne uma mensagem de erro.
6. A loja deseja consultar dados completos de pedidos. Crie uma procedure que receba um id_pedido e retorne: nome do cliente, data do pedido, produtos do pedido e quantidade.
7. Crie uma procedure que receba um id_cliente e retorne: o total gasto por esse cliente (somando todos os pedidos e itens).
