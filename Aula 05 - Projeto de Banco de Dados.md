# Projeto de um Banco de Dados

## Passo 1: Anállise de Requisitos

- Compreender quais dados serão armazenados no banco de dados.
- Compreender quais aplicações serão construídas usando esses dados.
- Compreender quais operações são mais frequentes.
- O que os usuários querem do banco de dados?

## Passo 2: Projeto do banco de dados conceitual

- As informações obtidas no passo de análise são usadas para desenvolver uma descrição de alto nível dos dados.
- Usa-se o modelo ER.
- Facilitar a discussão entre todas as pessoas envolvidas.

## Passo 3: Projeto lógico do banco de dados

- Escolher um SGBD para implementar o banco de dados.
- Converter o projeto conceitual em um projeto lógico.
- Conversão ER para o Relacional.

## Passo 4: Refinamento do esquema

- Analisar o conjunto de relações para identificar problemas e refina-las.
- Normalização das relações.

# Modelagem de Dados

- Criação de modelos conceituais, lógicos e físicos descrevendo como os dados estão relacionados entre si e como são armazenados e acessados dentro de um sistema.
- Garante integridade e consistência dos dados.

<img width="480" height="392" alt="image" src="https://github.com/user-attachments/assets/228598fc-e27f-4e9b-8898-03af0ab55b2a" />

## Modelagem Conceitual

- Representação abstrata e independente de implementação dos dados.
- Geralmente representada por meio do Diagrama Entidade Relacionamento (DER).

## Modelagem Lógica

- Fornece mais detalhes da modelagem conceitual.
- Define-se chaves e restrições.
- Geralmente representada por Modelos de Dados Relacionais.

## Modelagem Física

- Modelo é implementado em um SGBD específico.
- Define-se os tipos de dados, detalhes, organização física, índices, etc.

# Modelo Entidade-Relacionamento (ER)

## Mini-mundo

- **Definição:** é a representação de um pedaço da realidade que será modelado no banco de dados.
- **Foco:**: só inclui informações relevantes para os objetivos do sistema (não é o mundo todo, só a parte útil).
- **Exemplo:** em um sistema de biblioteca, o mini-mundo é composto por livros, autores, usuários, empréstimos e devoluções.
- **Exclusão:** informações fora do escopo não entram (ex.: cor da estante ou marca da lâmpada da biblioteca não são relevantes).
- **Modelagem:** o mini-mundo é transformado em um modelo conceitual (como o diagrama ER).
- **Restrição:** contém também as regras de negócio que limitam e organizam como os dados se relacionam.
- **Finalidade:** garantir que o banco represente fielmente o pedaço da realidade que ele precisa armazenar e gerenciar.

## Abstração

- Simplificação da realidade de acordo com a necessidade.
- Esconde detalhes não necessários.
- **Cenário 1:** Estacionamento
  - Placa, Modelo, Cor
- **Cenário 2:** Oficina Mecânica
  - Placa, Quilometragem, Histórico de Revisão.

## Modelo ER

- Descreve os dados de aplicações do mundo real em termos de **entidades** (objetos), **atributos** (características) e seus **relacionamentos**;
- É largamente utilizado para o desenvolvimento da fase inicial do projeto de BD;
- Fornece conceitos para partir de uma descrição informal dos usuários para obter uma descrição mais detalhada;

### Entidades

<img width="222" height="146" alt="Captura de tela de 2026-04-10 14-27-31" src="https://github.com/user-attachments/assets/3b484079-40dd-4710-bdff-fe61f5e594dd" />

- É um objeto do mundo real distinguível de outros objetos:
  - **Ex.:** no contexto empresarial (funcionário, diretor, cliente);
- Pode ser um objeto com existência **física** ou **abstrata**;
  - **Ex.:** no contexto bancário (funcionário, conta);
- Descrito por propriedades/atributos.
- No modelo entidade relacionamento, as entidades são representadas por um **retângulo**.

### Entidade Forte:**

<img width="222" height="146" alt="image" src="https://github.com/user-attachments/assets/bfa22754-3882-4237-91b3-d65a18c2bf1f" />

- Existe independentemente da existência de outra entidade.
- No modelo entidade relacionamento, as entidades fortes são representadas por um **retângulo**.

### Entidade Fraca:**

<img width="222" height="146" alt="Captura de tela de 2026-04-10 14-31-19" src="https://github.com/user-attachments/assets/bdfdd462-afc1-4c03-b6a9-b8230e79ad47" />

- Depende da existência de outra entidade.
- No modelo entidade relacionamento, as entidades fracas são representadas por um **retângulo dentro de outro**.

### Atributos

<img width="222" height="84" alt="image" src="https://github.com/user-attachments/assets/620fefaa-86e2-472c-950e-df24c568ce34" />

- Usados para descrever um conjunto de entidades ou de relacionamentos
- **Ex:** o conjunto de entidades Empregado pode ter os seguintes atributos:
  - Nome
  - Matrícula
  - Sexo
  - Idade
  - Endereço
- **Obs.:** todas as entidades em um dado conjunto de entidades têm os mesmos atributos.
- Os atributos são representados no modelo ER através de uma **elipse (círculo achatado)**.

### Atributos Simples x Compostos

- **Atributo simples ou atômico**

<img width="222" height="84" alt="image" src="https://github.com/user-attachments/assets/620fefaa-86e2-472c-950e-df24c568ce34" />

- Não pode ser decomposto (dividido) em atributos mais básicos.
  - Ex.: sexo {M, F}

- **Atributo composto**

<img width="402" height="203" alt="Captura de tela de 2026-04-10 14-38-21" src="https://github.com/user-attachments/assets/964a8e72-2629-47dc-a45d-d3d884d0163b" />

- Pode ser decomposto em atributos mais simples
  - **Ex.:** endereço (nome_rua, nro_casa,complemento, nome_bairro, cep)

### Atributos Monovalorados x Multivalorados

- **Monovalorado**

<img width="222" height="84" alt="image" src="https://github.com/user-attachments/assets/620fefaa-86e2-472c-950e-df24c568ce34" />

- Possui um único valor para cada entidade
  - **Exemplo:** idade

- **Multivalorado**

<img width="198" height="73" alt="Captura de tela de 2026-04-10 14-40-36" src="https://github.com/user-attachments/assets/9aa94ac5-372d-4e3f-bcb5-ae289f4bb6e1" />

- Múltiplos valores para cada entidade
  - **exemplo:** atributo telefone.

### Atributos Armazenado x Derivado 

- **Armazenado**

<img width="222" height="84" alt="image" src="https://github.com/user-attachments/assets/620fefaa-86e2-472c-950e-df24c568ce34" />

- Está realmente armazenado no BD;
  - Ex.: Nome da pessoa;

- **Derivado**

<img width="198" height="73" alt="image" src="https://github.com/user-attachments/assets/4c59760e-73be-4d74-ad9e-877eaa3bb418" />
  
- Pode ser determinado através de outros atributos ou através de entidades relacionadas;
  - Ex.: idade = data_atual - data_nascimento
  - Ex.: nro_empregados = soma de entidades

### Atributos Chave

- Atributo-Chave ou restrição de exclusividade:
- Um tipo de entidade tem um mais ou mais valores que são distintos para cada entidade individual no conjunto de entidades.
  - Ex.: O atributo chave para uma pessoa seria o CPF.
- Logo, duas entidade de um mesmo conjunto de entidades não podem ter a mesma chave.
- Alguns tipos de entidades possuem mais de um atributo-chave.

### Relacionamento

<img width="276" height="152" alt="Captura de tela de 2026-04-10 14-44-55" src="https://github.com/user-attachments/assets/c1a1f345-be64-42b3-b799-5449f4b65903" />

- É uma associação entre duas ou mais entidades.
  - **Ex:** João trabalha no departamento farmacêutico.
- Reuni-se um conjunto de relacionamentos similares em um conjunto de relacionamentos (Tipo-Relacionamento):
  - Ex: Empregado trabalha em Departamento;
- Pode ter um conjunto de atributos descritivos
- Armazenam informações sobre o relacionamento
  - Ex: João trabalha no departamento farmacêutico desde janeiro de 2000.

<img width="823" height="213" alt="Captura de tela de 2026-04-10 14-45-49" src="https://github.com/user-attachments/assets/d56f23db-d050-445f-89ed-da15ca672e8e" />

- Deve ser unicamente identificado pelas entidades participantes
  - Ex: cada relacionamento trabalha_em deve ser identificado pela matrícula do funcionário e código do departamento.

<img width="823" height="213" alt="Captura de tela de 2026-04-10 14-45-49" src="https://github.com/user-attachments/assets/d56f23db-d050-445f-89ed-da15ca672e8e" />

- Pode envolver 2 ou mais entidades.
  - **Ex:** associação entre empregado, departamento e localização(ternário).

<img width="592" height="231" alt="Captura de tela de 2026-04-10 14-47-03" src="https://github.com/user-attachments/assets/34296fb3-4cea-4414-b248-2724063746e1" />

- Pode envolver duas entidades do mesmo conjunto de entidades (Auto-relacionamento)
  - Especificar o papel de cada uma;

<img width="285" height="292" alt="Captura de tela de 2026-04-10 14-47-49" src="https://github.com/user-attachments/assets/4a3f0485-3689-4868-8f71-8e76649c3e6c" />

### Cardinalidade

- Ajuda a definir o relacionamento, pois ela define o seu número de ocorrências.
- Para determinarmos a cardinalidade, devemos fazer algumas perguntas relativas ao relacionamento em ambas as direções:
  - Pergunta: Um departamento possui quantos empregados?
  - Resposta: No mínimo 1 e no máximo N.
  - Pergunta: Um empregado está alocado em quantos departamentos?
  - Resposta: No mínimo em 1 e no máximo em 1.

- Especifica o número máximo de instâncias de relacionamentos em que uma entidade pode participar:
- Ex: relacionamento Trabalha_para
  - Departamento:Funcionário
  - Cardinalidade 1:N
- Tipos de cardinalidade
  - 1:1, 1:N, N:1 e M:N

### Relacionamento um-para-um

- É usado quando uma entidade A se relacionar com apenas uma entidade B e vice-versa.
- Esse relacionamento é representado pelo sinal: 1:1.

<img width="595" height="129" alt="Captura de tela de 2026-04-10 14-48-26" src="https://github.com/user-attachments/assets/972becb5-61fc-4c53-b667-3c7b07cadaea" />

### Relacionamento um-para-muitos

- É usado quando uma entidade A pode se relacionar com uma ou mais entidades B.
- No entanto, uma entidade B se relaciona apenas com uma única entidade A.

<img width="595" height="129" alt="Captura de tela de 2026-04-10 14-49-10" src="https://github.com/user-attachments/assets/15faa226-e9f6-4c37-ba72-7ee524b3b106" />

### Relacionamento muitos-para-muitos

- Quando várias entidades A se relacionam com várias entidades B, e vice-versa.

<img width="595" height="170" alt="Captura de tela de 2026-04-10 14-49-43" src="https://github.com/user-attachments/assets/fff1d488-4c54-4f57-9917-b33c343108f5" />

## Atividades

1. Um berçário deseja informatizar suas operações. Quando um bebê nasce, algumas informações são armazenadas sobre ele, tais como: nome, data do nascimento, peso do nascimento, altura, a mãe deste bebê e o médico que fez seu parto. Para as mães, o berçário também deseja manter um controle, guardando informações como: nome, endereço, telefone e data de nascimento. Para os médicos, é importante saber: CRM, nome, telefone celular e especialidade.

2. Uma floricultura deseja informatizar suas operações. Inicialmente, deseja manter um cadastro de todos os seus clientes, mantendo informações como: CPF, nome, telefone e endereço. Deseja também manter um cadastro contendo informações sobre os produtos que vende, tais como: nome do produto, tipo (flor, vaso, planta,...), preço e quantidade em estoque. Quando um cliente faz uma compra, a mesma é armazenada, mantendo informação sobre o cliente que fez a compra, a data da compra, o valor total e os produtos comprados.

3. Uma biblioteca deseja manter informações sobre seus livros. Inicialmente, quer armazenar para os livros as seguintes características: ISBN, título, ano editora e autores deste livro. Para os autores, deseja manter: nome e nacionalidade. Cabe salientar que um autor pode ter vários livros, assim como um livro pode ser escrito por mais de um autor. Cada livro da biblioteca pertence a uma categoria. A biblioteca deseja manter um cadastro de todas as categorias existentes, com informações como: código da categoria e descrição. Uma categoria pode ter vários livros associados a ela.
