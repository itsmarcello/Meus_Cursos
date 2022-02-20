# Curso de GIT

## Definicoes
 * Repositorio: Onde os codigos sao Armazenados. Cada projeto sera um repositorio. Github e gitbucket sao os servidores de gerenciamento de repositorios. 

 ## Comandos
  * Enviar para a Origem/Master: *git push -u origin master*
  * Saber o que foi modificado: *git status*
  * Adicionar arquivos antes do Commit:     *git add*,  *git add.* 
  * Atualizando suas pastas locais: *git pull* <span style="color:red"> Faça Frequentemente! </span>
  * Clonando Repositorio: *git clone*
  * Deletando arquivos do git: *git rm*
  * Verificando todos os Commits: *git log*  "q" para sair da tela
  * Renomenando/ Movendo arquivos: *git mv arquivo.py destino/arquivo.py*

  * Resetar um arquivo conforme ele esta na master *git checkout nomearquivo.py*

  * Resetar uma branch para ficar conforme a master
  *git reset --hard origin/master*

  ## Branches

  É sempre bom criamos uma branch para nova featura da aplicação que estamos criando. 

  * Criar uma branch: *git branch nome_da_branch*
  * Deletando Branch: *git branch -d ou --delete nome_da_branch*
  * Mudar de brach *git checkout -b 'nome_do_arquivo'* É justamente o '-b' que permite mudar e criar a branch ao mesmo tempo
  