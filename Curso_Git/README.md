
# CURSO GIT 

## Limpar a tela ( clear)

## Abrindo uma pasta ( cd )
cd C:\Users\irsma
cd Desktop

## Mostrar todos os arquivos de uma pasta ( ls ou dir)
cd Desktop
ls

## Sair de pastas ou voltar no diretorio  (cd ..)

## Criar pastas ( mkdir NOME )

## Mostrar tudo que sofreu alterações ( git status )

## Adicionar novos arquivos ao Trakcing ( git add -A )
git add NOME
git add -A -> pega todos os novos

## Finalizar alterações locais ( git commit -m "COMENTÁRO" )
git commit -m "Criação dos arquivos"
git commit -am "Criação dos arquivos"  -> Add e Commit ao mesmo tempo

## Lista de Todos os Commits ja dados em um git ( git log )

## Revertendo modificações (git reset --MODO IDCOMMIT)
Modo:
soft: volta no tempo, porem mantendo arquivos antes do Commit
mixed: Quase o mesmo
hard: realmente volta TUDO
Idcommot: 
Ex: c2faf11cc4476b3c61e0170f78f5aee9b8127636

## Mostrar Branch atual ( git branch )

## Criar Branch ( git branch NOME)
git branch Novos_Cursos

## Mudar de Branch ( git checkout NOME )
git checkou Novos_Cursos

## Diferenciação entre dois arquivos o tempo ( git diff ) 
a letra q sai do (end)
git diff --name-only -> Só o nome do arquivo que foi modificado
git diff NOME

## Reverter alteração antes do commit ( git checkout HEAD -- NOME )  

## Voltar à alguma commit especifico, mas guardando commit feito ( git revert --no-edit )

## Deletar branch na Cloud ( git push origin :NOME)
## Deletar branch Local (git branch -D NOME)

## PULL arquivos da nuvem (git pull origin master)

## Clone de um projetopara o meu local (git clone URL)
Crie uma nova pasta
Copie a URL do site
Use: git clone https://github.com/TEstudos/Curso_HTML5_GustavoGuanabara

## 
