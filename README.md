# [cygwin](http://www.cygwin.com/)
- Terminal que utiliza, no Windows, comandos básicos do Linux, bash  
do Unix 
- [Básico sobre o cygwin](https://youtu.be/TFCCriN_MvU?t=11m40s)

# Comandos terminal Linux 
- `pwd` print working directory 
- `cd /` change directory to root 
- `ls` lista as pastas do diretório atual 
  - `-la` parâmetro que lista os arquivos e pastas do diretório  
  atual, inclusive os ocultos. Nos sistemas Unix, todo diretório  
  que começa com `.` não é mostrado 
- `cd cygdrive` entra no root do windows 
  - `ls` lista os discos rígidos do windows 
- `clear` limpa o terminal 
- `mkdir` cria um diretório no diretório atual 
- `touch nomeArquivo.extensao` cria um arquivo

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

# Comandos do Git 
- `git --version` mostra a versão do Git instalada 
- `git` mostra alguns comandos de ajuda 
- `git init` inicia um repositório do git 
  - Cria um diretório `.git` oculto no diretório atual 
  - Esse diretório permite a inicialização e criação de históricos de  
  alterações dos arquivos
- `git status` mostra o status da árvore atual do git
  - Pode ser utilizado a qualquer momento 
  - Mensagens
    - "Changes not staged for commit" indica que um arquivo já  
    adicionado à staging area anteriormente foi modificado. Ou seja,  
    o arquivo já faz parte do repositório .git, mas possui alterações 
    - "Changes to be committed:" indica que desta vez, há alterações  
    a serem commitadas

# Estágios do Git 
- Estágios são, basicamente, 3 momentos do projeto 

![estagios-git](https://user-images.githubusercontent.com/29297788/43348687-b9edea20-91d1-11e8-843d-16369b268a44.jpg)

1. Working Directory
- É o diretório atual em que se está trabalhando 
- A primeira etapa a ser feita é passar o arquivo deste estágio para  
o estágio 2 (Staging Area)
2. Staging Area
- Entra-se nesse momento à partir do momento em que se adiciona um  
arquivo ao repositório do Git, fazendo com que o arquivo faça parte  
da árvore do git 
3. .git directory (Repository)

## `git add <file>` 
- Passa um arquivo do Working Directory para o Staging Area 
- Após executado, é exibida uma mensagem 'changes to be commited',  
ou seja, a mensagem já não é de untracked files como anteriormente 
- Ou seja, agora o arquivo foi adicionado na staging area, mas  
ainda não faz parte do .git directory (repositório)

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
repositório .git 
- Mostra uma hash que representa o commit feito, o nome e  
e-mail de quem fez o commit, a data e horário e a mensagem  

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
- Permite visualizar as modificações feitas nos arquivos 
do commit 

## Cores e operadores nas linhas no git 
- \- e Vermelho: Linha removida 
- \+ e Verde: Linha adicionada 
  - Linhas que serão adicionadas no próximo `git add`
- Amarelo: arquivos que foram modificados e não foram adicionados  
à stagin area 
  - Indica que o momento atual é o working directory 
