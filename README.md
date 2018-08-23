# [cygwin](http://www.cygwin.com/) 
- Terminal que utiliza, no Windows, comandos básicos do Linux, bash  
do Unix 
- [Básico sobre o cygwin](https://youtu.be/TFCCriN_MvU?t=11m40s)
- Cmder também aceita comandos Unix

# Comandos terminal Linux 
- `pwd` print working directory 
- `cd /` change directory to root 
- `ls` lista as pastas do diretório atual 
  - `-la` parâmetro que lista os arquivos e pastas do diretório  
  atual, **inclusive os ocultos**. Nos sistemas Unix, todo diretório  
  que começa com `.` é um arquivo oculto 
  - `-l` parâmetro que mostra apenas os arquivos visíveis 
    - Mostra os arquivos com mais detalhes 
      - Data da última alteração
      - Tamanho
      - Usuário
- `cd cygdrive` entra no root do windows 
  - `ls` lista os discos rígidos do windows 
- `clear` limpa o terminal 
- `mkdir` cria um diretório no diretório atual 
- `touch nomeArquivo.extensao` cria um arquivo
- `rm` deleta um arquivo do diretório atual 
- `rm -r` deleta um diretório 
- `cat` mostra, no terminal, o conteúdo de um arquivo 
- `echo` imprime uma string dentro de um arquivo 
  - `echo "uma string" >> nomeArquivo.extensao`
    - Se o arquivo não existir, ele é criado 
- `/cygdrive/c/Users/roger/` acessa o diretório de usuário

# O que é o Git 
- Sistema de controle de versão 
  - Ajuda a controlar versões de projetos 
  - Permite o acesso à todas as alterações feitas em um projeto 
  - Permite o acesso ao histórico de todas as versões do projeto 
    - Cria pontos específicos no tempo 

# Por que usar 
- Resolver problemas de controle de versão manuais 
  - Permite o abandono de cópia e renomeação de pastas e arquivos  
  ao serem alterados 

# Instalando o [Git](https://git-scm.com)
- Após a instalação, o comando `git` estará disponível no terminal 

# [Instalando o Git no Cygwin](https://www.youtube.com/watch?v=mwu0FuHkjBg)
- Deve ser selecionado ao instalar ou reinstalar o sygwin, na opção  
'devel $ default'

# Comandos iniciais do Git 
- `git --version` mostra a versão do Git instalada 
- `git` mostra alguns comandos de ajuda 
- `git init` inicia um repositório do git 
  - Cria um diretório `.git` oculto no diretório atual 
  - Esse diretório permite a inicialização e criação de históricos de  
  alterações dos arquivos
- `git status` mostra o status da árvore atual do git
  - Pode ser utilizado a qualquer momento 1
  - Mostra todos os arquivos alterados desde o último commit 
  - Mensagens
    - "Changes not staged for commit" indica que um arquivo já  
    adicionado à staging area anteriormente foi modificado. Ou seja,  
    o arquivo já faz parte do repositório .git, mas possui alterações 
    - "Changes to be committed:" indica que desta vez, há alterações  
    a serem commitadas
    - Caso um novo arquivo tenha sido criado após o último commit,  
    o arquivo será mostrado como 'untracked'. Ou seja, o arquivo ainda  
    não está na staging area 

# Untracked files
- São arquivos que foram criados e ainda não foram adicionados à staging  
area e nem fazem parte do `.git` directory 
- Se um arquivo que já faz parte da staging area for alterado, a mensagem  
é que o arquivo foi **modificado**
- Se um arquivo ou pasta é criado e deletado sem ter sido adicionado à  
staging area (`git add`), ao dar um `git status`, o arquivo não será  
mostrado como deletado 
- O git, por padrão, não faz commit de diretórios vazios
  - É necessário que o diretório tenha, pelo menos, um  
  arquivo 

# Estágios do Git 
- Estágios são, basicamente, 3 momentos do projeto 
![estagios-git](https://user-images.githubusercontent.com/29297788/43348687-b9edea20-91d1-11e8-843d-16369b268a44.jpg)

1. Working Directory
  - É o diretório atual em que se está trabalhando 
  - A primeira etapa a ser feita é adicionar o arquivo deste estágio para  
  o estágio 2 (Staging Area)
2. Staging Area
  - Momento em que os arquivos foram adicionados, onde o próximo passo é  
  commitá-los (incluí-los) no `.git` directory 
3. .git directory (Repository)
  - Este repositório é local, fica apenas na máquina que está sendo  
  usada. Ninguém tem acesso ao repositório. 
  - Guarda todo o histórico de commits do projeto 

## `git add <file>` 
- Passa arquivos do Working Directory para o Staging Area 
  - Aceita vários arquivos por parâmetro, separados por espaço:  
  `git add <file1> <file2>`
- Após executado, caso um git status seja declarado, será exibida  
uma mensagem 'changes to be commited', ou seja, a mensagem já não  
é de untracked files como anteriormente 
- Ou seja, agora o arquivo foi adicionado na staging area, mas  
ainda não faz parte do .git directory (repositório)

## `git add .`
- Adiciona todos os arquivos alterados no Working Directory para  
o Staging Area 
- Não adiciona arquivos deletados 

## Configurações pré-commit 
- Os comandos abaixo precisam ser setados apenas uma única vez 
  - Não é por projeto, é apenas uma única vez 
- Essas configurações irão valer para todos os projetos do git 
- Ficarão listadas no histórico 

### `git config --global user.name "Nome Aqui"`
- Diz para o git **quem ** está colocando o arquivo no repositório  
.git

### `git config --global user.email "endereco@email"`
- Informa o email de quem colocou está colocando o arquivo no  
repositório .git

### `git config -l` ou `git config --list`
- Lista as configurações 
- Verifica se os comandos setados funcionaram corretamente 

### `git config <property>` 
- algumas propriedades possíveis 
  - `user.name`
    - Mostra meu nome de usuário cadastrado
  - `user.email`
    - Mostra meu e-mail cadastrado
  - `core.editor`
    - Mostra o editor de texto padrão para a edição de mensagens  
    de commits 

## `git commit` - Commitando sem o parâmetro `-m`
- Se este comando for executado, o editor de texto será aberto  
para que a mensagem de commit possa ser editada 
  - Edição possível: 
    - Título da mensagem de commit (1ª linha)
    - Corpo da mensagem de commit
      - Pode ser uma lista: 
       - Item 1
       - Item 2
       - Item 3...
- Permite detalhar melhor o que foi feito naquele commit 
- Após editar a mensagem e dar um `git log`, o commit mais  
organizado é mostrado no terminal 
  - Muito importante ao usar o GitHub 

## Setando o editor da mensagem de commit para todos os projetos 
- No Windows, o recomendado é o Vim

## Comandos do Vim para a edição da mensagem de commit
- `i` entra no insert mode, para que o código / mensagem seja  
inserida
- `esc` sai do modo de inserção
- `:wq + enter` sai do vim 

## `git commit -m "Commit Message"`
- Passa o arquivo da staging area para o .git directory 
- Limpa o working directory 
- Ideal para **mensagens pequenas**
  - O `git commit` (sem `-m`) deve ser usado para mensagens  
  detalhadas 
- A mensagem a ser colocada deve ser informativa, que diga  
exatamente qual alteração foi feita e porque ela foi feita 
- Após a execução do comando, serão mostradas uma hash que foi  
criada para o commit, a mensagem informada, a quantidade de  
arquivos e linhas alteradas, e o arquivo que foi criado
- Se o `git status` for executado após o commit, uma mensagem  
dizendo que o working directory está limpo será mostrada 

## `git log`
- Permite visualizar todos os commits adicionados no  
repositório .git (histórico)
  - Cada commit mostrado é uma versão do projeto 
- Mostra uma hash que representa o commit feito, o nome e  
e-mail de quem fez o commit, a data e horário e a mensagem  
- O commit mais recente fica na parte superior da listagem 

## `git log --name-status`
- Além das informações presentes no `git log` padrão, exibe,  
o nome dos arquivos que foram alterados ou excluídos, além do  
hash do commit, autor, data e mensagem de commit 
  - A: add. Arquivos que foram adicionados 
  - M: modified. Arquivos que foram modificados 
  - D: deleted. Arquivos que foram deletados 
- Auxilia a visualização em casos onde é necessário voltar ao  
histórico do projeto 

## `git log --pretty=oneline`
- Mostra os os commits de forma "bonitinha", em uma única linha 
  - Mostra apenas o texto do commit 

## `git log --abbrev-commit`
- Abrevia a mensagem de commit 
  - Exibe apenas os 7 primeiros caracteres das hashs dos commits 

## `git log --stat`
- Exibe algumas estatísticas do log 

## `git log -p`
- Exibe as alterações feitas nos arquivos 
  - `git log -p -3` exibe a quantidade de commits especificada por  
  parâmetro

## Combinando git logs 
- É possível combinar, por exemplo, o `--pretty=oneline` com o  
`abbrev-commit`:
  - `git log --pretty=oneline --abbrev-commit`
  - Exibe os commits em uma única linha, de forma abreviada 

## Arquivos do git directory modificados 
- Ao modificar um arquivo anteriormente commitado para o  
.git directory, essas alterações do arquivo voltam para o  
working directory, mas, como o arquivo foi adicionado anteriormente,  
o git sabe que ele foi adicionado ao .git directory 
- Cada alteração feita nesse tipo de arquivo move o arquivo de  
volta para o working directory 
- Se um `git status` for executado nesse momento, os arquivos  
modificados serão mostrados 

## `git diff` 
- diff: diferença de tudo o que foi feito no arquivo 
- Permite visualizar as modificações entre os arquivos que  
estão no working directory e no staging area, desde o último  
`git add`

## `git diff <file>` 
- Permite visualizar as alterações feitas apenas do arquivo  
especificado

## `git diff --staged`
- Mostra as alterações entre os arquivos de staging area e git  
directory
- Comumente usado após o git add 

## `git diff <hashCommit1 hashCommit2>`
- Exibe as alterações feitas entre commits
- É permitido colocar apenas os primeiros 7 caracteres da hash do commit 
- Para saber quais alterações foram feitas **desde o primeiro commit**  
até último, basta especificar o primeiro commit como parâmetro:  
`git diff hashPrimeiroCommit`
- Para **comparações entre 2 commits**, basta passar a hash do commit  
mais recente como primeiro parâmetro e a hash do mais antigo como  
segundo parâmetro 

## Cores e operadores nas linhas no git 
- \- e Vermelho: Linha removida 
- \+ e Verde: Linha adicionada 
  - Linhas que serão adicionadas no próximo `git add`
- Amarelo: arquivos que foram modificados e não foram adicionados  
à stagin area 
  - Indica que o momento atual é o working directory 

# Frequência entre commits
- A cada alteração pequena e simples, é necessário fazer um commit 
  - O recomendado é fazer um commit após uma pequena lógica  
  implementada, por exemplo
  - Isso permite voltar, facilmente, no tempo 
  - Permite a visualização do que foi feito de data x até data y
- A demora em fazer commits não é benéfica para o projeto
- É importante entender que commits marcam breakpoints 
  - Pontos específicos no tempo, no histórico, que é onde  
  é possível voltar 

# Utilização do Git em trabalhos diferentes de código 
- TCC
  - Em um TCC, em que várias alterações são requeridas,  
  é uma ótima ideia commitar as alterações 
    - Se algo que foi apagado precisa ser reescrito, por  
    exemplo, o que foi apagado estará no histórico do Git 
- Trabalhos acadêmicos 
- Imagens 
  - Neste caso, não é possível visualizar as alterações  
  diretamente, no terminal 
- **Qualquer coisa na vida que precise de um histórico**

# Removendo aquivos do working directory 
- Se simplesmente um arquivo do **diretório atual** (working  
directory) for deletado, ao rodar o git status, é exibido que  
o arquivo foi deletado 

# `git rm <file>`
- Remove o arquivo do `.git` directory 
- Após isso, um git status mostra que o arquivo foi removido e  
que há alterações que precisam ser commitadas 
  - Ou seja, o git add e o git status são utilizados para  
  adicionar ou remover aquivos da staging area 
  - Se deleted estiver verde e a menensagem "changes to be commited  
  é mostrada", significa que já posso commitar 
- A remoção do arquivo é adicionada, mas a ação que está sendo  
feita é a remoção de um arquivo 
- Mas, **o arquivo está no histórico**
  - Executando o comando `git log --name-status`
- Ao remover o arquivo apenas com o `rm nomeArquivo` e executar um  
`git status`, é mostrado que há mudanças que não estão no stage area,  
ou seja, não foram commitadas

# Encontrando um arquivo excluído
- É possível localizar, no histórico (`git log`), um commit que  
ainda possua o arquivo deletado, executar um `git diff` com a  
hash desse commit, e ver, em vermelho, as linhas do arquivo  
excluído 

# `git add --all` ou `git add -A`
- Faz com que todas as ações que foram feitas no working directory  
sejam adicionadas
  - Arquivos novos
  - Arquivos deletados
  - Arquivos modificados
- Evita o uso do `git add arquivo` pro arquivo modificado e `git rm`  
para os arquivos deletados 

# `git add -f nomeArquivo`
- Força o commit de um arquivo que esteja no `.gitignore`

# `.gitignore`
- Ignora alguns arquivos do repositório 
  - Arquivos que, mesmo sendo necessários no projeto,  
  não devem ser commitados, por exemplo
  - Estes arquivos devem ser adicionados ao `.gitignore`
    - `echo "node_modules" >> .gitignore`
- Deve estar na raiz do projeto 
- Arquivo conhecido, no mundo do Linux, como dot file 
  - Lembrando que, no Linux, todos os arquivos que  
  começam com `.` são ocultos
- Para adicionar múltiplos arquivos e pastas, basta inserir  
os nomes apenas com quebra de linhas 
- É importante que os arquivos não tenham sido adicionados  
à staging area antes de serem listados no `.gitignore`

Exemplo em arquivos node JS: 
- Para se trabalhar com o node, primeiramene é necessário um arquivo  
`package.json`
- Ao criar esse arquivo, e executar um `git status`, é mostrada uma  
mensagem dizendo que `package.json` não foi adicionado à staging area  
e não faz parte do `.git` directory (untracked file)
- Existem arquivos do node que precisam existir no projeto, mas não  
é necessário que eles sejam versionados 
- Se o Gulp é instalado localmente, por exemplo, com o comando  
`npm i --save-dev gulp`
  - Ele irá baixar o gulp, criar um diretório `node_modules` e, nesse  
  diretório, haverá o projeto do gulp disponível para ser utilizado no  
  meu projeto local 
  - O `package.json`, após um pacote do node ser instalado, o pacote  
  é adicionado automaticamente como dependência do projeto
    - Para instalar as dev dependencies do node, basta executar  
    `npm install` e ele irá instalar os pacotes que estão dentro  
    do `package.json`
    - Ou seja, geralmente, o node_modules não precisa ser versionado  
    no projeto. 
- Então, após a instalação, o git status mostra que `node_modules` e  
`package.json` são arquivos não-trackeados
- É possível remover, a `node_modules` e, tudo o que tiver como  
dependência de desenvolvimento dentro de `package.json` pode ser  
instalado novamente com o comando `npm install`
  - Ou seja, o projeto pode ter apenas o `package.json`. O  
  `node_modules` não é necessário 
    - `node_modules` possui muitos arquivos que irão deixar o projeto  
    grande 
- Sempre que esse projeto precisar ser baixado, basta executar o  
`npm install` e, automaticamente, o npm irá criar a `node_modules`  
já com as ferramentas que eu preciso, dentro dele 
- Porém, como o node_modules é necessário enquanto eu estiver  
desenvolvendo

# Arquivos ou diretórios commitados acidentalmente, antes de serem incluídos no `.gitignore`
- Um exemplo recorrente é o commit do `node_modules`
  - Se o arquivo que não era para ser commitado for incluído no  
  `.gitignore` após o commit e, o `git add` for executado novamente,  
  aparentemente está tudo ok. 
    - Ao instalar um outro módulo e executar `git log --name-status`,  
    é mostrado que o `node_modules` continua no `.git` repository 
    - É possível utilizar `rm -r node_modules` 
      - Ao executar o git status, é mostrado que `node_modules`  
      está sendo deletado
      - Agora, ao dar um `git add -A` e um git status, é mostrado  
      que `node_modules` foi deletado do `.git` directory 
      - Então, é possível commitar, passando a mensagem de que  
      `node_modules` foi removida 
      - Agora, caso um pacote seja instalado e a node_modules criada,  
      nada será adicionado ao `.git` directory, pois node_modules já  
      está no `.gitignore`
      - Se após os passos acima, o arquivo que estiver listado no  
      `.gitignore` não poderá mais ser adicionado com o `git add`, e  
      uma mensagem de erro será exibida 

# `git rm -rf nomeArquivo --cached` - Removendo um arquivo da staging area sem deletá-lo do working directory 
- Se a node_modules for commitada para a staging area, acidentalmente,  
é possível removê-la sem a necessidade de deleta-la do diretório atual  
(working directory)
  - Útil quando já houver vários módulos instalados 
- Após a execução do comando, o arquivo será removido do `.git` directory  
e será listado como untracked, no git status 

# Adicionando ao .gitignore arquivos que já estão na staging area 
1. Adicionar o nome do arquivo no `.gitignore`
2. Remover o arquivo da staging area
  - `git rm nomeDoArquivo --cached` ou, no caso de diretórios,  
  `git rm -rf nomeDoArquivo --cached`
    - --cached não deletará o arquivo ou diretório do working directory 
3. Ao dar um git status, é mostrado que o arquivo foi deletado 
  1. Um git diff --staged pode ser executado para confirmar 
  2. Agora o arquivo não é mais mostrado como untracked 

# `git commit -a -m "message..."` ou `git commit -am "message..."`, no Linux - Pulando a etapa de commitar um arquivo para a staging area 
- Caso o arquivo **alterado** já faça parte do .git directory,  
o comando fez o commit e a adição 
- É um comando perigoso. É recomendado, sempre, usar o  
`git add nomeArquivo` ou `git add .` e depois o `git commit -m "mensagem"`

# `~/.gitignore` - Utilizando o .gitignore na raiz de usuário 
- É possível colocar um arquivo .gitignore na pasta de usuário  
  - windows: (c/Users/roger)
  - unix:  
    - `touch ~/.gitignore` 
      - `~` representa a pasta de usuário
    - Incluir arquivos a serem ignorados
      - Ao dar um git status, o arquivo incluído no .gitignore  
      ainda é mostrado como untracked
    - Para funcionar, é necessário executar o comando abaixo 

# `git config --global core.excludesfile /cygdrive/c/Users/roger/.gitignore` - Configurando um `.gitignore` padrão para todos os projetos presentes na máquina 
- Na primeira vez que executado, não mostra nada, pois ainda não  
há excludes file nele
- Posso então configurar, no meu diretório de usuário, o  
core.excludesfile, passando como parâmetro o .gitignore de  
usuário: 
  - `git config --global core.excludesfile /cygdrive/c/Users/roger/.gitignore`
    - O core.excludesfile disse para que o git configurasse um  
    `.gitignore` padrão para todos os projetos instalados nessa  
    máquina
      - É possível portanto, ignorar o node_modules de todos  
      os projetos nesta máquina, sem a necessidade de ficar  
      adicionando ele no `.gitignore` de cada arquivo 
      - Ideal para arquivos específicos recorrentes 
    - Agora, ao dar um git status, os arquivos listados no  
    .gitignore da pasta de usuário fez com que esses arquivos  
    fossem ignorados no working directory

# Branches
- Ramificações do projeto
  - Cada ramificação é uma cópia do projeto 
- Servem para os casos em que é necessário criar, por exemplo,  
uma nova feature no projeto 
  - Exemplos: 
    - Adicionar CSS em um componente
  - Criam um ambiente separado do ambiente principal (master)
- Evitam que alterações sejam feitas na branch master, pois ela  
é a branch padrão do git, a branch que apresenta o ambiente  
final
- São criadas com base na branch atual 
  - A branch será criada com o mesmo conteúdo e histórico da  
  branch atual 
  - Os arquivos também serão "copiados" (na verdade, serão  
  referenciados)
- Tudo o que é alterado em uma branch, não afeta a outra, pois  
cada branch é um ambiente completamente separado 
- É importante não trabalhar na branch principal, mesmo ao  
trabalhar sozinho
  - Fazer com que cada branch seja uma feature a ser adicionada  
  no projeto 
  - A branch master deve conter apenas o conteúdo mais atualizado  
  possível
  - Possibilidades e recomendações: 
    - Criar uma branch 'dev', que será a branch padrão para  
    desenvolver e criar alterações no projeto. Essa branch, deve  
    ser tratada como a branch master de desenvolvimento. Tudo o  
    que é beta deve estar nela. 
      - Baseado na branch dev, é possível criar uma branch chamada  
      'js', por exemplo, onde serão feitas features em JavaScript 
      - Após codar a feature, dar um git commit 
        - Se for o momento, um git checkout pode ser executado  
        para a branch 'dev' e a branch js pode ser mergeada com  
        a branch dev
      - Ou seja, é possível editar os arquivos de javascript em  
      uma branch específica para eles. O mesmo acontece com o  
      html e css. 
    - O que deve ser mergeado para a master são apenas as  
    **coisas finais do projeto**. Ela será sempre a versão mais  
    estável do projeto. A versão final. 
      - Assim, se der algum problema ou qualquer tipo de erro, o  
      erro não ficará na master 

# `git branch`
- Lista as branches existentes no projeto 

# `git branch <branchName>`
- Cria uma nova branch, baseada na branch em que eu estava  
anteriormente
  - Os da logs da branch anterior permanecem na nova branch.  
  Os arqiuvos também são os mesmos. 
- Caso a branch já exista, uma mensagem de erro será exibida  
e a branch não será criada 

# `git checkout <branchName>`
- Troca de branch 

# `git checkout -b <branchName>`
- Atalho que cria e já acessa uma branch 
- `-b` = branch
- `checkout` = muda de branch 

# `git branch -m <newBranchName>`
- Renomeia uma branch 
- É necessário estar dentro da branch a ser renomeada 

# `git branch -D <branchName> <branchName2> <branchName3>` - Removendo / deletando branches 
- Remove uma ou múltiplas branches 
- Útil em casos onde é necessário apagar branches de features que  
já foram mergeadas na branch principal (dev)

# `git checkout --orphan <branchName>`
- Cria e troca para uma nova branch vazia 
- Útil em casos onde é necessária a criação de um histórico novo ou  
é desejável manter duas diferentes estruturas no projeto. Exemplo: 
  - Uma com o código do projeto em si 
  - Outra com os arquivos estáticos do site do projeto 
  - Como os dois casos acima fazem parte do mesmo projeto, não é  
  necessário criar um repositório separado para cada um 
- A branch não será baseada em alguma outra  
- O git log estará limpo, os arquivos saem do estado do git  
repository e vão para o staging area, como se tivessem acabado de  
terem sido adicionados com o git add 
  - Há a opção de reutilizar os arquivos (commitar) ou removê-los  
  com o `git rm -rf .`, para remover todos os arquivos da staging  
  area
  - Lembrando que a nova branch orfã nunca será mergeada com a branch  
  principal 

# `git merge <branchName>` - Unindo alterações entre branches diferentes 
- **Estando na branch master**, git merge recebe o nome da branch  
a ser unida à master 

# Criando repositórios 
- O conceito de ter repositórios é a possibilidade de centralizar  
os arquivos em um só lugar, para que outras pessoas também possam  
colaborar com o projeto 
- Possibilita que as alterações feitas sejam enviadas para um local  
onde haja um gerenciamento de todo o histórico dos commits do projeto 
  - O repositório possibilita que Designers, Front-end developers e  
  Back-end developers trabalhem no mesmo repositório
- Repositórios devem ter o mesmo nome do projeto, com `.git` no final
- Lembrando que, na maior parte dos casos, o repositório não será local,  
como neste exemplo didático, mas sim, no GitHub. 
  - Não faz sentido manter o projeto em um repositório local, ao  
  invés de hospedar no GitHub

# `git init --bare` 
- Cria um repositório no git, ao ser executado dentro diretório que será  
o repositório do projeto (exemplo abaixo, ao falar sobre `git clone`)
- Ao listar os arquivos e diretórios do repositório, é notável que ele  
não criou um diretório `.git`, pois na verdade, este repositório já é,  
teoricamente, um diretório `.git`
  - Ele cria, no repositório, basicamente a mesma estrutura de  
  diretórios de um diretório `.git`
- Este repositório `.git` nada mais é do que o próprio repositório do  
projeto, porém, de forma local
- Ao executar esse comando, o repositório `.git` criado é um caminho  
aonde é possivel enviar os arquivos do projeto e centralizá-los

# `git remote add <origin> <pathToRepositoryToInsertFiles>` - Adicionando um repositório ao projeto 
- Deve ser executado dentro do diretório do projeto 
  - Por convenção, o repositório do projeto é chamado de 'origin'
- Linka o repositório do projeto com o repositório `.git` do projeto  
(my-project.git)
- No repositório `.git`, ao executar o comando `pwd`, será retornado  
o caminho do repositório onde os arquivos devem ser inseridos 
# `git remote -v`

- Exibe os repositórios origin fetch e o origin push

# `git push <origin> <branch>` - Sincronizando o ambiente local com um repositório 
- `push`: empurrar
- `<branch>`:  nome da branch a ser sincronizada 
- Empurra para o origin o que está na branch (histórico)
  - Irá criar, no repositório, uma branch com o mesmo nome da branch  
  atual do projeto, ou, apenas sincronizar a branch, caso ela já  
  exista no repositório 

Exemplo: 

- `git push origin master`
  - Empurra para a branch master do origin (my-project.git), tudo o  
  que está na branch de trabalho atual
  - Todas as branches podem ser enviadas para o repositório origin 

# [`git clone <repositoryName>` - Clonando um repositório existente](#git-clone)
- Clonar um repositório é uma das vantagens em manter um repositório  
onde outras pessoas possam acessá-lo
- Exemplo: 
  - Tenho uma pasta chamada time. Dentro dela, outras pastas de cada  
  membro do time + a pasta 'servidor', onde irá ficar o repositório  
  `.git` do projeto 
  - Dentro da pasta 'servidor', posso criar um repositório  
  `ecommerce.git`, com o comando `mkdir ecommerce.git`
  - Dentro da pasta `ecommerce.git`, posso executar o comando  
  `git init --bare`
  - A partir de agora, `ecommerce.git` será o repositório principal,  
  onde as coisas do projeto serão compartilhadas 
  - Posso então sair da pasta deste repositório (`ecommerce.git`) e  
  voltar 2 níveis, para acessar a pasta 'time' e então, acessar a  
  minha pasta 'roger'
  - Dentro da minha pasta, que representa meu computador local, posso  
  criar o diretório principal do ecommerce e começar a trabalhar nele.  
  Existem duas formas de se criar este repositório: 
    - Executar o `mkdir ecommerce`, acessá-lo e, dentro dele, iniciar  
    um repositório `.git` com o comando `git init`
    - Agora, é só linkar o meu repositorio `ecommerce` com o  
    repositório que está no servidor. 
    - Posso então executar um `pwd` dentro do repositório do servidor,  
    para copiar o caminho dele. 
    - Agora, basta estar dentro desse meu repositório `ecommerce` e  
    executar o comando `git remote add origin <caminhoDoRepoDoServidor>`
    - Feito isso, ao executar o comando `git remote -v`, é mostrado o  
    caminho do repo do servidor, que é listado como 'origin'
  - Para clonar este repositório no computador de outros membros do  
  time, basta dar um `pwd` na pasta `ecommerce.git`, copiar o caminho  
  e, dentro da pasta da 'ana', por exemplo, executar um  
  `git clone caminhoDoEcommerce.git` e o repositório será clonado  
  dentro de um diretório `ecommerce`, dentro da pasta da ana
    - Feito isso, ao executar o comando `git remote -v`, dentro do  
    diretório `ecommerce` é mostrado o caminho do repo do servidor,  
    que é listado como 'origin'
  - Agora, os dois membros do time, Roger e Ana, podem fazer alterações,  
  trabalhando no mesmo projeto e fazendo push no repositório principal,  
  que é o repositório do servidor (`ecommerce.git`)
    - Agora, qualquer alteração feita no repositório 'roger' não  
    irá refletir, obviamente, no repositório da ana 
  - Agora, se roger faz uma alteração e dá um push pro repositório  
  remoto `ecommerce.git` e ana altera um arquivo e faz um push  
  também, ana visualizará a mensagem dizendo que o push dela foi  
  rejeitado, pois o repositório local dela não está atualizado 
    - Não é possível enviar uma alteração para o repo remoto sem  
    pegar o arquivo atualizado 

# `git pull <origin> <branch>` - Puxando dados de um repositório remoto 
- Puxar
- Garante que eu esteja com a última versão atualizada do projeto 
- Após puxar os arquivos atualizados do repositório remoto, é possível  
então dar um push com as alterações locais feitas 
- **Ao trabalhar em equipe, antes de alterar qualquer arquivo e dar um push para o servidor ou repo remoto, sempre executar em meu computador, ou pasta local, o comando `git pull origin master`, para que as alterações sejam baixadas para meu repositório local**
  - Isso garante que, antes de começar a trabalhar, os arquivos  
  estarão atualizados 

# Controle de versão distribuído 
- Ao contrário de um controle de versão centralizado, o repositório  
principal não fica bloqueado quando alguém está fazendo alterações  
em um arquivo 
- Permite trabalhar de forma descentralizada. Apenas o repo principal  
será um lugar centralizado 
- É possível que duas ou mais pessoas editem os mesmos arquivos, pois  
o git irá trabalhar com o sistema de auto merge dele 

# Nunca faça commits direto na branch master 
- Usar uma branch por feature 

# Melhorando o histórico de commits 

# `git commit -m "..." --amend`
- **Usar apenas em commits que não foram pusheados para o repo principal**
- Usar apenas em casos onde seria ideal que um detalhe que foi  
utilizado no último commit **sem push** fosse inserido no commit  
- Em casos onde a última alteração feita no arquivo poderia  
ser commitada junto com o commit mais recente (exemplo:  
ajustou o título da página, commitou e depois apenas reindentou  
um bloco de código), é possível: 
  - copiar a hash do último commit
  - dar um git add no arquivo alterado 
  - executar um git commit e, após a mensagem do commit, utilizar  
  o parâmetro `--amend`
    - `git commit -m "Ajusta título a página e indentação" --amend`
- Ao utilizar este comando, o último commit é sobrescrito
- Evita sujar o histórico com um commit de algo que não é  
significativo e não precisava estar ali 
- Requer muito cuidado caso o push para o repositório principal  
já tenha sido executado 
  - Se o amend for utilizado para um commit já existente no repo  
  principal, haverá um conflito no commit e será gerado um tipo  
  de problema que terá que ser resolvido manualmente  

# Como funciona o automerge do Git 
- O automerge entre o mesmo arquivo em diferentes branches funciona  
apenas para linhas de código distantes umas das outras 
- O problema não é trabalhar no mesmo arquivo em que a outra pessoa está  
trabalhando, mas sim, em **linhas de código próximas umas das outras** ou  
na mesma linha 
- Digamos que meu arquivo `style.css` seja alterado, adicionado  
com o `git add .` e commitado, na branch 'dev'
- Feito isso, irei para a branch master. Na branch master, as  
alterações feitas no arquivo, na branch 'dev', não foram  
refletidas na branch atual (master)
- Irei, à partir da branch master, criar e acessar uma nova  
branch chamada 'altera-cor-texto' e fazer uma outra alteração  
no mesmo arquivo css 
- Após alterar, irei dar um `git add .` e um `git commit -m "..."`  
- Ou seja, agora, o mesmo arquivo css tem uma alteração na branch  
'dev' (tamanho do texto) e outra alteração na branch  
'altera-cor-texto' (cor do texto)
- Na branch 'dev' o texto está com 18px e na branch  
'altera-cor-texto' o texto ainda com 14px
- Se, na branch 'dev', for executado um `git merge altera-cor-do-texto`,  
será exibida uma mensagem de conflito no arquivo `style.css`
- Se um `git status` for executado após isso, será exibida uma  
mensagem dizendo que um arquivo foi modificado por duas branches  
- Ao executar um `git diff`, é mostrado que a branch HEAD (atual)  
possui linhas de código diferentes em relação à branch  
'altera-cor-texto' (imagem abaixo)

![diff](https://user-images.githubusercontent.com/29297788/44011809-257ef8e4-9e91-11e8-83be-c2b46d66da8a.jpg)

- Neste caso, como é um código pequeno, é possível acessr o arquivo,  
deixar apenas o código correto e fazer o commit normalmente 

# Resolvendo problemas de conflito 
- Primeira solução: **abortar o merge**, com o comando  
`git merge --abort`, após a exibição do conflito, o git  
irá tentar abortar o merge feito. 
  - Após isso, ao executar um `git status`, é exibido que  
  o working directory está limpo e o arquivo está com as  
  alterações anteriores 
- Próxima solução: analisar o código que possui os sinais  
de '+' (imagem abaixo) em relação ao que possui os sinais  
de '-' e identificar o que foi alterado 

![diff-2](https://user-images.githubusercontent.com/29297788/44011980-60c6f194-9e92-11e8-8a04-ca70f86f6014.jpg)

- Então, neste caso, como é um código pequeno, basta ir no  
arquivo css, copiar a alteração de cor da branch  
'altera-cor-texto', colá-la no código da branch atual,   
remover o código da branch 'altera-cor-texto' e remover os  
códigos `<<<<<HEAD` e `>>>>> branchname` que o conflito  
gerou no arquivo
- Agora, ao dar um `git diff`, a atualização do código é  
mostrada
- Então, posso adicionar e commitar o arquivo, com uma mensagem  
especificando que o conflito de cor foi resolvido 
- Agora, ao dar um `git status`, é exibido que a branch já  
está funcionando normalmente 
- Então, agora é possível acessar a branch master e mergear  
a branch 'dev' nela, com o `git merge dev`

Outro tipo de problema: 
- Faço uma alteração no `<title>` de um arquivo html, na branch principal
- Adiciono e commito a alteração, dou checkout para a branch 'dev'
- Na branch 'dev', faço uma alteração no mesmo arquivo html,  
em outra parte dele (adiciono a tag footer)
- Adiciono e commito a alteração 
- Faço o merge da branch master na branch 'dev'
- **Agora o git conseguiu fazer o automerge**
  - Ou seja, tenho as duas alterações feitas no arquivo

# Configurando a merge tool 
- O Git, por padrão, possui uma ferramenta para automatizar a resolução  
de conflitos 

# `git config --global merge.tool meld`
- Ao executar o comando `git config -l`, é exibida a possibilidade de  
configuração da merge tool: `merge.tool=vim`
- Para alterar a ferramenta de vim para meld, é necessário executar o  
comando `git config --global merge.tool meld`
- Após isso, ao executar um `git config --list`, é exibido que agora  
a merge tool é o meld: `merge.tool=meld`
- Após isso, é necessário, no Windows, seguis os passos abaixo: 
  - After [installing it](http://meldmerge.org/)
  - I had to tell git where it was:
  - git config --global merge.tool meld
  - git config --global diff.tool meld
  - git config --global mergetool.meld.path "C:\Program Files (x86)\Meld\meld\meld.exe"
  - And that seems to work. Both merging and diffing with "git difftool"  
  or "git mergetool"
- Agora, ao dar conflito de arquivo, basta executar o comando  
`git mergetool`
  - Será exibido o arquivo em que o merge está sendo feito e uma  
  mensagem de aguardo da confirmação para o uso do meld 
  - Após isso, uma interface será aberta 
    - Janela 1: 
      - Alterações feitas no meu repo local
    - Janela 2: 
      - Como o arquivo irá ficar 
    - Janela 3: 
      - O arquivo remoto (a outra branch que foi mergeada)
    - Para selecionar quais alterações devem permanecer, basta clicar  
    nas setas das janela 1 ou 2
    - Ao terminar, é só salvar e fechar 
    - É importante perceber que ele cria alguns arquivos temporários,  
    que ficam no meu repo local do projeto 
    - Ao dar um `git status`, são exibidas as modificações do arquivo 
    - Para ignorar os arquivos que o meld criou, como eles ainda não  
    estão adicionados na staging area, basta adicioná-los no `.gitignore`
      - `echo "*.orig" >> .gitignore` inclui, no .gitignore, todos os  
      arquivos `.orig` gerados pelo meld 

# `git checkout <file>` - Voltando alterações não commitadas
- Ao alterar um arquivo, se ele não tiver sido adicionado à staging area  
com o `git add`, basta executar este comando e as  
**alterações feitas no commit anterior estarão de volta** 

# `git diff -w` Visualizando alterações ignorando espaços em branco 
- Na branch master, faço uma alteração no title do index.html e  
dou um tab à mais nas tags internas do body 
- Ao executar um git diff, são exibidas as alterações do título e  
dos espaços adicionados 
  - Só que **alterações de espaçamento, geralmente, não são importantes**,  
  para a visualização  
- Este comando mostra o que foi alterado no arquivo, ignorando  
qualquer alteração que tenha apenas espaçamento adicionado 

# `git checkout <commit>` - Voltando no tempo 
- Ao executar um `git log --oneline`, são mostrados todos os commits  
da branch
- Se eu quiser voltar em algum deles, basta executar o `git checkout <commit>`,  
passando por parâmetro o número do commit 
- Ao voltar, se o `git log --oneline` for executado, apenas os commits  
feitos até aquele ponto serão visualizados 
- **Os commits anteriores não foram perdidos**
  - Ao dar um `git checkout master`, o projeto volta para a  
  posição onde ele estava (presente)
- É possível fazer alterações em um commit passado e manter essas  
alterações. Basta criar uma nova branch 
  - É como se essa nova branch fosse baseada à partir desse commit  
  do passado
    - `git checkout -b voltando-no-tempo`
  - Depois de criar essa nova branch, é possível fazer as alterações  
  necessárias nela e depois mergear essa branch com a master: 
    - `git checkout master`
    - `git merge voltando-no-tempo`
  - Assim, é possível pegar alterações feitas naquele arquivo e jogá-las  
  para a master 
  - Ou fazer coisas que ficaram para trás, foram apagadas mas é necessário  
  voltar nessas implementações 
  - Esse é um dos exemplos de como mensagens legíveis de commit podem ser  
  cruciais para o projeto 
  - E importante também que cada commit possua apenas uma implementação 

# `git checkout <branch> -b <new_branch>` - Mudando de branch e já criando uma nova 
- Apenas o `git checkout <branch>` irá mudar de branch 
- Este comando dá um checkout para a branch `<branch>` e já cria  
outra branch baseada nela 
- `<branch>` é a branch em que a nova branch criada será baseada 
- É interessante também em casos onde é necessário voltar no log 
  - Ao invés de passar apenas `git checkout <hash>`, é possível  
  concatenar o `-b <new_branch>`
  - Ou seja, já vai criar uma branch baseada em um commit do passado 

# `git stash` - Deixando o trabalho menos urgente para depois 
- Mantém alterações não comitadas em uma lista para que estas  
alterações sejam acessadas novamente depois 
- Salva o working directory em um estado 
- Ao executar um git status, é exibido que o working directory  
está limpo 
  - As alterações não comitadas desaparecem dos arquivos,  
  **mas não foram perdidas**
- Ideal para features que estão em desenvolvimento, não devem ser  
commitadas, mas é necessário salvar as alterações feitas para  
mudar para uma outra entrega mais urgente 
- **Não deixar muitos stashes**

## `git stash list` - Visualizar uma lista de stashes 
- Exibe um work in progress com a branch da feature que estava  
sendo desenvolvida no momento em que o `git stash` foi executado 
- O stash 0 é sempre o mais recente 
- Se neste momento uma alteração for feita 

## `git stash apply` - Voltar para o último stash 
- Volta as alterações feitas até o momento do `git stash`
- Após terminar o job mais urgente, voltar para a branch da  
feature menos urgente, que estava sendo desenvolvida, e executar  
este comando 
- Aplica sempre o stash mais recente 

## `git stash drop stash@{<stashNumber>}` - Remover / deletar um stash da lista

## `git stash pop` - Aplicar e já remover o último stash 

# `git log --pretty=format:"%h - %an, %ar : %s"` - Logs personalizados
- Ideal para alias no bash 
- Exibe o log com o seguinte formato: 
  - hash abreviada do commit (`%h`)
  - Espaços e traço (` - `)
  - Nome do autor do commit (`%an` - author name)
  - Há quanto tempo foi feito o commit (`%ar`)
  - Título do commit (`%s`)

- Tabela de possíveis logs personalizados:  

![tabela-logs](https://user-images.githubusercontent.com/29297788/44376289-2ffb0b80-a4ce-11e8-82b4-d84066014834.png)
![tabela-logs-02](https://user-images.githubusercontent.com/29297788/44376338-6fc1f300-a4ce-11e8-8f7a-19c02b094685.png)

# Conhecendo o [GitHub](https://github.com/)
- O papel do GitHub é substituir o repositório local do projeto (que  
pode estar um servidor, por exemplo)

# Criando um repo no GitHub
- A maneira ideal é iniciar um novo repositório dentro do GitHub 

# Subindo arquivos para um repo do github 
- Copiar a url do repo no github 
- Acessar diretório do projeto local, dentro da pasta do usuário 
- Dar um `git remote -v` e conferir se o origin já está configurado 
- O origin será alterado para apontar para o github 
  - Para que quando o push for feito, ao invés de enviar para o repo  
  local, os arquivos sejam enviados para o github 

# `git remote set-url <origin> <url>` - Alterando a url de `origin`
- Requisitos: 
  - [Estes passos](#git-clone)
- Estrutura: 
  - `git remote set-url origin https://github.com/Roger-Melo/anotacoes-git`
  - Verificar se foi modificado, com o `git remote -v`
