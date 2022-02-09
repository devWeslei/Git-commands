`Comando`: funcionalidade.   

 <h2> pegue um atalho 👇🏻</h2>   
 
- [Comandos principais do Git](#comandos-principais-do-git)
- [trabalhando com branches](#-trabalhando-com-branches-)
- [comandos não tão usuais, mas é bom saber](#-comandos-n%C3%A3o-t%C3%A3o-usuais-mas-%C3%A9-bom-saber)    

<h2 align="center">Comandos principais do Git</h2>  

`git init` : criar repositório.      
`git status` : verificar as mudanças do projeto.       
`git add`: adicionar novos arquivos para monitoramento git.        
>OBS: `git add .` adiciona vários arquivos de uma vez só.   
Ex: `git add formulário.txt` – adiciona o arquivo formulário.   
    `git add .` – adiciona todos os arquivos do projeto.   

`git commit`: guardar o estado do seu repositório local naquele momento. 
>OBS: vários arquivos de uma vez com a flag `-a`.

***É uma boa pratica enviar uma mensagem a cada commit com as alterações que foram feitas, a mensagem pode ser adicionada com a flag `-m`.**
>Ex: `git commit teste.css -m “Alterado rodape da pagina principal”` - salvar o estado do arquivo teste.css com a mensagem especificando a alteração.   
     `git commit -a -m “Adicionando Login”`– salvar o estado de todos arquivos com alterações do projeto, com a mensagem especificando a alteração.   

`git push`: Ação de enviar o código ao repositório remoto (que é o código fonte), quando finalizamos uma funcionalidade nova.   
***É importante acionar o `git status` frequentemente para saber os estados dos arquivos. Feito antes do push, o terminal mostrará quantos commits sua branch local está à frente da branch do código do servidor. Lembrando que a branch principal do servidor é a origin/main.
Após o push o código do servidor será atualizado baseando-se no código local enviado, discriminando todos os commits, passo-a-passo do que desenvolveu.**   

`git pull`: Ação de sincronizar o projeto local com as mudanças do remoto. Após o comando, se existir alteração no servidor (feitas normalmente por outro desenvolvedor), elas serão unidas ao seu código local.   
***É interessante acionar frequentemente para manter seu projeto local atualizado com os demais do time.**  

`git clone`: baixar um repositório de um servidor remoto, passando a referência do repositório remoto.
>OBS: este comando é utilizado quando entramos em um novo projeto, por exemplo.
Ex: `git clone https://github.com/fulanodetal/projeto_exe_1.git`

`git rm`: deletar arquivos da monitoração do git. 
>OBS: após deletar um arquivo do git, ele não terá mais suas alterações consideradas pelo git, apenas quando for adicionado novamente pelo `git add`.
Ex: `git rm formulario.txt` – exclui o arquivo formulario.

***Lembre-se de transmitir essa alteração para o repositório remoto dando 
`git commit -a -m “Deletando arquivos desnecessários”` e `git push` em sequência.**

`git log`: para receber uma informação dos commits realizados no projeto até então, com todas descrições da mensagem do commit, a data e o usuário.

`git mv`: renomear um arquivo ou mover para outra pasta. 
>OBS:O novo arquivo vai ser monitorado pelo git e o arquivo anterior é excluído.
Ex: `git mv rodape.css css/rodape.css` – movendo arquivo rodapé.css para a pasta css.
      `git mv bannerinicia.css bannerinicial.css`  - renomeando arquivo.
      
***Lembre-se de transmitir essa alteração para o repositório remoto com os comandos commit e push.**
  
`git checkout`: retorna o arquivo modificado ao original do repositório remoto (código fonte).
>Ex: `git checkout formulario.txt` – reseta o arquivo formulario conforme ele esta no arquivo remoto.

`git reset`: resetar as mudanças feitas da branch local. 
>Obs: geralmente é utilizado com a flag `--hard`, todas as alterações commitadas e também as pendentes serão excluídas.
Ex: `git reset --hard origin/master` – reseta o projeto para o ultimo estado do branch do repositório remoto.(do ultimo push do branch do remoto).

**Ignorando arquivos no projeto:** Devemos inserir um arquivo chamado `.gitignore` na raiz do projeto;       
***Nele podemos inserir todos os arquivos que não devem entrar no versionamento. Isso é útil parar arquivos gerados automaticamente ou arquivos que contêm informações sensíveis.**

<h2 align= "center"> Trabalhando com branches </h2>      

`git branch`: visualizar os branches disponíveis.   
`git branch <nome>`: cria um novo branch.   
`git branch -d <nome>` ou `git branch --delete <nome>`: para deletar um branch.   
`git checkout -b <nome>`:criar e mudar para outra branch.   
***alterando o branch podemos levar alterações que não foram commitadas junto, tome cuidado!**
   
`git switch -c <nome>`: novo jeito de criar e mudar para outra branch.   

`git checkout <nome>`: mudar para a branch.
`git switch <nome>`: novo jeito de mudar de branch.
***quando for trabalhar em uma funcionalidade nova, é importante que crie um branch novo em cima da main mais atualizada dando git pull no branch main e só depois criar um novo branch estando na main. Isso é boas práticas!**

`git merge <nome>`: unir dois códigos distintos de duas branches. 
>Obs: Normalmente é por meio dele que recebemos atualizações de outros devs.
***dificilmente dão merge do branch principal(main) pelo terminal, vai ser por alguma plataforma pois passará por correção. Mas, se seu branch está muito atrasado comparado à main, você pode dar merge do seu branch com a main para receber as atualizações da main e deixar a sua branch atualizada.**

`git stash`: para salvar as modificações atuais para prossegui com uma outra abordagem de solução e não perder o código. Após o comando o branch será resetado para a sua versão de acordo com o repositório.   
`git stash list`: verificar as stashes criadas.   
`git stash apply <numero stash>`: recuperar a stash, para continuar de onde parou com os arquivos adicionados a stash.   
`git stash clear`: para limpar totalmente as stash de um branch.   
`git stash drop <nome>`: para deletar uma stash específica.   

`git tag -a <nome> -m “<msg>”`:criar tags nos branches. 
>Obs: A tag é diferente do stash, serve como checkpoint de um branch, é utilizada para  demarcar estágios do desenvolvimento de algum recurso.
>
`git show <nome>`: verificar detalhada uma tag.
`git checkout <nome>`: trocar de tags.
`git push origin <nome>`: enviar tag para o repositório.
`git push origin --tags`: enviar todas as tags.

`git fetch`: você é atualizado de todos os branchs e tags que ainda não estão reconhecidos por você. 
>Obs: este comando é útil para utilizar o branch de algum outro dev do time. A nova branch ainda não vai ser reconhecida na lista enquanto não der checkout para a mesma.

**É extremamente importante dar um `git pull` na branch main toda vez que começar uma nova tarefa e, aí sim, criar uma nova branch com o `git checkout -b <nome>` tendo como parâmetro a main atualizada.**

`git commit --amend`: altera a mensagem do ultimo commit do histórico.
`git remote -v`: lista os links que o git esta apontando, como o (fetch – enviar)  e o (push – receber).   
`git remote rm origin`: apaga os links de referencia que o git está apontando. (exemplo acima).   
`git remote add origin <link>`: adiciona o repositório remoto que o git vai apontar.   
`git submodule add <repo>`: criar um outro projeto dentro do mesmo repositório.
> Obs: serve para projetos grandes com times de devs separados mas que os projetos usam as mesmas bibliotecas, então são projetos diferentes porém ligados a um submódulo.
> 
`git submodule`: lista os submódulos existentes no projeto. 
>Obs: para dar pull no submódulo basta estar o diretório dentro do arquivo submodule, caso queira dar pull na main basta voltar para dentro do arquivo da main.
>
`git push --recurse-submodules=on-demand`: para enviar para o repositório do submódulo (este fluxo fará a atualização apenas do submódulo).
> Obs: para atualizar um submódulo primeiro devemos commitar as mudanças.

<h2 align="center"> Comandos não tão usuais, mas é bom saber</h2>   
           
`git show`: mostrar informações do branch atual, as modificações dos arquivos e também seus commits.   
`git show <tag>`: exibir as informações de tags.   
`git diff`: exibir as diferenças do branch atual com o remoto.   
>Ex: `git diff main` - exibe no terminal as diferenças do seu arquivo para a main.   
Obs: também podemos verificar a diferença entre arquivos dando `git diff <arquivo> <arquivo_b>`

`git shortlog`: exibirá um log resumido do projeto, quais commits foram enviados ao projeto e por quem.

`git clean`: limpar arquivos que não estão sendo trackeados, ou seja, todos que não utilizou git add.

`git gc`: identifica e exclui arquivos que não são mais necessários, otimiza a performance do repositório. 
>Obs: pode ser utilizado com não tanta frequência, de mês em mês por exemplo.
>
`git fsck`: verificar a integridade dos arquivos e sua conectividade. 
>Obs: comando de rotina para ver se está tudo certo com nossos arquivos.

`git reflog`: mapear todos seus passos no repositório, até uma mudança de branch é inserida neste log. Por padrão, os reflogs expiram em 30 dias.

`git archive --format zip --output main_files.zip main`: transformar o repositório em um arquivo compactado, e então a branch main vai estar zipada no arquivo main_files.zip.   

</br>

>if this project helped you, contribute by giving a ⭐ !! I'll be grateful 😁      

</br>   
<div align="center">   
  
   [![Linkedin Badge](https://img.shields.io/badge/-weslei%20tiago-292929?style=flat-square&logo=Linkedin&logoColor=white&link=https://www.linkedin.com/in/weslei-tiago-53b47a208/)](https://www.linkedin.com/in/weslei-tiago-53b47a208/)   
  
   </div>
