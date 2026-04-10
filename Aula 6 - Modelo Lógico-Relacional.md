# Modelo Lógico Relacional

## Projeto Lógico

- Representa uma transição entre o modelo conceitual e o físico.
- **Conceitual =** Modelo mais abstrato, independe de SGBD.
- **Lógico =** Modelo traduzido para SGBD, mas não se preocupa com detalhes físicos;
- **Físico =** Modelo traduzido para SGBD, se importa com detalhes físicos.

## Modelo Relacional

- Representa os dados num Banco de Dados como uma coleção de relações e seus relacionamentos.
- Cada relação contém um nome e atributos com seus respectivos nomes.
- As relações são também conhecidas por tabelas no desenvolvimento.

### Relações (Entidade/Tabelas):

- Local onde as informações são armazenadas em um banco de dados relacional.
- **Ex.:** Relação Empregado, onde armazena-se as informações dos diversos empregados.

### Atributos (Campos):

- São as informações que fazem parte de uma determinada tabela/relação.
- **Ex.:** A relação Empregado possui os atributos nome, salario, cargo.

### Domínio:

- São os possíveis valores que um determinado atributo pode assumir;
- Desta forma, o domínio define o tipo do dado e o formato que aquele dado pode ser armazenado.
- **Ex.:** A data de nascimento deve ser armazenada no seguinte formato “dd/mm/aaaa”.

### Tuplas (Linhas/Registros):

- Representam os registros de uma relação.
- Ou seja, cada linha representa um registro diferente da minha tabela.
- Uma tabela sem relação sem tuplas é uma relação vazia.

<img width="867" height="403" alt="image" src="https://github.com/user-attachments/assets/f33a1350-6548-4206-b2dc-6ba391d442e3" />

## Chaves Primárias:

- Entidades geralmente possuem um atributo chave que é usado para garantir a identificação única.
- Um atributo que for chave primária não pode ter tuplas com o mesmo valor e também não pode ser vazio.
- Um registro que não possui valor é chamado de registro nulo (null).
- Desta forma, identificam de maneira única cada tupla de uma tabela.
- **Ex.:** CPF tabela de cadastro de clientes, CNPJ tabela de cadastro de fornecedores, Matrícula tabela de cadastro de alunos, etc.

## Chaves Estrangeiras:

- Uma chave estrangeira estabelece uma relação de integridade referencial com uma chave primária de outra tabela.
- Isso garante que os valores de um atributo (chave estrangeira) em uma tupla só serão aceitos se o mesmo valor existir em outro atributo (chave primária) da outra tabela.
- **Ex.:** Livro/Autor.

### A existência de uma chave estrangeira impõe algumas restrições para a modificação do conjunto de dados

- Na inclusão de uma linha da tabela com chave estrangeira.
- Na alteração de um valor de chave estrangeira.
- Na exclusão de uma linha da tabela com chave primária referenciada por chave estrangeira.

- Uma chave estrangeira, não, necessariamente, referencia uma chave primária de outra tabela.
- Uma chave estrangeira pode referenciar a chave primária da própria tabela, como uma forma de implementar um auto relacionamento.

## Modelo Lógico

- O modelo lógico de dados é criado a partir das descrições dos dados representadas em um modelo conceitual.
- Descreve como os dados serão armazenados no banco de dados, identificando as entidades, os atributos, as chaves primárias e estrangeiras e os seus relacionamentos.
- Existem a forma horizontal, forma vertical e a forma textual.
- Define quais tabelas o banco de dados possui, e quais os nomes das colunas dessas tabelas.

### Modelo Lógico - Forma Textual

- Listam-se as relações e, para cada relação, entre parênteses, os atributos que compõem a relação.
- Os campos que compõem a chave primária são sublinhados.

```
<nome da relação> (nome do campo 1, nome do campo 2)
```

### Exemplo

<img width="442" height="443" alt="Captura de tela de 2026-04-10 16-28-28" src="https://github.com/user-attachments/assets/724dbd12-5903-4f63-b0c6-bb3f6c745e6b" />

- Produto (preco, codigo, descricao, codigoTipoProduto)
- TipoProduto (descricao, codigo)

### Modelo Lógico - Forma Vertical

- As relações são representadas por um retângulo.
- As colunas são listadas dentro do retângulo que representa a relação.
- Há a indicação das colunas que compõem a chave primária.
- Há a indicação das colunas que compõem uma chave estrangeira

### Exemplo

<img width="442" height="602" alt="Captura de tela de 2026-04-10 16-32-03" src="https://github.com/user-attachments/assets/af136960-09c8-4718-af6b-975ba355ef11" />

### Modelo Lógico - Forma Horizontal

<img width="1009" height="602" alt="Captura de tela de 2026-04-10 16-32-46" src="https://github.com/user-attachments/assets/03393159-2230-4fe5-bf58-35c96a72b7e8" />

## Tipos Básicos de Dados do brModelo:

| Tipo    | Descrição                                                                 |
|---------|---------------------------------------------------------------------------|
| VARCHAR | VARCHAR são strings de tamanho variável.                                  |
| INTEGER | Valores inteiros.                                                         |
| NUMERIC | Usado por valores para os quais é importante preservar a exatidão, como dados monetários. |
| DATE    | Usado quando se necessita do valor da data.                               |

# Transformação MER para ML

<img width="683" height="364" alt="Captura de tela de 2026-04-10 16-40-54" src="https://github.com/user-attachments/assets/19384bae-4ddc-4757-ad25-a0c2131bf25d" />

## Passo 1: Mapear as Entidades

- Cada entidade será mapeada para uma relação no modelo lógico.
- Mapeando a entidade empregado para relação:







