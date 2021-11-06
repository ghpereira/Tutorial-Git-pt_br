# Tutorial-Git-pt_br
Arquivo de auxílio para quem tem dificuldades com comando GIT. Comandos explicados.

Comandos que serão explicados neste documentos.
git config
git init
git clone
git add
git commit
git diff
git reset
git status
git rm
git log
git show
git tag
git branch
git checkout
git merge
git remote
git push
git pull
git stash

Comandos do Git
### git config ###
Uso: git config –global user.name “[nome]”
Uso: git config –global user.email “[endereço de email]”
Este comando define o nome do autor e endereço de e-mail respectivamente para serem usados ​​com seus commits.

### git init ###
Uso: git init [nome do repositório]
Este comando é usado para iniciar um novo repositório.

### git clone ###
Uso: git clone [url]
Este comando é usado para obter um repositório de uma URL existente.

### git add ###
Uso: git add [arquivo]
Este comando adiciona um arquivo à área de teste.

Uso: git add *
Este comando adiciona um ou mais arquivos à área de teste.

### git commit ###
Uso: git commit -m “[Mensagem do commit]”
Este comando registra ou captura o arquivo permanentemente no histórico da versão.

Uso: git commit -a
Este comando confirma todos os arquivos que você adicionou com o comando git add e também confirma todos os arquivos que você alterou desde então.

### git diff ###
Uso: git diff
Este comando mostra as diferenças de arquivo que ainda não foram testadas.

Uso: git diff –staged
Este comando mostra as diferenças entre os arquivos na área de teste e a versão mais recente presente.

Uso: git diff [primeira branch] [segunda branch]
Este comando mostra as diferenças entre as duas branch mencionadas.

### git reset ###
Uso: git reset [arquivo]
Este comando remove o teste do arquivo, mas preserva o conteúdo do arquivo.

Uso: git reset [commit]
Este comando desfaz todos os commits após o commit especificado e preserva as mudanças localmente.

Uso: git reset –hard [commit]
Este comando descarta todo o histórico e volta para o especificado commit.

### git status ###
Uso: git status
Este comando lista todos os arquivos que precisam ser confirmados.

### git rm ###
Uso: git rm [arquivo]
Este comando exclui o arquivo de seu diretório de trabalho e organiza a exclusão.

### git log ###
Uso: git log
Este comando é usado para listar o histórico de versão para a branch atual.

Uso: git log –follow[arquivo]
Este comando lista o histórico de versão de um arquivo, incluindo a renomeação de arquivos também.

### git show ###
Uso: git show [commit]
Este comando mostra os metadados e as mudanças de conteúdo do commit especificado.

### git tag ###
Uso: git tag [commitID]
Este comando é usado para dar tags ao commit especificado.

### git branch ###
Uso: git branch
Este comando lista todos os branches locais no repositório atual.

Uso: git branch [branch name]
Este comando cria uma nova ramificação.

Uso: git branch -d [branch name]
Este comando exclui a ramificação/branch do recurso.

### git checkout ###
Uso: git checkout [branch name]
Este comando é usado para mudar de uma branch para outra.

Uso: git checkout -b [branch name]
Este comando cria uma nova ramificação e também muda para ela.

### git merge ###
Uso: git merge [branch name]
Este comando mescla o histórico do branch especificado no branch atual.

### git remote ###
Uso: git remote add [nome variável ex. origin] [Link de servidor remoto]
Este comando é usado para conectar seu repositório local ao servidor remoto.

### git push ###
Uso: git push [nome variável ex: origin] master
Este comando envia as alterações confirmadas do branch master para seu repositório remoto.

Uso: git push [nome variável ex: origin] [branch ex: master]
Este comando envia os commits do branch para o seu repositório remoto.

Uso: git push –all [variable name ex: origin]
Este comando envia todos os branches para seu repositório remoto.

Uso: git push [variable name] :[branch name]
Este comando exclui um branch em seu repositório remoto.

### git pull ###
Uso: git pull [Link do repositorio]
Este comando busca e mescla as mudanças no servidor remoto em seu diretório de trabalho.

### git stash ###
Uso: git stash save
Este comando armazena temporariamente todos os arquivos controlados modificados.

Uso: git stash pop
Este comando restaura os arquivos escondidos mais recentemente.

Uso: git stash list
Este comando lista todos os conjuntos de mudanças armazenados.

Uso: git stash drop
Este comando descarta o conjuntos de mudanças armazenados mais recentemente.
