# Tutorial-Git-pt_br

Arquivo de auxílio para quem tem dificuldades com comandos GIT. Comandos explicados com exemplos práticos e boas práticas.

**Última atualização:** 2026

---

## 📚 Sumário

- [Configuração Inicial](#configuração-inicial)
- [Criando e Clonando Repositórios](#criando-e-clonando-repositórios)
- [Trabalhando com Arquivos](#trabalhando-com-arquivos)
- [Histórico e Consultas](#histórico-e-consultas)
- [Branches](#branches)
- [Sincronização Remota](#sincronização-remota)
- [Operações Avançadas](#operações-avançadas)
- [Comandos Modernos (Git 2.23+)](#comandos-modernos-git-223)
- [Boas Práticas](#boas-práticas)
- [Referência Rápida](#referência-rápida)

---

## Configuração Inicial

### git config

**Descrição:** Define configurações globais do Git (nome do usuário, email, etc.)

```bash
# Configurar nome do usuário globalmente
git config --global user.name "Seu Nome"

# Configurar email globalmente
git config --global user.email "seu.email@exemplo.com"

# Configurar editor padrão
git config --global core.editor "vim"

# Visualizar todas as configurações
git config --list

# Configurar para um repositório específico (local)
git config user.name "Seu Nome Local"  # sem --global
```

**Dica:** Use `--global` para aplicar a todas os repositórios. Sem a flag, a configuração é apenas para o repositório atual.

---

## Criando e Clonando Repositórios

### git init

**Descrição:** Inicializa um novo repositório Git local

```bash
# Criar um novo repositório no diretório atual
git init

# Criar um novo repositório com nome específico
git init meu-projeto
cd meu-projeto
```

### git clone

**Descrição:** Clona um repositório existente para sua máquina

```bash
# Clonar um repositório
git clone https://github.com/usuario/repositorio.git

# Clonar em um diretório com nome diferente
git clone https://github.com/usuario/repositorio.git meu-diretorio

# Clonar apenas um branch específico
git clone --branch nome-branch https://github.com/usuario/repositorio.git

# Clonar com histórico limitado (mais rápido)
git clone --depth 1 https://github.com/usuario/repositorio.git
```

---

## Trabalhando com Arquivos

### git add

**Descrição:** Adiciona mudanças à área de teste (staging area)

```bash
# Adicionar um arquivo específico
git add arquivo.txt

# Adicionar múltiplos arquivos
git add arquivo1.txt arquivo2.txt

# Adicionar todos os arquivos modificados
git add .
git add --all  # equivalente

# Adicionar partes específicas de um arquivo (interativo)
git add -p  # ou --patch
```

### git commit

**Descrição:** Confirma as mudanças no histórico do repositório

```bash
# Commit com mensagem
git commit -m "Descrição do que foi alterado"

# Commit com mensagem detalhada
git commit -m "Título curto" -m "Descrição mais detalhada das mudanças"

# Commit de todos os arquivos modificados (sem usar git add)
git commit -a -m "Mensagem do commit"

# Alterar a mensagem do último commit
git commit --amend -m "Nova mensagem"

# Adicionar mudanças ao último commit (sem criar novo commit)
git commit --amend --no-edit
```

**Boas Práticas:**
- Use mensagens de commit claras e descritivas
- Comece com verbo no imperativo: "Adiciona feature", "Corrige bug"
- Mantenha commits pequenos e focados

### git diff

**Descrição:** Mostra as diferenças entre versões de arquivos

```bash
# Mostrar mudanças não testadas (não adicionadas)
git diff

# Mostrar mudanças já testadas (adicionadas mas não commitadas)
git diff --staged

# Mostrar mudanças entre dois branches
git diff branch1 branch2

# Mostrar mudanças entre dois commits
git diff commit1 commit2

# Mostrar mudanças em um arquivo específico
git diff arquivo.txt
```

### git rm

**Descrição:** Remove arquivos do repositório e do diretório de trabalho

```bash
# Remover um arquivo
git rm arquivo.txt

# Remover um arquivo do repositório mas manter localmente
git rm --cached arquivo.txt

# Remover todos os arquivos deletados
git rm $(git ls-files --deleted)
```

### git status

**Descrição:** Mostra o estado do repositório

```bash
# Mostrar status completo
git status

# Mostrar status em formato resumido
git status -s
```

---

## Histórico e Consultas

### git log

**Descrição:** Exibe o histórico de commits

```bash
# Mostrar histórico completo
git log

# Mostrar log em uma linha por commit
git log --oneline

# Mostrar últimos N commits
git log -n 5

# Mostrar log com estatísticas
git log --stat

# Mostrar log com mudanças em cada commit
git log -p

# Mostrar histórico de um arquivo específico
git log arquivo.txt

# Mostrar histórico incluindo renomeações
git log --follow arquivo.txt

# Mostrar log com branches em formato gráfico
git log --graph --oneline --all

# Filtrar por autor
git log --author="Nome do Autor"

# Filtrar por data
git log --since="2 weeks ago"
git log --until="2026-09-30"
```

### git show

**Descrição:** Mostra informações detalhadas de um commit específico

```bash
# Mostrar um commit específico
git show commit-hash

# Mostrar um arquivo em uma versão específica
git show commit-hash:arquivo.txt

# Mostrar as mudanças do último commit
git show
```

### git tag

**Descrição:** Cria tags (marcas) para commits específicos (útil para versões)

```bash
# Criar uma tag leve
git tag v1.0.0

# Criar uma tag anotada
git tag -a v1.0.0 -m "Versão 1.0.0"

# Listar todas as tags
git tag

# Mostrar informações de uma tag
git show v1.0.0

# Deletar uma tag local
git tag -d v1.0.0

# Deletar uma tag remota
git push origin --delete v1.0.0

# Enviar tags para o remoto
git push origin v1.0.0
git push origin --tags  # enviar todas
```

---

## Branches

### git branch

**Descrição:** Gerencia branches (ramificações)

```bash
# Listar todos os branches locais
git branch

# Listar todos os branches (local e remoto)
git branch -a

# Criar um novo branch
git branch novo-branch

# Criar um branch a partir de um commit específico
git branch novo-branch commit-hash

# Renomear um branch local
git branch -m nome-antigo nome-novo

# Deletar um branch local
git branch -d nome-branch
git branch -D nome-branch  # força deletar

# Deletar um branch remoto
git push origin --delete nome-branch
git push origin :nome-branch  # forma antiga
```

### git checkout

**Descrição:** Muda entre branches e restaura arquivos

```bash
# Mudar para outro branch
git checkout nome-branch

# Criar e mudar para novo branch em um comando
git checkout -b novo-branch

# Restaurar um arquivo para o estado anterior
git checkout arquivo.txt

# Restaurar um arquivo de um commit específico
git checkout commit-hash -- arquivo.txt
```

### git switch (NOVO - Git 2.23+)

**Descrição:** Alternativa moderna a `git checkout` para mudar entre branches

```bash
# Mudar para outro branch
git switch nome-branch

# Criar e mudar para novo branch
git switch -c novo-branch

# Voltar ao branch anterior
git switch -
```

**Por que usar?** Mais intuitivo e específico para mudança de branches.

### git merge

**Descrição:** Mescla histórico de um branch em outro

```bash
# Mesclar um branch no branch atual
git merge nome-branch

# Mesclar sem criar commit de merge
git merge --ff-only nome-branch

# Mesclar com commit de merge sempre
git merge --no-ff nome-branch

# Cancelar um merge em progresso
git merge --abort
```

---

## Sincronização Remota

### git remote

**Descrição:** Gerencia conexões com repositórios remotos

```bash
# Listar repositórios remotos configurados
git remote
git remote -v  # com URLs

# Adicionar um repositório remoto
git remote add origin https://github.com/usuario/repositorio.git

# Remover um repositório remoto
git remote remove origin

# Renomear um repositório remoto
git remote rename origin upstream

# Mostrar informações detalhadas de um remoto
git remote show origin

# Alterar URL do repositório remoto
git remote set-url origin https://novo-url.git
```

### git push

**Descrição:** Envia commits para o repositório remoto

```bash
# Enviar branch atual para o remoto
git push origin nome-branch

# Enviar todos os branches
git push origin --all

# Enviar com rastreamento automático
git push -u origin nome-branch  # -u = --set-upstream

# Enviar tags
git push origin --tags

# Forçar envio (CUIDADO - sobrescreve histórico remoto)
git push -f origin nome-branch
git push --force-with-lease origin nome-branch  # mais seguro

# Deletar um branch remoto
git push origin --delete nome-branch
```

### git pull

**Descrição:** Busca e mescla mudanças do repositório remoto

```bash
# Buscar e mesclar mudanças
git pull origin nome-branch

# Buscar sem mesclar (fetch)
git fetch origin

# Pull com rebase em vez de merge
git pull --rebase origin nome-branch
```

### git fetch

**Descrição:** Baixa mudanças remotas sem mesclar

```bash
# Buscar do repositório remoto padrão
git fetch

# Buscar de um remoto específico
git fetch origin

# Buscar todos os remotos
git fetch --all
```

---

## Operações Avançadas

### git reset

**Descrição:** Desfaz commits e mudanças

```bash
# Remover arquivo da staging area (não deleta mudanças)
git reset arquivo.txt

# Desfazer commits preservando mudanças
git reset commit-hash

# Desfazer commits e descartar mudanças
git reset --hard commit-hash

# Resetar apenas o index
git reset --mixed commit-hash

# Resetar com soft (mantém tudo na staging area)
git reset --soft commit-hash
```

⚠️ **Cuidado:** `--hard` descarta mudanças permanentemente!

### git rebase

**Descrição:** Reaplica commits de um branch em outro (reorganiza histórico)

```bash
# Fazer rebase interativo dos últimos N commits
git rebase -i HEAD~3

# Fazer rebase de um branch
git rebase nome-branch

# Continuar rebase após resolver conflitos
git rebase --continue

# Cancelar um rebase em progresso
git rebase --abort
```

### git stash

**Descrição:** Armazena temporariamente mudanças sem commitá-las

```bash
# Guardar mudanças
git stash
git stash save "Descrição das mudanças"

# Listar todas as mudanças guardadas
git stash list

# Aplicar a mudança mais recente
git stash pop

# Aplicar sem remover da pilha
git stash apply

# Aplicar um stash específico
git stash apply stash@{0}

# Deletar um stash
git stash drop stash@{0}

# Deletar todos os stash
git stash clear
```

### git cherry-pick

**Descrição:** Aplica commits específicos de outro branch

```bash
# Aplicar um commit específico
git cherry-pick commit-hash

# Aplicar múltiplos commits
git cherry-pick commit-hash1 commit-hash2

# Aplicar um intervalo de commits
git cherry-pick commit-hash1..commit-hash2

# Continuar após resolver conflitos
git cherry-pick --continue

# Cancelar cherry-pick
git cherry-pick --abort
```

### git restore (NOVO - Git 2.23+)

**Descrição:** Restaura arquivos para uma versão anterior

```bash
# Restaurar um arquivo modificado
git restore arquivo.txt

# Restaurar arquivo para um commit específico
git restore --source=commit-hash arquivo.txt

# Remover arquivo da staging area
git restore --staged arquivo.txt
```

---

## Comandos Modernos (Git 2.23+)

### Comparação com Comandos Antigos

| Tarefa | Comando Antigo | Comando Moderno |
|--------|---|---|
| Mudar de branch | `git checkout branch` | `git switch branch` |
| Criar e mudar | `git checkout -b branch` | `git switch -c branch` |
| Restaurar arquivo | `git checkout arquivo` | `git restore arquivo` |
| Remover staging | `git reset arquivo` | `git restore --staged arquivo` |

**Por que migrar?** Os comandos modernos são mais específicos e intuitivos.

---

## Boas Práticas

### ✅ Commits

- **Mensagens claras:** "Adiciona autenticação de usuário" em vez de "fix"
- **Commits pequenos:** Um objetivo por commit
- **Frequentes:** Commit regularmente, não no final
- **Use formato padrão:**
  ```
  [Tipo] Descrição breve (máximo 50 caracteres)
  
  Explicação mais detalhada das mudanças
  (opcional, máximo 72 caracteres por linha)
  ```

### ✅ Branches

- Use nomes descritivos: `feature/login`, `fix/bug-404`, `docs/readme`
- Delete branches após merge
- Nunca trabalhe diretamente em `main` ou `master`
- Use um branch strategy (GitHub Flow, Git Flow)

### ✅ .gitignore

Crie um arquivo `.gitignore` na raiz do projeto para excluir arquivos:

```
# Dependências
node_modules/
venv/
__pycache__/

# Variáveis de ambiente
.env
.env.local

# Arquivos de sistema
.DS_Store
Thumbs.db

# IDE
.vscode/
.idea/

# Build
dist/
build/
*.log
```

### ✅ Colaboração

- Faça `git pull` antes de começar
- Crie Pull Requests para revisão de código
- Resolva conflitos antes de merge
- Use `git log --graph --oneline --all` para visualizar histórico

### ✅ Segurança

- Nunca commit senhas ou tokens (use `.env`)
- Use SSH em vez de HTTPS quando possível
- Assine commits importante com GPG: `git commit -S`

---

## Referência Rápida

```bash
# Iniciar um projeto
git init
git config user.name "Nome"
git config user.email "email@exemplo.com"

# Trabalhar com mudanças
git status                  # Ver mudanças
git add .                   # Adicionar mudanças
git commit -m "Mensagem"    # Confirmar

# Trabalhar com branches
git branch                  # Listar branches
git switch -c novo-branch   # Criar e mudar
git merge outro-branch      # Mesclar

# Sincronizar com remoto
git fetch                   # Baixar mudanças
git pull                    # Atualizar branch
git push origin branch      # Enviar mudanças

# Ver histórico
git log --oneline           # Histórico resumido
git log --graph --all       # Histórico visual
git show commit-hash        # Ver commit específico

# Desfazer mudanças
git restore arquivo.txt     # Descartar mudanças
git reset HEAD arquivo.txt  # Remover da staging
git reset --hard commit     # Desfazer commits
```

---

## 📚 Recursos Adicionais

- [Documentação Oficial do Git](https://git-scm.com/doc)
- [Pro Git Book](https://git-scm.com/book/pt-BR/v2)
- [GitHub Docs](https://docs.github.com)
- [Atlassian Git Tutorials](https://www.atlassian.com/git/tutorials)

---

**Contribuições são bem-vindas!** Se encontrar erros ou quiser adicionar conteúdo, abra uma issue ou pull request.
