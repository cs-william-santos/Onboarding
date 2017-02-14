# Pratical GIT

### Comandos principais do GIT

Ao longo deste documento, teremos uma breve explicação para facilitar o entendimento.

**Criar um repositório** 
Crie um novo diretório e em seguida digite o comando:


```sh
$ git init
```
Crie uma cópia de trabalho para o repositório local executando o comando:
``` sh
git clone </path/to/resository>
```
Ao usar um servidor remoto o comando será:
``` sh
git clone <user>@<server>:</path/to/repository>
```
**Fluxo do Trabalho**

Os repositórios locais consistem em três "trees" mantidas pelo git:

* First is your **WORK DIRECTORY** that contains the current files;
* Second **INDEX** that functions as a temporary area;
* And, finally, the **HEAD** that points to the last commit.
Add and confirm.

* Primeiro é o seu **WORK DIRECTORY** que contém os arquivos atuais;
* Segundo **INDEX** que funciona como uma área temporária;
* E, finalmente, o **HEAD** que aponta para o último commit.
Adicione e confirme.


|WORK DIRECTORY||INDEX||HEAD
:-:|:-:|:-:|:-:|:-:|
![IMAGE ALT TEXT HERE](https://cdn1.iconfinder.com/data/icons/line-mix-vol-3/128/-60-128.png) | **add** |![IMAGE ALT TEXT HERE](https://cdn4.iconfinder.com/data/icons/aami-web-internet/64/aami14-02-128.png)|**commit**|![IMAGE ALT TEXT HERE](https://cdn3.iconfinder.com/data/icons/basic-mobile-part-2/512/folder_tree-128.png)
|||**STAGE**|||

Para propor as alterações (adicione-as ao Índice), informar o git que você deve controlar o arquivo, use o comando:

``` sh
git add <file>
git add *
```

Este é o primeiro passo no fluxo de trabalho git básico. Para confirmar as alterações e confirmar utilize o commit, desta forma:

``` sh
git commit -m "Comentário da mudança"
``` 
Agora os arquivos serão carregados em HEAD, mas ainda não serão carregados para o repositório remoto.

**Enviando as alterações**
As mudanças estão agora no HEAD em sua cópia de trabalho do trabalho. Para enviar essas alterações para o seu repositório remoto, execute:
``` sh
git push origin master
```
Para alterar a branch master para qualquer outra, enviando suas alterações a ela.

Se você não clonou um repositório existente e deseja conectar seu repositório a um servidor remoto, deve adicioná-lo com:
``` sh
git remote add origin <server>
```
Você agora pode enviar suas alterações para o servidor remoto selecionado.
Branched.

The branches are used to develop characteristics isolated from each other. The master branch is the "default" branch when you create a repository. Use other branches to develop and merge them into the master branch upon completion.

As branches são utilizadas para desenvolver características isoladas umas das outras. O ramo master é o ramo "padrão" quando você cria um repositório. Use outras branches para desenvolver e mesclá-los na branch master após a conclusão.

Criado uma nova branch com o nome **function_x**, para selecionar utilize:
```sh
git checkout -b function_x
```
Para retonar a branch master, use o comando:
``` sh
git checkout master
```
Remover a branch, para remover faça desta maneira: 
``` sh
git branch -d function_x
```
Uma branch não está disponível para outras pessoas a menos que você envie a branch para o repositório remoto.

``` sh
git push origin <function_x>
```
**Atualizar e mesclar**

Para atualizar seu repositório local com a versão mais recente, execute:
```sh
git pull <branch origen> <destino branch>
```

Em seu diretório de trabalho para obter e mesclar alterações remotas.
Para mesclar outra ramificação para sua ramificação ativa (por exemplo, master), use:

``` sh
git merge <branch>
```
Em ambos os casos, intercala as alterações automaticamente. Mas, nem sempre acontece e resulta em conflitos. Você precisará resolver a mesclagem desses conflitos manualmente editando os arquivos exibidos pelo git. Depois de alterar, você precisa marcá-los com merge e feito:

```sh
git add <file>
```
Antes de mesclar as alterações, você também pode visualizá-las usando:
```sh
git diff <branch origem> <destino branch>
```
**Rotulando**

é recomendado criar rótulos para releases de software. Este é um conhecido conceito, que também existe no SVN. Você pode criar um novo rótulo chamado 1.0.0 executando o comando
```sh
git tag 1.0.0 1b2e1d63ff
```
o **1b2e1d63ff** representa os 10 primeiros caracteres do id de commit que você quer referenciar com seu rótulo. Você pode obter o id de commit com 
``` sh
git log
```
Você pode também usar menos caracteres do id de commit, ele somente precisa ser único. 

**Sobrescrever** 

Se cometer algum erro, você pode sobrescrever as alterações locais usando o commando:
```sh
git checkout -- <file>
```
Isso substitui como em sua árvore com o conteúdo mais recente. Alterações adicionadas ao índice, bem como novos arquivos serão mantidas.

Se ao invés disso você deseja remover todas as alterações e commits locais, recupere o histórico mais recente do servidor e aponte para seu branch master local desta forma

```sh
git fetch origin
git reset --hard origin/master
```
