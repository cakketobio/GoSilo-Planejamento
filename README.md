# GoSilo-Planejamento

![Status](https://img.shields.io/badge/status-em%20andamento-yellow)
![Fase](https://img.shields.io/badge/fase-planejamento-blue)
![Período](https://img.shields.io/badge/período-2º%20semestre-green)

Repositório de Documentação, pesquisa de usuários, protótipos e planejamento do GoSilo.

---
## O Problema:
> A silagem é um alimento perecível produzido a partir da fermentação de plantas como milho, sorgo e capim, e estraga rapidamente se não for armazenada em condições adequadas logo após a colheita. Muitos produtores rurais enfrentam safras acima do esperado e ficam sem espaço em seus silos, correndo o risco de perder toda a produção. Ao mesmo tempo, outros produtores possuem silos com capacidade ociosa que poderiam ser alugados.

O **GoSilo** conecta essas duas realidades: quem tem espaço anuncia, quem precisa armazena. Tudo por meio de um sistema de leilão de espaços em silos, visualizados em um mapa interativo.

---
## Equipe

| Nome | Papel (Scrum) | GitHub |
|------|---------------|--------|
| Anna Luisa | Scrum Master & Tech Lead | [@annaluisa](https://github.com/cakketobio) |
| Ana Vitória | Product Owner | [@anavitoria](https://github.com/anavitoria) |
| Breno | Tech Lead & Pesquisador | [@breno](https://github.com/bd2s17) |
| Brian | UI Designer | [@brian](https://github.com/brian) |

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
 
    
---

## Metodologia

Utilizamos uma adaptação do **Scrum** com sprints de 1 a 2 semanas.

### Sprints

| Sprint | Duração | Objetivo | Status |
|--------|---------|----------|--------|
| Sprint 0 | 1 semana | Setup, repositórios, kickoff e definição de stack | Pendente |
| Sprint 1 | 1,5 semanas | Pesquisa com produtores rurais e wireframes iniciais | Pendente |
| Sprint 2 | 2 semanas | Protótipos de média fidelidade, fluxos e modelagem | Pendente |
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

A definir na Sprint 0. Ver documento [`docs/stack-proposta.md`](docs/stack-proposta.md).

Sugestão inicial: React Native + Firebase (avaliar viabilidade).

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
- [ ] Repositório configurado
- [ ] Pesquisa com usuários realizada
- [ ] Protótipos criados
- [ ] Modelagem concluída

---

## Links

- **Repositório de código (Fase 02):** [em breve]
- **Board Kanban:** [Board Kanban do GoSilo](https://trello.com/invite/b/gdIdj7zz/ATTI027b16c041f19ee0085082933894d026F77FA151/projeto-integrador)
- **Protótipo no Figma:** [em breve]

---

> **"Conectar silos vazios a silagens que não podem esperar."**
