---
layout: post
title: GIT - Um guia rápido
---


- Download do GIT: https://git-scm.com/download
- git init : Utilize este comando de dentro da pasta de seu projeto para iniciar um novo repositório local.

- git config: Para configurar o email e usuário. Com a flag --global, o usuário é configurado para todos os repositórios da máquina.

  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"

- git status: Exibe o status dos arquivos presentes no repositório. Mostra também alteraçes realizadas nestes arquivos.

- git add: Adiciona os arquivos para a área de commit (index ou staging area. Após o commit, a versão commitada é chamada de HEAD). 'git add .' adicionará todo o repositório atual. Serve para novos arquivos ou arquivos alterados. 'git add caminho/do/diretorio' também adicionará o diretório completo.
 
- git ls-files: Comando para listar os arquivos que já estão sendo controlados.

- git log: Exibe um histórico resumido dos últimos commits.

- git whatchanged: Mostra quais foram os arquivos alterados nos últimos commits. com a flag -p exibe as alterações de cada arquivo indivudalmente.

- git remote add origin url-do-repositorio-remoto: configura o repositório remoto para o projeto.

- git push apelido-do-repositorio branch-criado : Envia as alteraçes para o repositório remoto. A flag -u indica que a branch local deve ser igual à branch remota com o mesmo alias.

- git push -d remote-alias branch-alias Remove o branch especificado.

- git branch branch-alias: Cria um novo branch com o alias especificado. Com a flag -r exibe as branches remotas.
  git branch branch-alias -b: Cria um novo branch e altera para a branch atual.
  git branch -t branch-alias origin/correspondent-remote-branch-alias: Cria um branch com um branch remoto correspondente, monitorando as diferenças já no momento da criação.
 
  
- git checkout alias-branch-destino: Altera o working branch para o branch de destino especificado.

- git fetch origin: Verifica todas as atualizaçes do repositório origin.

- Conflitos:

- Ao utilizar o comando git push, caso hajam conflitos no arquivo que se deseja subir para o repositório remoto, o GIT alertará o conflito. Para indicar que o conflito foi selecionado, usar os comandos'git add arquivo', 'git commit arquivo -m "mensagem do commit". Desta forma será indicado que o conflito foi solucionado e o git push poderá ser executado.'

- O Git utiliza os caracteres >, < e =. Entre o < e o = fica o conteúdo antigo e entre o > e = fica o conteúdo novo.
