# GoSilo-Planejamento

![Status](https://img.shields.io/badge/status-concluído-success)
![Fase](https://img.shields.io/badge/fase-planejamento-blue)
![Período](https://img.shields.io/badge/período-2º%20semestre-green)

Repositório de **documentação, pesquisa com usuários, modelagem e planejamento** do projeto GoSilo.

Este repositório concentra os artefatos produzidos durante a etapa de planejamento do projeto e serve como base para a prototipação e, posteriormente, para o desenvolvimento da aplicação.

---

## Sobre o GoSilo

O **GoSilo** é uma aplicação mobile que conecta produtores rurais que precisam de espaço para armazenar sua produção a proprietários de silos que possuem capacidade de armazenamento disponível.

A proposta funciona como um **marketplace de espaços para armazenamento agrícola**, permitindo que:

* Proprietários anunciem espaços disponíveis em seus silos;
* Produtores encontrem espaços adequados para armazenar sua produção;
* Usuários encontrem silos por localização e características;
* Produtores realizem propostas e lances;
* Proprietários acompanhem propostas recebidas;
* As partes acompanhem reservas e negociações.

O sistema busca reduzir perdas de produção e melhorar o aproveitamento da capacidade de armazenamento existente.

---

## O Problema

> Sementes secas (grãos) colhidas de plantas cultivadas, como soja, milho, arroz e trigo, têm a característica de perder a qualidade e sofrer ataques de fungos ou insetos se forem guardados com umidade elevada ou sem controle de temperatura logo após a colheita. Muitos produtores enfrentam supersafras ou gargalos logísticos e ficam sem espaço para guardar toda a produção a granel, correndo o risco de sofrer perdas financeiras severas por deterioração; ao mesmo tempo, outros produtores ou cooperativas investiram em estruturas robustas de silos que ficam parcialmente ociosas em determinadas épocas do ano, gerando uma oportunidade para o aluguel de espaço e comercialização programada.

O **GoSilo** conecta essas duas realidades:

**quem tem espaço anuncia, quem precisa armazena.**

A solução utiliza localização, anúncios, comunicação entre usuários e um sistema de propostas/leilão para facilitar a contratação de espaços de armazenamento.

---

## Objetivo

O objetivo do projeto é desenvolver uma solução digital que facilite o acesso a espaços de armazenamento agrícola, conectando oferta e demanda de forma mais rápida, organizada e transparente.

### Objetivos específicos

* Facilitar a busca por espaços disponíveis;
* Permitir que proprietários monetizem capacidade ociosa;
* Reduzir o tempo necessário para encontrar armazenamento;
* Centralizar informações sobre os silos;
* Permitir negociação entre produtores e proprietários;
* Utilizar geolocalização para facilitar a busca;
* Proporcionar comunicação em tempo real;
* Criar uma experiência simples e adequada ao contexto do agronegócio.

---

## Equipe

| Nome        | Papel (Scrum)            | GitHub                                             |
| ----------- | ------------------------ | -------------------------------------------------- |
| Anna Luisa  | Scrum Master & Tech Lead | [@annaluisa](https://github.com/cakketobio)        |
| Ana Vitória | Product Owner            | [@anavitoria](https://github.com/yik3x)            |
| Breno       | Tech Lead & Pesquisador  | [@breno](https://github.com/bd2s17)                |
| Brian       | UI Designer              | [@brian](https://github.com/ferrarinetto13-glitch) |

---

## Papéis

| Pessoa          | O Que Faz                                                                                             |
| --------------- | ----------------------------------------------------------------------------------------------------- |
| **Anna Luisa**  | Organiza o time, gerencia o GitHub, documenta o projeto e conduz reuniões.                            |
| **Ana Vitória** | Representa a perspectiva do usuário, conduz entrevistas, define prioridades e participa da validação. |
| **Brian**       | Desenvolve as interfaces, cria os protótipos e define elementos visuais.                              |
| **Breno**       | Pesquisa tecnologias, analisa soluções existentes e contribui para a modelagem do sistema.            |

---

## Estrutura do Repositório

```text
GoSilo-Planejamento/
│
├── docs/
│   ├── stack-proposta.md
│   ├── git-comandos-basicos.md
│   └── retrospectivas/
│
├── pesquisa/
│   ├── problema-relato-pessoal.md
│   ├── solucoes-existentes.md
│   ├── questionario-base.md
│   ├── participantes-pesquisa.md
│   ├── entrevistas-transcricoes.md
│   └── resultados-pesquisa-usuarios.md
│
├── modelagem/
│   ├── casos-de-uso-v1.png
│   ├── casos-de-uso-v2.png
│   ├── diagrama-classes.png
│   └── diagrama-fluxo-sistema.png
│
└── README.md
```

---

## Pesquisa com Usuários

A pasta [`pesquisa`](pesquisa) concentra os estudos realizados para compreender o problema e validar a necessidade da solução.

Entre os materiais estão:

* Relatos relacionados ao problema;
* Análise de soluções existentes;
* Questionário utilizado nas pesquisas;
* Participantes;
* Transcrições das entrevistas;
* Resultados consolidados da pesquisa.

A pesquisa foi utilizada como base para definição das funcionalidades e dos principais fluxos do GoSilo.

---

### Repositório de Protótipos

A evolução completa dos protótipos do GoSilo está documentada no repositório:

**[GoSIlo-Prototipos](https://github.com/cakketobio/GoSIlo-Prototipos)**

O repositório de protótipos contém:

* Fluxos de navegação;
* Protótipos de baixa fidelidade;
* Protótipos de média fidelidade;
* Protótipos de alta fidelidade;
* Guia de estilo;
* Glossário visual;
* Validação final do protótipo.

Dessa forma, este repositório concentra a **concepção e planejamento da solução**, enquanto o repositório de protótipos concentra a **materialização visual e interação da solução**.

---

## Modelagem

A pasta [`modelagem`](modelagem) reúne os principais diagramas utilizados para representar o funcionamento e a estrutura do sistema.

Entre eles:

* Diagrama de Casos de Uso;
* Diagrama de Classes;
* Diagrama de Fluxo do Sistema.

A modelagem auxilia na transformação dos requisitos levantados durante a pesquisa em uma estrutura que possa posteriormente ser implementada.

---

## Metodologia

Utilizamos uma adaptação do **Scrum**, organizada em sprints de aproximadamente 1 a 2 semanas.

A metodologia foi utilizada para organizar as atividades de pesquisa, documentação, UX/UI e modelagem.

### Sprints

| Sprint   | Duração     | Objetivo                                             | Status    |
| -------- | ----------- | ---------------------------------------------------- | --------- |
| Sprint 0 | 1 semana    | Setup, repositórios, kickoff e definição da stack    | Concluído |
| Sprint 1 | 1 semana | Pesquisa com produtores rurais e análise do problema | Concluído |
| Sprint 2 | 1 semana   | Protótipos, fluxos de navegação e modelagem          | Concluído |
| Sprint 3 | 1 semana    | Ajustes finais, validação e documentação             | Concluído |

---

## Reuniões

| Tipo          | Frequência       | Duração   | Objetivo                                   |
| ------------- | ---------------- | --------- | ------------------------------------------ |
| Daily         | Seg, Qua, Sex    | 15 min    | Alinhamento: "Fiz / Vou fazer / Bloqueios" |
| Planning      | Início da sprint | 30–40 min | Definição das tarefas                      |
| Review        | Final da sprint  | 20 min    | Apresentação das entregas                  |
| Retrospectiva | Final da sprint  | 20 min    | Avaliação e melhoria do processo           |

---

## Tecnologias

A stack tecnológica foi definida considerando as necessidades do GoSilo, principalmente geolocalização, comunicação em tempo real, persistência de dados e funcionamento do sistema de propostas/leilão.

A especificação completa está disponível em [`docs/stack-proposta.md`](docs/stack-proposta.md).

### Front-end

* **React Native + Expo** — desenvolvimento do aplicativo mobile multiplataforma.

### Back-end

* **Python + FastAPI** — desenvolvimento da API e das regras de negócio.
* **WebSockets** — comunicação em tempo real, principalmente para o sistema de leilão e atualizações entre usuários.

### Banco de Dados e Geolocalização

* **PostgreSQL** — gerenciamento e persistência dos dados.
* **PostGIS** — extensão utilizada para operações de geolocalização e consultas espaciais.

### Segurança

* **Argon2id ou BCrypt** — armazenamento seguro de senhas por meio de funções de hash.
* **AES-256** — criptografia de dados sensíveis armazenados no sistema.

### Design e Prototipação

* **Figma** — criação e prototipação das interfaces e fluxos de usuário.
* **Lovable** — ferramenta auxiliar para exploração e construção inicial de interfaces.

A implementação da stack será realizada na etapa de **Desenvolvimento**, enquanto este repositório registra as decisões tomadas durante o planejamento.

---

## Público-Alvo

O público-alvo inicial do GoSilo são **produtores rurais brasileiros**, especialmente aqueles envolvidos com produção e armazenamento de grãos.

A solução considera dois perfis principais:

### 1. Anunciantes

Proprietários de silos, produtores rurais, cooperativas ou empresas que possuem **capacidade de armazenamento ociosa** e desejam disponibilizá-la.

### 2. Locatários

Produtores rurais que precisam encontrar **espaço para armazenar sua produção**, especialmente durante períodos de alta demanda.

### Região Inicial

**Estado de Goiás.**

A expansão para outras regiões poderá ser considerada posteriormente.

---

## Fluxo Geral da Solução

```text
                    GoSilo
                       │
           ┌───────────┴───────────┐
           │                       │
     Dono do Silo            Produtor Rural
           │                       │
     Cria anúncio              Busca silos
           │                       │
     Define condições          Visualiza mapa
           │                       │
     Recebe propostas          Consulta anúncio
           │                       │
     Analisa lances             Faz proposta
           │                       │
           └───────────┬───────────┘
                       │
                 Negociação
                       │
                    Reserva
```

---

## Evolução do Projeto

O desenvolvimento do GoSilo foi dividido em etapas complementares:

```text
Pesquisa
   ↓
Planejamento
   ↓
Requisitos
   ↓
Modelagem
   ↓
UX/UI
   ↓
Protótipos
   ↓
Validação
   ↓
Desenvolvimento
```

### Repositórios

| Etapa           | Repositório             | Objetivo                                       |
| --------------- | ----------------------- | ---------------------------------------------- |
| Planejamento    | **GoSilo-Planejamento** | Pesquisa, documentação, requisitos e modelagem |
| Prototipação    | **GoSIlo-Prototipos**   | UX/UI, fluxos e protótipos                     |
| Desenvolvimento | **GoSilo-Codigo**       | Controle de versão da aplicação                     |

---

## Status Atual

### Planejamento

* [x] Ideia do projeto definida
* [x] Problema documentado
* [x] Público-alvo definido
* [x] Repositório configurado
* [x] Stack tecnológica definida
* [x] Pesquisa com usuários realizada
* [x] Análise de soluções existentes realizada
* [x] Requisitos levantados
* [x] Modelagem realizada
* [x] Fluxos principais definidos

### Prototipação

* [x] Wireframes iniciais
* [x] Fluxos de navegação
* [x] Protótipo de baixa fidelidade
* [x] Protótipo de média fidelidade
* [ ] Protótipo de alta fidelidade
* [x] Guia de estilo
* [x] Glossário visual
* [ ] Validação final

### Desenvolvimento

* [ ] Configuração do projeto
* [ ] Implementação do front-end
* [ ] Implementação do back-end
* [ ] Banco de dados
* [ ] Sistema de geolocalização
* [ ] Sistema de propostas/leilão
* [ ] Chat
* [ ] Testes
* [ ] Deploy

---

## Links

* **Repositório de Planejamento:** [GoSilo-Planejamento](https://github.com/cakketobio/GoSilo-Planejamento)
* **Repositório de Protótipos:** [GoSilo-Prototipos](https://github.com/cakketobio/GoSilo-Prototipos)
* **Repositório de Código:** Em desenvolvimento
* **Board Kanban:** [Board Kanban do GoSilo](https://trello.com/b/gdIdj7zz/projeto-integrador)

---

> **"Menos burocracia, mais receita."**
