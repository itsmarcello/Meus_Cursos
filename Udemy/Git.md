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

  ```
  Antes de criar uma nova branch, volte para a master e dê um GIT PULL, para garantir que todos os dados estão atualizados ao criarmos na nova Branch 
  ```
  É sempre bom criamos uma branch para nova featura da aplicação que estamos criando. 

  * Criar uma branch: *git branch nome_da_branch*
  * Deletando Branch: *git branch -d ou --delete nome_da_branch*
  * Mudar de brach *git checkout -b 'nome_do_arquivo'* É justamente o '-b' que permite mudar e criar a branch ao mesmo tempo
  * Unindo Branch (MERGE): Estando na branch que voce quer como principal (geralmente a master), execute o codigo com o nome da branch da qual voce quer trazer os dados  *git merge 'nome_da_branch*. 

  ## Stash
Salvar as modificações atuais para testar uma outra abordagem, sem perder o codigo atual. 

* Volta o Branch para a master: *git stash*
* Para recupar um Ssh ja feito: *git stash apply ID* PS: Antes de trocar para outro stash, é necessario salvar as mudanças atuais em um stash novo. 
* Ver mudanças: git stash show -p ID
* Deletando Stash: git stash drop ID. Ou git stash clear, para apagar todas

## Tag

As Tags servem como checkpoints para as branches, marcando estagios do desenvolviemnto

* Criand a Tag: git tag -a nome_da_tag -m "mensagem"  
* Listar tags: git tag
* Ver detalhes da tag: git show nome_da_tag (q para sair)
* Enviando um tag para o servidor: git push origin nome_da-tag
* Enviar todas as tags: git origin --tags. O Repositorio receberá uma Tag e não uma branch, como estávamos fazendo. Assim, outra pessoa pode continnuar o desenvolvimento a partir da sua Tag já criada.




