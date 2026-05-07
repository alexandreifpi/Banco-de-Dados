# Transações

---

## Conceitos Importantes

---

### 1. Sistema Monousuário e Multiusuário 

**Monousuário**

- Somente um usuário pode acessar o banco de dados por vez.
- **Exemplo:** SQLite, Microsoft Access.

**Multiusuário**

- Vários usuários podem utilizar o sistema ao mesmo tempo.
- **Exemplo:** MySQL, Postgres, Oracle, etc.

---

### 2. Estado Consistente de Banco de Dados

- É o estado do banco de dados que atende a todas as restrições definidas sobre ele.
- Reflete a realidade que representa.
- **Exemplo:** Pedidos com valores positivos após atualização de dados.

---

### 3. Controle de Concorrência

- Garantia de que múltiplas transações ativadas por vários usuários produzirão resultados corretos quanto manipulam o banco de dados.

---

### 4. Recuperação de Falha

- Garantia de que caso a transação venha a falhar, o banco de dados consiga recuperar seu estado anterior a ela.

---

## Transação

---

### Conceito de Transação

- Conjunto de operações que deve ser executado como uma única unidade.
- Se pelo menos uma das partes dessa transação falhar, todas as alterações realizadas até aquele ponto devem ser revertidas.
- Isso garante que o banco de dados permaneça em um estado consistente.
- Crucial em ambientes onde múltiplas operações podem afetar a integridade dos dados, como em sistemas de comércio eletrônico ou bancos.
- Pode incluir uma ou mais operações de **inserção**, **exclusão**, **modificação** ou **recuperação** de dados.

---

### Exemplo

1. leia(A)
2. A := A - Y
3. escreva(A)
4. leia(B)
5. B := B + Y
6. escreva(B)

---

## Operações Básicas de Transação

---

### READ_ITEM(X) ou R(X)

- Lê um item do banco de dados chamado X para uma variável do programa também chamada X.

---
  
### WRITE_ITEM(X) ou W(X)

- Grava o valor da variável de programa X no item de banco de dados chamado X.

---

### Exemplo

<img width="835" height="347" alt="image" src="https://github.com/user-attachments/assets/0954ce5c-a762-4db7-85e2-adc7c10d4648" />

---

## Propriedades de uma transação

---

### A C I D

---

### Atomicidade

- Assegura que uma transação seja tratada como uma única unidade indivisível.
- Se uma transação contém várias operações, todas elas devem ser concluídas com sucesso para que a transação seja considerada completa.
- Se qualquer operação falhar, todas as alterações realizadas até aquele ponto são desfeitas.
- Essencial para evitar que o banco de dados fique em um estado inconsistente, resultado de operações incompletas ou falhas.

---

### Exemplo Atomicidade

1. leia(A)
2. A := A - Y
3. escreva(A)
4. leia(B)
5. B := B + Y
6. escreva(B)

---

### Exemplo Atomicidade

- Se a transação falhar após o passo 3 e antes do passo 6, o valor será perdido, levando a um estado de inconsistência do banco de dados.
- Essa falha pode ser causada tanto por hardware, quanto por software.

---

### Consistência

- Implica que uma transação deve levar o banco de dados de um estado válido a outro estado válido.
- Significa que todas as restrições de integridade (como chaves primárias e estrangeiras, restrições de unicidade, etc.) devem ser respeitadas antes e depois da transação.
- Uma transação que provoca inconsistência nos dados deve ser rejeitada.
- Portanto, a consistência garante que as regras de negócio e as restrições de integridade sejam sempre respeitadas, mantendo a qualidade e confiabilidade dos dados.

--- 

### Exemplo Atomicidade

1. leia(A)
2. A := A - Y
3. escreva(A)
4. leia(B)
5. B := B + Y
6. escreva(B)

---

### Exemplo Atomicidade

- Uma transação ao iniciar deve ter um banco de dados consistente.
- Quanto concluída deve deixar o banco de dados consistente.
- Durando sua execução, o banco de dados pode ficar temporariamente inconsistente.
- No passo 4, após escrever em A, meu banco de dados passa para um estado inconsistente.
- No entanto, no passo 6, ao escrever em B, meu banco de dados passa para um estado consistente novamente.

---

### Isolamento

- Princípio que garante que as operações de uma transação não afetem ou sejam afetadas por outras transações que estão sendo executadas ao mesmo tempo.
- Isso é vital em ambientes de múltiplos usuários, onde várias transações podem estar ocorrendo simultaneamente.

---

### Exemplo Isolamento

- Uma transação T1 não pode ser dependente de outra transação T2 que possa estar executando simultaneamente.
- Mesmo que as duas transações sejam concorrentes (modifiquem o mesmo item de dados).

---

### Exemplo Isolamento

| Tempo | T1 | T2
| --- | --- | --- |
| 1 | leia(A) |  |
| 2 | A := A - Y |  |
| 3 | escreva(A) |  |
| 4 |  | leia(A) |
| 5 |  | leia(B) |
| 6 |  | imprima(A+B) |
| 7 | leia(B) |  |
| 8 | B := B + Y |  |
| 9 | escreva(B) |  |



---

### Durabilidade

- Assegura que, uma vez que uma transação é confirmada (commit), suas alterações no banco de dados são permanentes, mesmo em caso de falhas de sistema, como quedas de energia ou falhas de hardware.
- Uma vez que uma transação foi feita, as alterações devem ser registradas de forma que possam ser recuperadas, garantindo que não haja perda de dados.
- Sistemas de gerenciamento de banco de dados (SGBDs) utilizam várias técnicas, como registros de log, para garantir a durabilidade das transações.

---

## Referências

- https://paanalytics.net/blog/transacoes-e-controle-de-concorrencia-em-sql/
