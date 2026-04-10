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
- **Entidade Forte:**
  - Existe independentemente da existência de outra entidade.
- **Entidade Fraca:**
  - Depende da existência de outra entidade.
