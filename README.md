# Regras para edição deste arquivo:

Este é um projeto colaborativo. Isso quer dizer que outras pessoas vão mexer no arquivo, editando o que você escreveu, ampliando ou mesmo apagando. A vida é assim, e é assim que os grandes projetos open souce funcionam.
Para facilitar a vida de todos algumas regras simples, que se forem seguidas tornam tudo mais fácil para todos:

   1. Não se preocupe com a formatação do texto por enquanto. Ela é importante, mas não definimos como fazer ainda. Se quiser usar formatação use-a, mas preocupe-se em manter algo que fique claro para todos (por exemplo usar fonte courier para exemplos ou tabulações).
   2. Evite simplesmente apagar o que outra pessoa escreveu. Em outros projetos deste tipo que participei usávamos o recurso de tachado no texto, comentários entre colchetes e novo texto na frente. Isso funcionou muito bem, e gostaria de usar aqui. Portanto se você não gostar de algo que eu escreví simplesmente coloque um tachado [menu format, strikethrough] e a correção na frente.
   3. Para sugerir tópicos simplesmente adicione ao indice, na próxima página. Cada tópico teóricamente será um capítulo, então para o digitar adicione uma quebra de linha, defina o título como heading1 e meta bronca.
   4. Para chamar atenção use cores de fundo ao invés de fontes grandes. 

Acho que é isso. Adicione seu nome na lista de colaboradores a seguir e mãos a obra.


# Colaboradores: (em ordem alfabética)

    * Bruno Barros (bkether@gmail.com)
    * Emerson Vinicius (duke.m16@gmail.com)
    * Fernando Ribeiro (ferbass@gmail.com)
    * Guilherme Ceolin (guiceolin@gmail.com)
    * Lucas Catón (lucacaton@gmail.com)
    * Luciano Sousa (ls@lucianosousa.net)
    * Marcelo Fontes Castellani (marcelo@mindaslab.com)
    * Roberta Soares (robs.soares@gmail.com)
    * Rodolfo Luiz (rodolfols@gmail.com)

# Tópicos que serão abordados

	1. O que é o Git e para que serve;
	2. Instalando e configurando o Git (OSX, Linux e Windows).
	3. Criação de um repositório local, adição de arquivos e primeiro commit;
	4. Adicionando um repositório remoto e enviando as coisas para lá;
	5. Usando o git no dia a dia


## Tópicos futuros

	6. Git GUI tools
		6.1. Linux
			6.1.1. gitg
			6.1.2. gitk
		6.2. OSX
		6.3. Windows
	7. Como colaborar em um projeto open source com o git;
	8. Github
	9. Arquivo de configuração (~/.gitconfig)

Criação de um repositório local, adição de arquivos e primeiro commit

Vamos começar da maneira mais simples possível, criar uma aplicação Rails e a adicionar a um repositório Git. Para isso abra o terminal e crie um projeto Rails:

>$ rails git_na_pratica
create  
create  app/controllers
create  app/helpers
create  app/models
[......]
create  doc/README_FOR_APP
create  log/server.log
create  log/production.log
create  log/development.log
create  log/test.log

Entre no diretório do projeto e inicie o repositório com o comando git init:

>$ cd git_na_pratica/
$ git init
Initialized empty Git repository in /home/desenvolvimento/git_na_pratica/.git/

Você pode encontrar um diretório .git agora dentro de seu diretório. É nesse diretório que o Git guarda todas as informações, diferente do SVN e do CVS, que criam uma pasta para cada pasta de seu projeto.

>$ ls -al
total 72
drwxr-xr-x 14 castellani castellani  4096 2010-07-27 10:01 .
drwxr-xr-x 15 castellani castellani  4096 2010-07-27 10:00 ..
drwxr-xr-x  6 castellani castellani  4096 2010-07-27 10:00 app
drwxr-xr-x  5 castellani castellani  4096 2010-07-27 10:00 config
drwxr-xr-x  2 castellani castellani  4096 2010-07-27 10:00 db
drwxr-xr-x  2 castellani castellani  4096 2010-07-27 10:00 doc
drwxr-xr-x  7 castellani castellani  4096 2010-07-27 10:01 .git
drwxr-xr-x  3 castellani castellani  4096 2010-07-27 10:00 lib
drwxr-xr-x  2 castellani castellani  4096 2010-07-27 10:00 log
drwxr-xr-x  5 castellani castellani  4096 2010-07-27 10:00 public
-rw-r--r--  1 castellani castellani   307 2010-07-27 10:00 Rakefile
-rw-r--r--  1 castellani castellani 10011 2010-07-27 10:00 README
drwxr-xr-x  3 castellani castellani  4096 2010-07-27 10:00 script
drwxr-xr-x  7 castellani castellani  4096 2010-07-27 10:00 test
drwxr-xr-x  6 castellani castellani  4096 2010-07-27 10:00 tmp
drwxr-xr-x  3 castellani castellani  4096 2010-07-27 10:00 vendor

Vamos agora realizar o primeiro commit de nosso projeto. Para começar vamos adicionar todos os arquivos da pasta com o comando git add . (ou git add --all). Esse comando informa ao git que desejamos adicionar ao controle de versão todos os arquivos e diretórios da pasta onde estamos, recursivamente.

>$ git add .

Depois vamos realizar o primeiro commit utilizando o comando git commit -a -m "Primeiro Commit". A opção -a (ou --all)indica que o commit será para todos os arquivos modificados, renomeados ou apagados. Para arquivos novos você deve obrigatóriamente usar o git add antes do git commit. Já a opção -m informa a mensagem de commit.

Ao invés de git commit -a -m "Primeiro Commit" também é possível usar git commit -am "Primeiro Commit".

>$ git commit -am "Primeiro Commit"
[master (root-commit) 6316e12] Primeiro Commit
42 files changed, 8461 insertions(+), 0 deletions(-)
create mode 100644 README
create mode 100644 Rakefile
create mode 100644 app/controllers/application_controller.rb
create mode 100644 app/helpers/application_helper.rb
create mode 100644 config/boot.rb
create mode 100644 config/database.yml
[......]
create mode 100644 test/performance/browsing_test.rb
create mode 100644 test/test_helper.rb

Para ver o seu commit use git log. Você verá uma listagem com a mensagem de commit, o autor e outros dados.

>$ git log
commit 6316e121fa36b01bb17e437b5a596bf53d1fbe3c
Author: Marcelo Castellani <castellani@castellani-desktop.(none)>
Date:   Tue Jul 27 10:11:16 2010 -0300

   Primeiro Commit

Outro comando muito útil é o git status, que mostra quais arquivos foram modificados e em qual branch estamos trabalhando. Vamos falar sobre branchs mais a frente, não se preocupe com isso agora.

>$ git status
># On branch master
nothing to commit (working directory clean)

Adicionando um repositório remoto e enviando as coisas para lá
Para criar um repositório remoto precisamos seguir os seguintes passos:

   1. Criando repositório e iniciando o repositório

    * Abra o Terminal
    * Acesse seu servidor via ssh (ssh usuario@servidor.com)
    * Crie um diretório no local desejado com a extensão .git (mkdir projeto.git)
    * Entre no diretório criado (cd projeto.git)
    * Inicie o repositório com o comando git --bare init

## Usando o git no dia a dia

No dia o git é uma ferramenta super pratica para se usar, normalmente no processo de versionamento do codigo ira usar comandos como add, rm, commit, e push

###git add
Como é de se imaginar, esse comando adiciona os arquivos em um repositório temporário para em breve ser comitado

###git rm

git commit -m “descrição do commit”

git commit -am “descrição do commit”
