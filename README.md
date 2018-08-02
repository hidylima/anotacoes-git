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

# Estágios do Git 
- Estágios são, basicamente, 3 momentos do projeto 
![estagios-git](https://user-images.githubusercontent.com/29297788/43348687-b9edea20-91d1-11e8-843d-16369b268a44.jpg)


1. Working Directory
- É o diretório atual em que se está trabalhando 
- A primeira etapa a ser feita é passar o arquivo deste estágio para  
o estágio 2 (Staging Area)
2. Staging Area
- Momento em que os arquivos foram adicionados, onde o próximo passo é  
commitá-los (incluí-os) no `.git` directory 
3. .git directory (Repository)

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

## `git commit -m "Commit Message"`
- Passa o arquivo da staging area para o .git directory 
- Limpa o working directory 
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

## `git log --name-status`
- Exibe, o nome dos arquivos que foram alterados ou excluídos,  
além do hash do commit, autor, data e mensagem de commit 
  - A: add. Arquivos que foram adicionados 
  - M: modified. Arquivos que foram modificados 
  - D: deleted. Arquivos que foram deletados 

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
- Um exemplo recorrente é o commit do `node_modules`, por exemplo 
  - Se o arquivo que não era para ser commitado for incluído no  
  `.gitignore` após o commit, e, o `git add` for executado novamente,  
  aparentemente está tudo ok. 
    - Ao instalar um outro módulo e executar `git log --name-status`,  
    é mostrado que o `node_modules` continua no `.git` repository 
    - Utilizar `rm -r node_modules` também é uma tentativa 
      - Ao executar o git status, é mostrado que `node_modules`  
      está sendo deletada
      - Agora, ao dar um `git add -A` e um git status, é mostrado  
      que `node_modules` foi deletado do `.git` directory 