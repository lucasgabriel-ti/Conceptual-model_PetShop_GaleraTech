# Modelagem de Banco de Dados com brModelo

Repositório destinado ao armazenamento de projetos e estudos de modelagem de dados (Conceitual e Lógico) desenvolvidos durante o curso **Galera Tech** como aprendizado em banco de dados SQL.

## Objetivo

O propósito deste repositório é aplicar os conceitos de diagramação e estruturação de bancos de dados relacionais utilizando a ferramenta brModelo.

## Tecnologias e Ferramentas

* **brModelo:** Ferramenta CASE para ensino e modelagem de bancos de dados relacionais.

## Projeto: Pet Shop Galera Tech

Modelo Entidade-Relacionamento (MER) de um sistema de gestão para uma rede de pet shops (multiloja). O modelo cobre o cadastro de tutores e pets, o quadro de funcionários por loja e o registro dos atendimentos com os serviços prestados.

### Entidades e atributos

| Entidade | Atributos | Chave primária |
|---|---|---|
| **Tutor(a)** | nome_tutor, email_tutor, cpf_tutor | `id_tutor` |
| **Pet** | nome_pet, sexo_pet, especie_pet, id_tutor | `id_pet` |
| **Loja** | cnpj, numero_loja | `id_loja` |
| **Funcionário(a)** | nome_funcionário, cargo, id_loja | `id_funcionário` |
| **Serviço** | nome_serviço, tipo_serviço, preço | `id_serviço` |
| **Atendimento** | data, status, id_loja, id_pet, id_funcionario | `id_atend` |
| **Item de atendimento** | id_atend, id_serviço | `id_item_atend` |

### Relacionamentos e cardinalidades

| Relacionamento | Entidades envolvidas | Cardinalidade |
|---|---|---|
| **tem** | Tutor(a) ↔ Pet | (1,n) : (1,n) |
| **possui** | Loja ↔ Funcionário(a) | (1,n) : (1,1) |
| **faz** | Funcionário(a) ↔ Atendimento | (1,n) : (1,n) |
| **tem** | Atendimento ↔ Item de atendimento | (1,n) : (1,n) |
| **tem** | Serviço ↔ Item de atendimento | (1,n) : (1,n) |
| **realiza** | Tutor(a) / Pet ↔ Item de atendimento | (1,n) : (1,n) : (1,1) |
| **realiza** | Item de atendimento ↔ Funcionário(a) | (1,n) : (1,n) |

### Regras de negócio representadas

* Um tutor pode ter vários pets, e um pet pode estar vinculado a mais de um tutor.
* Cada funcionário pertence a uma única loja, e uma loja possui vários funcionários.
* Um atendimento pode conter vários serviços, registrados como itens de atendimento.
* Cada atendimento registra o pet atendido, a loja, o funcionário responsável, a data e o status.

### Legenda do diagrama

* **Retângulos:** entidades (em vermelho, as entidades de cadastro; em azul, as entidades de movimentação).
* **Losangos:** relacionamentos.
* **Círculos preenchidos:** atributos-chave.
* **Círculos vazios:** atributos comuns.
* **(min, max):** cardinalidade de cada lado do relacionamento.

## Estrutura do repositório


├── conceitual/     # Modelo Entidade-Relacionamento (MER)
├── logico/         # Modelo lógico (tabelas, PKs e FKs)
└── README.md

## Roadmap

- [x] Modelo conceitual (MER) do Pet Shop Galera Tech
- [ ] Modelo lógico (tabelas, chaves primárias e estrangeiras)
- [ ] Resolução dos relacionamentos N:N com tabelas associativas
- [ ] Modelo físico em SQL (DDL)
- [ ] Carga de dados de teste e consultas de exemplo

## Como visualizar os modelos

1. Acesse o brModelo (versão web) ou abra o arquivo `.brM3` na versão desktop.
2. Importe o arquivo do modelo desejado, disponível nas pastas `conceitual/` e `logico/`.
3. Navegue pelo diagrama usando os controles de zoom e exportação da ferramenta.

## Contexto

Projeto desenvolvido para fins educacionais durante o curso **Galera Tech**.
