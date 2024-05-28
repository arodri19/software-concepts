Aqui estão alguns dos comandos Git mais comuns:

```bash
git init # inicializa um novo repositório Git
git clone <url> # clona um repositório existente

git status # mostra o status do repositório atual
git add <file> # adiciona um arquivo ao stage
git commit -m "<message>" # cria um novo commit com a mensagem fornecida

git push <remote> <branch> # empurra os commits para o branch remoto
git pull <remote> <branch> # puxa as mudanças do branch remoto

git branch # lista todos os branches
git branch <name> # cria um novo branch
git checkout <branch> # muda para o branch especificado

git merge <branch> # mescla o branch especificado ao branch atual
git rebase <branch> # aplica os commits do branch atual em cima do branch especificado

git log # mostra o histórico de commits
git diff # mostra as diferenças entre o stage e o último commit
```

Lembre-se de substituir `<url>`, `<file>`, `<message>`, `<remote>`, `<branch>` e `<name>` pelos valores apropriados para o seu caso.

Existem algumas maneiras de desfazer um commit no Git, dependendo do que você deseja alcançar.

1. **Se você deseja desfazer o último commit e manter as alterações no seu diretório de trabalho (não no stage), você pode usar `git reset --soft HEAD~1`.**

```bash
git reset --soft HEAD~1
```

2. **Se você deseja desfazer o último commit e manter as alterações no stage (prontas para commit), você pode usar `git reset --mixed HEAD~1`.**

```bash
git reset --mixed HEAD~1
```

3. **Se você deseja desfazer o último commit e descartar todas as alterações, você pode usar `git reset --hard HEAD~1`.**

```bash
git reset --hard HEAD~1
```

4. **Se você já fez push do seu commit para o repositório remoto e deseja desfazer isso, você pode criar um novo commit que desfaz todas as alterações feitas no commit anterior usando `git revert HEAD`.**

```bash
git revert HEAD
```

Lembre-se de que `HEAD~1` significa "um commit antes do HEAD (o commit atual)". Se você quiser desfazer mais de um commit, pode usar `HEAD~2` para dois commits atrás, `HEAD~3` para três, e assim por diante.

Para visualizar o histórico de commits no Git, você pode usar o comando `git log`. Este comando mostra uma lista de todos os commits no branch atual em ordem cronológica inversa.

```bash
git log
```

A saída padrão do `git log` inclui o SHA do commit, o autor, a data e a mensagem do commit.

Se você quiser ver o histórico de commits com uma visão mais compacta, pode usar a opção `--oneline`:

```bash
git log --oneline
```

Isso mostrará cada commit em uma única linha, incluindo o SHA abreviado do commit e a mensagem do commit.

Se você quiser ver o histórico de commits mostrando as alterações feitas em cada commit, pode usar a opção `-p` ou `--patch`:

```bash
git log -p
```

Isso mostrará o diff introduzido em cada commit, além das informações padrão do commit.

O comando `git cherry-pick` é usado para aplicar as alterações introduzidas por alguns commits existentes para o branch atual. 

Aqui está um exemplo básico de como usar o `git cherry-pick`:

```bash
git cherry-pick <commit-hash>
```

Neste comando, substitua `<commit-hash>` pelo hash do commit que você deseja aplicar ao branch atual. 

Por exemplo, se você tem um commit com o hash `abc123` que você deseja aplicar ao branch atual, você usaria:

```bash
git cherry-pick abc123
```

Se você quiser aplicar várias commits, você pode listar todos os hashes de commit, separados por espaços:

```bash
git cherry-pick abc123 def456 ghi789
```

Lembre-se de que o `git cherry-pick` aplica as alterações de commit ao branch atual e cria um novo commit com essas alterações. Se você quiser incluir a mensagem de commit original, use a opção `-x`:

```bash
git cherry-pick -x <commit-hash>
```

Isso incluirá uma linha na mensagem de commit que indica o commit de origem.

Para alterar a última mensagem de commit, você pode usar o comando `git commit --amend`. Isso abrirá o editor configurado no seu Git, permitindo que você altere a mensagem do último commit.

```bash
git commit --amend
```

Se você quiser apenas alterar a mensagem sem alterar o commit em si, você pode usar a opção `-m` para fornecer a nova mensagem diretamente na linha de comando:

```bash
git commit --amend -m "Nova mensagem de commit"
```

Substitua "Nova mensagem de commit" pela mensagem que você deseja usar.

Lembre-se de que alterar a mensagem de commit criará um novo commit e o commit antigo será descartado. Se você já fez push do commit original para um repositório remoto, você precisará fazer push novamente usando a opção `--force`:

```bash
git push origin <branch-name> --force
```

Substitua `<branch-name>` pelo nome do seu branch. Tenha cuidado ao usar `--force`, pois isso pode sobrescrever as alterações no repositório remoto.