# [cygwin](http://www.cygwin.com/)
- Terminal que utiliza, no Windows, comandos básicos do Linux, bash  
do Unix 
- [Básico sobre o cygwin](https://youtu.be/TFCCriN_MvU?t=11m40s)

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

# `git branch -D <branchName> <branchName2> <branchName3>`
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

# `git clone <repositoryName>` - Clonando um repositório existente 
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