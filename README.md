# GoSilo-Planejamento

![Status](https://img.shields.io/badge/status-em%20andamento-yellow)
![Fase](https://img.shields.io/badge/fase-planejamento-blue)
![Período](https://img.shields.io/badge/período-2º%20semestre-green)

Repositório de Documentação, pesquisa de usuários, protótipos e planejamento do GoSilo.

---
## O Problema:
> Sementes secas (grãos) colhidas de plantas cultivadas, como soja, milho, arroz e trigo, têm a característica de perder a qualidade e sofrer ataques de fungos ou insetos se forem guardados com umidade elevada ou sem controle de temperatura logo após a colheita. Muitos produtores enfrentam supersafras ou gargalos logísticos e ficam sem espaço para guardar toda a produção a granel, correndo o risco de sofrer perdas financeiras severas por deterioração; ao mesmo tempo, outros produtores ou cooperativas investiram em estruturas robustas de silos que ficam parcialmente ociosas em determinadas épocas do ano, gerando uma oportunidade para o aluguel de espaço e comercialização programada

O **GoSilo** conecta essas duas realidades: quem tem espaço anuncia, quem precisa armazena. Tudo por meio de um sistema de leilão de espaços em silos, visualizados em um mapa interativo.

---
## Equipe

| Nome | Papel (Scrum) | GitHub |
|------|---------------|--------|
| Anna Luisa | Scrum Master & Tech Lead | [@annaluisa](https://github.com/cakketobio) |
| Ana Vitória | Product Owner | [@anavitoria](https://github.com/yik3x) |
| Breno | Tech Lead & Pesquisador | [@breno](https://github.com/bd2s17) |
| Brian | UI Designer | [@brian](https://github.com/ferrarinetto13-glitch) |

---
## Papéis

| Pessoa | O Que Faz |
|--------|-----------|
| **Anna Luisa** | Organiza o time, cuida do GitHub, documenta tudo, conduz reuniões. |
| **Ana Vitória** | Voz do usuário. Vive o problema, conduz entrevistas, define prioridades, valida protótipos. |
| **Brian** | Desenha as telas, cria protótipos no Figma, define cores e ícones. |
| **Breno** | Pesquisa tecnologias, analisa concorrentes, desenha diagramas do sistema. |

---

## Estrutura do Repositório

- **docs/** – Documentação geral
  - `stack-proposta.md` – Proposta da stack tecnológica
  - `git-comandos-basicos.md` – Guia de comandos do Git
  - **retrospectivas/** – Atas de retrospectiva do grupo
- **pesquisa/** – Pesquisa com usuários
  - `problema-relato-pessoal.md` – Relatos pessoais coletados
  - `solucoes-existentes.md` – Análise de mercado
  - `questionario-base.md` – Perguntas estruturadas
  - `participantes-pesquisa.md` – Lista de entrevistados
  - `entrevistas-transcricoes.md` – Transcrições completas
  - `resultados-pesquisa-usuarios.md` – Relatório final da pesquisa
- **ux/** – UX/UI Design
  - **wireframes-iniciais/** – Primeiros esboços das telas
  - `fluxo-navegacao.png` – Mapa de navegação do app
  - `glossario-visual.md` – Definições de termos de design
  - `guia-estilo.md` – Paleta de cores, tipografia, etc.
- **modelagem/** – Diagramas do sistema
  - `casos-de-uso-v1.png` – Diagrama de Casos de Uso (Versão 1)
  - `casos-de-uso-v2.png` – Diagrama de Casos de Uso (Versão 2)
  - `diagrama-classes.png` – Diagrama de Classes UML
  - `diagrama-fluxo-sistema.png` – Fluxo de dados e arquitetura
- - **prototipação/** – Protótipos
  - `protótipos` - Protótipos Desenvolvidos
 
    
---

## Metodologia

Utilizamos uma adaptação do **Scrum** com sprints de 1 a 2 semanas.

### Sprints

| Sprint | Duração | Objetivo | Status |
|--------|---------|----------|--------|
| Sprint 0 | 1 semana | Setup, repositórios, kickoff e definição de stack | Concluído |
| Sprint 1 | 1,5 semanas | Pesquisa com produtores rurais e wireframes iniciais | Concluído |
| Sprint 2 | 2 semanas | Protótipos de média fidelidade, fluxos e modelagem | Concluído |
| Sprint 3 | 1 semana | Ajustes finais, validação com usuários e documentação | Pendente |

### Reuniões

| Tipo | Frequência | Duração | Objetivo |
|------|------------|---------|----------|
| Daily | Seg, Qua, Sex | 15 min | Alinhamento rápido: "Fiz/Vou fazer/Bloqueios" |
| Planning | Início da sprint | 30-40 min | Definir tarefas da sprint |
| Review | Final da sprint | 20 min | Mostrar entregas para o time |
| Retrospectiva | Final da sprint | 20 min | Melhorar o processo |

---

## Tecnologias (provisórias)

A stack tecnológica do GoSilo foi definida na Sprint 0, considerando as necessidades do aplicativo, especialmente geolocalização, comunicação em tempo real, gerenciamento de dados e funcionamento do sistema de leilão. Ver documento [`docs/stack-proposta.md`](docs/stack-proposta.md).

### Front-end

* **React Native + Expo** — desenvolvimento do aplicativo mobile multiplataforma.

### Back-end

* **Python + FastAPI** — desenvolvimento da API e das regras de negócio do sistema.
* **WebSockets** — comunicação em tempo real, utilizada principalmente para o sistema de leilão e atualizações entre usuários.

### Banco de dados e geolocalização

* **PostgreSQL** — gerenciamento e persistência dos dados da aplicação.
* **PostGIS** — extensão do PostgreSQL utilizada para operações de geolocalização e consultas espaciais.

### Segurança

* **Argon2id ou BCrypt** — armazenamento seguro de senhas por meio de funções de hash.
* **AES-256** — criptografia de dados sensíveis armazenados no sistema.

### Design e prototipação

* **Lovable** — criação dos protótipos e interfaces do aplicativo.
* **Figma** — criação dos protótipos e interfaces do aplicativo.

A implementação dessas tecnologias será realizada na **Fase 02 — Desenvolvimento**, enquanto este repositório concentra o planejamento, a pesquisa, a prototipação e a modelagem do sistema.


---

## Público-Alvo

Produtores rurais brasileiros que trabalham com silagem, divididos em dois perfis:

1. **Anunciantes:** Produtores com silos de capacidade ociosa (médios e grandes proprietários)
2. **Locatários:** Produtores que precisam de espaço para armazenar silagem com urgência

Região inicial: Estado de Goiás.

---

## Status Atual

- [x] Ideia do projeto definida
- [x] Problema documentado
- [x] Repositório configurado
- [ ] Pesquisa com usuários realizada
- [x] Protótipos criados
- [ ] Modelagem concluída

---

## Links

- **Repositório de código (Fase 02):** [em breve]
- **Board Kanban:** [Board Kanban do GoSilo](https://trello.com/invite/b/gdIdj7zz/ATTI027b16c041f19ee0085082933894d026F77FA151/projeto-integrador)
- **Protótipo no Lovable:** [em breve]

---

> **"Menos burocracia, mais receita."**
