*Navegação via command line interface e instalação*

 

**COMANDOS BÁSICOS PARA UM BOM DESEMPENHO NO TERMINAL**

A maioria dos sistemas operacionais tem programas que possuem interface gráfica, ou seja, a forma como o usuário interage com os programas é de forma gráfica, pode clicar, arrastar, tudo é responsivo, a interface responde ao comando do usuário, sejam eles, clicar, usar atalhos do teclado etc.

O Git é um software que foi criado de forma diferente. O design é voltado para outro tipo de programa, ele é um CLI (*Command-Line Interface), não é GUI (*Graphic User Interface), ou seja, a forma de interação é por linhas de comando, não tem uma interface gráfica.

Hoje em dia temos programas que automatizam isso e acrescentam uma interface gráfica ao Git, tornando-o mais simples.

Mas aqui vamos interagir com a linha de comando, bem raiz, para entender conceitos chave, e estabelecer um conhecimento profundo.

Interagir com o Git da forma que ele foi criado para trabalhar.

**Alguns comandos importantes para poder navegar:**

​                               

Comandos básicos para que posso me situar e navegar usando o CLI, e interagir com o Git da maneira que consiga aprender os conceito de forma correta.

Os comandos em sistema operacional Windows (derivado do Shell) e Unix (derivados do Bash, Linux ou Apple) são diferentes.

 

 

Para abrir o terminal Git:

Area de trabalho > Botão Windows > digitar cnd (prompt de comando) > abre o terminal do Windows na pasta padrão, dentro do Diretório C:\Users\ e o nome do usuário.

 

O Windows 10 é um sistema Linux rodando dentro do Windows, então consegue rodar comandos de navegação em ambos.

**Comandos de navegação:**

Comando para listar – poder me situar dentro do sistema operacional e entender em qual local estou.

Comando dir + enter

Traz uma lista de diretórios contidos na pasta na qual estou situada, que é C:\Users\Lorena

 

No Linux o comando é ls + enter

Todos os comandos possuem variâncias, ou seja, flags, que são complementos que passo para os comandos, que complementam, modificam ou formatam a forma como os comandos são devolvidos para mim.

Como que eu subo ou desço o nível nesses diretórios?

Como vou para uma pasta específica dentro do sistema operacional?

Comando “change directory” = cd. Me possibilita navegar entre as pastas e é igual para todos os sistemas operacionais.

Comando cd + espaço + / + enter

 

A barra é um caminho específico.

Nesse comando ele me leva para a base do diretório “C:\>”

 

E no comando dir + enter lista todas as pastas dentro desse diretório.

 

No Linux o comando cd + / + enter é o mesmo.

Para entrar numa pasta no Windows o comando é:

cd + espaço + Windows 



 

Entrei na pasta Windows.

Usando o comando dir + enter o programa me mostra todas as pastas, arquivos e programas contidos na pasta Windows.

Para voltar, fazer o caminho inverso, uso o comando cd + .. (dois pontos) retrocede um nível.

No Linux é o mesmo comando.

Quando a tela fica muito poluída e quero limpar, interagir com o terminal mais limpo, há os seguintes comandos:

No Windows:

Comando cls + enter

= clear screem

 

No linux:

Commando clear + enter

Ou atalho ctrl + l



 

No Windows o atalho não funciona.

 

Outro atalho: a tecla de tab (espaço) tem a função de autocompletar, se reconhecer que na pasta tem aquele nome, autocompleta pra mim, o que facilita com nomes grandes e complexos de arquivos e evita erros humanos.

 

Comando para criar uma pasta é mkdir + nome da pasta

 

Esse resultado indica que a criação da parta deu certo, pois nada aconteceu. Conceito importante no Git: silence for success, se der tudo certo o terminal não vai falar nada.

Comando dir + enter

 

Vai me listar os diretórios contidos, e no final tem a pasta chamada workspace.

No Linux o comando é o mesmo, mkdir + nome da pasta que quero criar.

Usar o cd para navegar para essa pasta recém criada:

Comando cd + espaço + workspace

 

Então estou dentro da pasta.

Linux mesmo comando.

Criar alguns arquivos dentro dessa pasta para entender a diferença entre deletar arquivos e deletar repositórios.

Posso navegar na interface gráfica do Windows e fazer essa mesma atividade. Mas para fazer aqui no terminal:

Comando echo + nome + > + nome do arquivo.extensão

 

O símbolo > é um redirecionador de fluxo, ele pega o output da função echo e joga em um arquivo.

O sistema checa se já tem essa pasta, caso não, ele cria.

Se não traz resposta deu certo.

Usando o comando dir + enter consigo ver o arquivo contido da pasta workspace.

 

Para sair da pasta workspace uso:

Comando cd + ..

Volto para a pasta “C:\

 

Comando dir + enter

 

Novamente lista os diretórios presentes nessa pasta.

Para excluir um arquivo:

Comando del + espaço + workspace

 

O programa pergunta se tenho certeza que quero deletar tudo que está na pasta workspace. Escrevo S

 

Em teoria deletou, se não retornou com nada.

 

Listo as pastas, e o workspace está lá ainda.

No Windows tem uma diferença entre deletar arquivos e deletar repositórios.

O comando del se restringe apenas a deletar arquivos, e workspace é um diretório. Ou seja, esse comando deletou os arquivos dentro de workspace, não tem mais nada lá, mas não deletou a pasta.

 

Não é exatamente o que eu queria, quero deletar o repositório e todo o conteúdo dela.

Para isso:

Usando a seta para cima no terminal, consigo ver o histórico de comandos que utilizei até aqui, procuro o comando que usei para criar o arquivo hello.txt dentro da pasta workspace.

 

E novamente crio o arquivo.

Saio da pasta e listo novamente.

 

Para deleter o reposito com todos os arquivos que estão lá dentro.

Comando mkdir + espaço + nome do diretório

rmdir = remove directory

esse comando é para deletar uma pasta vazia.

Para deletar uma pasta com arquivos:

Comando rmdir + espaço + nome do diretório + espaço + /S + espaço + /Q

São duas flags.

 

Listo o conteúdo da pasta, e workspace foi deletada.

 

 

**REALIZANDO A INSTALAÇÃO DO GIT**

A instalação é diferente para diferentes sistemas operacionais: Windows, Linux e MacOS.

Site oficial do Git.

www.git-scm.com