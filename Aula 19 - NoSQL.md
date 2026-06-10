!!!capa
instituicao: Instituto Federal do Piauí
curso: Tecnologia em Sistemas para Internet
disciplina: Banco de Dados
professor: Alexandre Lages
tema: Bancos de Dados NoSQL

---

# Bancos de Dados NoSQL

---

## Instalação do MongoDB no Linux

```bash
$ sudo apt update
$ sudo apt install -y mongodb-org
$ sudo systemctl start mongod
$ sudo systemctl status mongod
$ sudo systemctl enable mongod
```

---

## Executando o MongoDB

```bash
$ mongosh
```

---

## Criando ou Acessando Banco de Dados

```bash
$ use escola
```

---

## Bancos de Dados NoSQL

- São bancos de dados não relacionais.
- Podem armazenar dados em um formato não estruturado.
- Desta forma, são mais flexíveis (cada registro pode ter uma estrutura diferente) e escaláveis.
- São projetados para suportar uma grande quantidade de dados.
- Ideal para aplicações modernas e com grande volume de dados.

---

## Principais Características

- **Dinâmico:** Permite criar estruturas de dados flexíveis que não exigem alterações no schema.
