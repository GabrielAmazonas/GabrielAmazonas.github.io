---
layout: post
title: GIT - Um guia rápido
---


## Download do GIT: https://git-scm.com/download

### Comandos Básicos:

- `git init` : Utilize este comando de dentro da pasta de seu projeto para iniciar um novo repositório local.

- `git config`: Para configurar o email e usuário. Com a flag --global, o usuário é configurado para todos os repositórios da máquina.

  `git config --global user.email "you@example.com"`
  `git config --global user.name "Your Name"`

- `git status`: Exibe o status dos arquivos presentes no repositório. Mostra também alteraçes realizadas nestes arquivos.

- `git add`: Adiciona os arquivos para a área de commit (index ou staging area. Após o commit, a versão commitada é chamada de HEAD). 'git add .' adicionará todo o repositório atual. Serve para novos arquivos ou arquivos alterados. 'git add caminho/do/diretorio' também adicionará o diretório completo.
 
- `git ls-files`: Comando para listar os arquivos que já estão sendo controlados.

- `git log`: Exibe um histórico resumido dos últimos commits.

- `git whatchanged`: Mostra quais foram os arquivos alterados nos últimos commits. com a flag -p exibe as alterações de cada arquivo indivudalmente.

- `git remote add origin url-do-repositorio-remoto` : configura o repositório remoto para o projeto.

- `git push apelido-do-repositorio branch-criado` : Envia as alteraçes para o repositório remoto. A flag -u indica que a branch local deve ser igual à branch remota com o mesmo alias.

- `git push -d remote-alias branch-alias` Remove o branch especificado.

- `git branch branch-alias`: Cria um novo branch com o alias especificado. Com a flag -r exibe as branches remotas.

-  `git branch branch-alias -b`: Cria um novo branch e altera para a branch atual.

- `git branch -t branch-alias origin/correspondent-remote-branch-alias`: Cria um branch com um branch remoto correspondente, monitorando as diferenças já no momento da criação.
 
- `git checkout alias-branch-destino`: Altera o working branch para o branch de destino especificado.

- `git fetch origin`: Verifica todas as atualizaçes do repositório origin.

### Conflitos:

- Ao utilizar o comando `git push`, caso hajam conflitos no arquivo que se deseja subir para o repositório remoto, o GIT alertará o conflito. Para indicar que o conflito foi selecionado, usar os comandos `git add arquivo`, `git commit arquivo -m "mensagem do commit"`. Desta forma será indicado que o conflito foi solucionado e o git push poderá ser executado.'

- O Git utiliza os caracteres >, < e =. Entre o < e o = fica o conteúdo antigo e entre o > e = fica o conteúdo novo.

- Trabalhando com múltiplos branches:

- `git branch checkout -b nomeDoBranch` : Cria e entra na branch 
- `git checkout master` & `git pull` antes de atualizar o branch master; 
- `git merge nomeDoBranch`: Irá trazer os commits do branch indicado para a branch atual.
- `git push` enviará as novas alterações para o repositório.
- Em outro branch, ao realizar: `git checkout master` e `git pull`, irão ser trazidas as alterações mais recentes da branch master.
- `git rebase` atualiza uma branch com base em outra.
- Exemplo: `git rebase master desenvolvimento`: Atualizará a branch desenvolvimento com base na branch master.
- após o `git rebase`, o branch selecionado estará atualizado, com os commits realizados no próprio branch e os commits realizados na master. 
- agora é possível voltar para a branch master através do comando `git checkout master` e trazer os commits da branch desenvolvimento através do comando `git merge desenvolvimento`. Para enviar as alterações do branch master para o repositório remoto, basta utilizar novamente o comando `git push`.

### Resolvendo conflitos entre os branches:

- Caso ao rodar o comando `git pull` já hajam atualizações do branch master, o usuário deverá usar o `git rebase master desenvolvimento` para atualizar sua branch de desenvolvimento atual com base na branch master do repositorio.

- Ao ocorrer o conflito, o GIT indicará em que arquivo o conflito foi gerado. Após solucionar o conflito, o usuário deverá usar o comando `git add arquvioDoConflito.formato` para adicionar novamente o arquivo ao staging area e prepará-lo para o commit

- O usuário deverá utilizar o `git rebase --continue` para seguir com o rebase que foi pausado pelo conflito.

- Os conflitos são gerados Commit por Commit, o que torna mais fácil a resolução.

### Revertendo arquivos para o estado anterior:

- O comando `git checkout nomeDoArquivo.formato` pode ser utilizado para retorna o estado do último commit deste arquivo. 
- `git checkout arquivo` só funcionará e reverterá o arquivo caso o mesmo não esteja pronto para ser commitado. (Não tenha sido usado como parâmetro para o `git add`.

- Caso o arquivo já esteja pronto para commit e seja necessário revertê-lo, deverá ser utilizado o comando `git reset -HEAD nomeDoArquivo.formato`, que alteraráo estado do arquivo de staged para unstaged antes de realizar o `git checkout nomeDoArquivo.formato`.

- para reverter para um commit anterior, é possível utilizar o comando: `git reset id-do-commit`. O id do commit pode ser encontrado através do comando `git log`. Esta opção irá desfazer TODOS os commits posteriores ao commit selecionado, porém irá manter as alterações nos arquivos em modo unstaged. 

- Para reverter as alterações causadas por um único commit , é utilizado o comando `git revert id-do-commit`. Com este comando, é gerado um novo commit que desfaz o commit selecionado.

- Para salver o estágio atual do arquivo temporariamente, utiliza-se o comando `git stash`. Já o comando `git stash list` irá exibir os arquivos salvos no stash. 

- Para retomar o desenvolvimento de um arquivo do stash, usar o comando `git stash apply nomeDoStash`. O nome do stash possui o formato "Stash@{0}" e é exibido através do `git stash list`.

- Para descartar os arquivos do `git stash`, o comando `git stash drop` pode ser utilizado. O ideal é utilizar após o apply do stash desejado.

### Busca avançada de commits:

- `git bisect start` Iniciará o modo de busca dos commits com problema.
- Este comando necessita dos comandos `git bisect bad nome-do-commit-defeituoso` e `git bisect good nome-do-commit-sem-defeito`.
- Com estes comandos, o git trará os commits realizados entre o commid bad e o commit good, um a um e pedirá para que o desenvolvedor especifique se este é um commit good ou bad.
- Este modo irá alternar entre os commits do intervalo selecionado de acordo com o que o desenvolvedor sinalziar como git good ou git bad.



