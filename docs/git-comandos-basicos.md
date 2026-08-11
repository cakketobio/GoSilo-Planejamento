# Comandos Básicos do Git
Aqui estão os comandos essenciais, organizados do básico ao avançado, para o time usar no dia a dia.

---

## 1. Configuração Inicial (faz uma vez só)

```bash
# Configurar nome e email (aparece nos commits)
git config --global user.name "Seu Nome"
git config --global user.email "seu@email.com"

# Verificar se está tudo certo
git config --list
```

---

## 2. Primeiro Acesso ao Projeto

```bash
# Clonar o repositório do GitHub para o computador
git clone https://github.com/cakketobio/gosilo-planejamento.git

# Entrar na pasta do projeto
cd gosilo-planejamento
```

---

## 3. Rotina Diária (o que fazer todo dia)

Sempre **antes** de começar a trabalhar:

```bash
# Puxar as atualizações mais recentes
git pull origin main
```

Durante o trabalho:

```bash
# Ver o que foi alterado (arquivos modificados, novos, etc.)
git status

# Adicionar um arquivo específico
git add nome-do-arquivo.md

# Adicionar TODOS os arquivos modificados
git add .

# Criar um commit (foto do estado atual)
git commit -m "feat: adiciona questionário de pesquisa"

# Enviar para o GitHub
git push origin main
```

---

## 4. Trabalhando com Branches (EVITAR CONFLITOS)

```bash
# Criar uma nova branch e já entrar nela
git checkout -b feature/tela-login

# Ver em qual branch você está
git branch

# Trocar de branch
git checkout main

# Depois de commitar na branch de feature, enviar para o GitHub
git push origin feature/tela-login

# Voltar para a main, puxar atualizações e juntar a feature
git checkout main
git pull origin main
git merge feature/tela-login

# Apagar a branch depois do merge (opcional)
git branch -d feature/tela-login
```

---

## 5. Resolvendo Problemas Comuns

| Problema | Comando |
|----------|---------|
| **Desfazer alteração em um arquivo (antes de add)** | `git restore nome-do-arquivo.md` |
| **Tirar um arquivo do stage (depois de add, antes de commit)** | `git reset nome-do-arquivo.md` |
| **Desfazer o último commit (mantendo alterações)** | `git reset --soft HEAD~1` |
| **Ver histórico de commits** | `git log --oneline` |
| **Ver diferenças exatas (o que mudou)** | `git diff` |
| **Resolver conflito de merge** | Abrir o arquivo, escolher o código certo, remover os marcadores `<<<<<<<`, depois `git add` e `git commit` |

---

## 6. Fluxo de Trabalho Diário (resumo visual)

```
git pull origin main          ← Puxa o que o time fez
   ↓
(edita, cria, modifica)
   ↓
git status                    ← Vê o que mudou
   ↓
git add .                     ← Prepara tudo
   ↓
git commit -m "mensagem"      ← Salva localmente
   ↓
git push origin main          ← Sobe para o GitHub
```

---

## 7. Padrão de Mensagens de Commit (sugestão)

Usem prefixos para organizar o histórico:

| Prefixo | Quando usar |
|---------|-------------|
| `feat:` | Nova funcionalidade ou arquivo |
| `fix:` | Correção de erro |
| `docs:` | Documentação |
| `style:` | Ajustes visuais (formatação, espaços) |
| `refactor:` | Refatoração de código |
| `test:` | Testes |

**Exemplos:**
```
feat: adiciona tela de cadastro
fix: corrige link do Trello no README
docs: atualiza ata da reunião de kickoff
```

---

## 8. Observações

> **Antes de começar qualquer tarefa, sempre façam `git pull origin main`.**  
> Isso evita 90% dos conflitos e retrabalho.
