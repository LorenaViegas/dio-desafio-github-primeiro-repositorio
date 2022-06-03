*Entendendo como o Git funciona por debaixo dos panos*

 

**TÓPICOS FUNDAMENTAIS PARA ENTENDER O FUNCIONAMENTO DO GIT**

Como o Git funciona por traz da tela?

Conceitos fundamentais da tecnologia Git.

Saber o que está acontecendo por debaixo dos panos quando executar meus comandos no programa.

Entendendo a tecnologia em geral, é importante para entender realmente o que estou fazendo, sem aprofundar muito.

4 tópicos:

​                               

Objetos fundamentais que rodam por debaixo do pano que constituem o sistema.

O que é o sistema distribuído?

Porque o Git é tão seguro e as pessoas o usam tanto?

O que é o SHA1:

 

O SHA1 é uma chave de encriptação, um algoritmo que pega o arquivo, seja foto, imagem, frase etc. e embaralha de forma muito especifica. Isso é importante para sabermos se o arquivo foi modificado por alguém sem autorização, por exemplo.

 

Esse conjunto de caracteres é único, serve como identificação. 

Se tenho um arquivo muito grande e quero saber se ele foi modificado por alguém, sejam coisas simples ou complexas, aplico o algoritmo sha1, gera um conjunto de 40 caracteres, específicos, que é uma encriptação para aquele arquivo, e comparo esse conjunto de caracteres com o que eu tenho do documento original, comparando. Fica mais fácil comparar assim do que o documento inteiro. Se houve a modificação, o conjunto de caracteres será diferente. 

Mas, se eu desfizer essa mudança, ex. se a modificação foi um ponto, e colocar novamente o ponto no lugar de alteração, o algoritmo sha1 será exatamente o mesmo que o primeiro. 

O Git faz uso dessa encriptação para identificar os arquivos de forma segura e rápida.

 

Representar o estado de um arquivo. Sempre que rodo o algoritmo no arquivo, pode trazer uma chave diferente, se o arquivo foi modificado.  

Comando echo + “string” | openssl sha1

Me mostra o algoritmo de 40 caracteres.

echo – mostra a string novamente no terminal

Jogo a string “ola mundo” para dentro de um algoritmo de encriptação com o openssl sha1, estou especificando que quero usar sha1.

É muito relevante.

Tenho que ser capaz de olhar para essa estrutura e saber o que aconteceu por debaixo dos panos, o que aconteceu com os objetos do Git, mais para frente vou saber.

 

PRÁTICA

Abro o Git Bash

 

Ele vai abrir na pasta do Git, por padrão.

 

Passar esse arquivo por um algoritmo de encriptação.

Essa encriptação pode ser usada para objetos internos do Git também.

 

**OBJETOS INTERNOS DO GIT**

 

Esses são os 3 tipos básicos de objeto do Git responsáveis pelo versionamento do código.

Entender as funcionalidades básicas desses objetos para exemplificar de forma clara o porquê de o Git ser um sistema distribuído e seguro.

 

**Blobs**

 

O comando echo pega uma string e mostra o output dessa string, e passo esse output (conteúdo) para uma função do Git.

É a função git hash-object + flag stdin (pois essa função espera receber um arquivo, mas estou enviando texto, e é só para que essa função entenda isso).

Se passo essa string ‘conteúdo’ para essa função do Git ela devolve o sha1 dessa string ‘conteúdo’ (conjunto de caracteres identificador).

Se fizer a mesma coisa, mas usando comando openssl sha1 gera outro tipo de sha1. Isso acontece porque a forma como o Git manipula é através de objetos, os arquivos ficam guardados dentro desse objeto blob, e ele contém metadados.

 

O objeto blob tem os seguintes metadados:

\1.  tipo – que é o blob; 

\2.  tamanho – da string ou arquivo, que nesse caso é 42; 

\3.  barra contrária + 0 = \0; 

\4.  conteúdo – de fato do arquivo, seja texto, binário, etc. Nesse exemplo é um texto “Ola Mundo”.

Essa é a estrutura básica de uma blob (bolha).

 

Para ter o mesmo sha1 em ambos os casos, basta que eu use o openssl sha1 + metadados entre aspas simples: 

tipo, tamanho, \0, string 

=

‘blob 9\0conteudo’

Assim gera o mesmo sha1.

Nesse exemplo o comando é: 

echo -e ‘blob 9\0conteudo’ | openssl sha1

 

Isso tudo significa que: a partir do momento que sei o que o sha1 faz, entendo que o Git vai guardar os arquivos, gerando um sha e também vai armazenar metadados nesses objetos. Logo, consigo entender a função dos objetos. 

Ou seja, o objeto blob guarda metadados, que são: tipo do objeto, tamanho, string etc.

 

**Trees**

 

As trees (árvores) são o segundo objeto, elas apontam para os blobs e também armazenam metadados.

É uma crescente, a blob é o bloco básico de composição, a tree armazena e aponta para tipos de blobs diferentes, e os commits, que tem a função de juntar tudo e dar significado a essa cadeia, aponta para as trees.

A tree também contém metadados: 

\1.  tipo; 

\2.  tamanho;

\3.  \0; 

\4.  aponta para um blob (que por sua vez tem um sha1); 

\5.  guarda o nome do arquivo (diferente do blob que não guarda nome do arquivo, somente o sha1 do arquivo – caractere identificador). 

\6.  gera um sha1.

A tree é responsável por montar toda a estrutura de onde está localizado o arquivo.

A tree pode apontar para blobs (que são “arquivos”) ou para outras trees (pastas). Isso acontece porque os diretórios dentro do sistema operacional podem conter outros diretórios, então faz sentido que o Git use um objeto recursivo*, que são as trees, ou seja, uma tree apontar para outra tree, assim como um diretório pode conter outro diretório.

\* É a possibilidade de uma função fazer uma chamada a ela mesma. Em um procedimento ou função **recursiva**, a função chama explicitamente ela mesma passando os parâmetros necessários para a sua execução.

 

É dessa forma que as trees funcionam.

As trees também tem um sha1 desses metadados.

Então as blobs (bolhas) têm um sha1 do arquivo, as trees apontam para as blobs e têm um sha1 dos metadados das trees. Se mudar alguma coisa na cadeia dessa tree, ao gerar o sha1 ele vai ser diferente.

Uma coisa sempre está relacionada com a outra, se mudar uma vírgula no arquivo, muda toda a encriptação da estrutura.

 

Estrutura das trees.

Temos as trees, que retém informações de arquivos que está apontando, ou seja, nesse exemplo é o README, Rakefile e o lib.

Ela aponta para blobs e aponta também para outra tree, que por conseguinte aponta para uma blob.

A tree é um objeto que encapsula esse comportamento de diretórios e é usada para apontar para diretórios que contém arquivos, e, por conseguinte, para outros arquivos.

 

**Commit**

 

Commit (compromisso) é o objeto mais importante de todos, pois junta tudo e dá sentido para as alterações que estou fazendo no código, ao longo do tempo.

O commit aponta para as trees e contém:

\1.  tipo – que é commit;

\2.  a tree que aponta;

\3.  tamanho;

\4.  um parente – é o último commit realizado antes dele;

\5.  um autor – quem é o dono dessa cadeia, o usuário responsável por criar essa cadeia, que no caso vai aparecer meus dados, user name e user email;

\6.  uma mensagem – que explica a cadeia, explica o motivo de criar aquele commit e para que ele serviu. 

O autor e a mensagem fazem parte do sentido que o commit gera. Os arquivos (representados pelos blobs) dentro das pastas (trees) significam uma cadeia, posso escrever uma mensagem dentro do commit que vai explicar, dar significado para esse monte de arquivo dentro de um monte de pasta.

\7.  o timestamp – é o carimbo de tempo, hora e dia exata de quando foi criado.

\8.  o sha1 do próprio commit – uma encriptação dos metadados que ele armazena.

Significa que se alterar um dado dentro de uma blob, gera um sha1 daquela blob, essa blob por sua vez está dentro de uma tree, que também tem os metadados alterados e assim por diante.

O commit aponta para tree. Se mudar qualquer coisa no arquivo, reflete na blob, que reflete na tree que reflete no commit.

Isso tudo garante a segurança das informações do código. Por isso o Git é tão confiável.

O commit garante que ninguém alterou o código, olhando o histórico dele, e que se tiver alterado, consigo saber quem foi, quando foi e o quê foi.

Monta uma linha do tempo, pois o commit aponta para parentes, que são as alterações realizadas antes dele.

É uma forma segura de demonstrar que aquele commit representa exatamente o que quero dizer com o código, que não teve interferência de outras pessoas.

Não tem como uma pessoa agir maliciosamente tentando alterar o código de um respectivo commit ou arquivo, sem que isso fique muito claro dentro do histórico do commit, pois uma vez que altera um arquivo altera toda a estrutura do commit.

Por isso é único para cada autor.

 

Aqui temos blobs, que são arquivos e contém o sha1 desses arquivos, temos a tree que aponta para os blobs com sha1 e armazena o nome dos arquivos, e temos o commit dando significância para esse conjunto de alterações que fazemos no arquivo, que por sua vez aponta para a tree e aponta para blobs.

O commit tem autor e metadados.

 

Conclusão: o Git é um sistema distribuído seguro porque:

Ex. tenho meu código/repositório Git hosteado em um servidor na nuvem, como ex. o GitHub. Tenho o código que vive lá, ele representa o estado final do meu código, é a versão mais atualizada. Esse repositório tem 40 pessoas contribuindo com ele. Na máquina dessas 40 pessoas, que são maintainers, pessoas que mantêm esse código de forma regular, está uma versão desse código. Então pelo fato dos commits serem tão difíceis de serem alterados, tanto a versão mais recente que está na máquina do servidor, como a versão dessas 40 pessoas, são versões confiáveis. Se der um problema na nuvem do GitHub, ex. bomba nuclear, perder todos os dados e o código não existir mais, para perder o repositório do código tem que acontecer algo com essas 40 pessoas também, porque as versões que elas mantêm são confiáveis, pela estrutura que o Git foi projetado.

Por isso é seguro e é um sistema distribuído. 

 

 

**CHAVE SSH E TOKEN**

Atualmente para acessar, usar e armazenar meus códigos no GitHub não basta mais só usuário e senha para autenticação. Preciso criar uma chave SSH ou um token.

O GitHub é uma plataforma em nuvem que vai guardar meu código e o manter seguro.

Tenho que me autenticar, dizer que sou eu.

Tenho que ter meu usuário e senha, além da chave SSH ou token.

Como criar uma chave SSH e token, pois são mais seguros e tem um processo para cria-los.

Chave SSH é uma forma de estabelecer conexão segura e encriptada entre duas máquinas.

Vou me conectar com o servidor do GitHub e vou configurar a minha máquina local como uma máquina confiável para o GitHub, estabelecendo essa conexão com 2 chaves, uma pública e uma privada. Vou pegar a minha chave pública e colocar no GitHub. A partir desse momento o GitHub vai conhecer minha máquina, então todos os repositórios que tiver na minha máquina vou enviar direto para meu repositório no GitHub por esse processo SSH, e enviar código direto para lá, o GitHub vai conhecer a assinatura da minha máquina, já vai ter uma conexão pré-configurada para isso, e vou ser capaz de enviar códigos sem precisar colocar senha.

A chave SSH fica no seguinte caminho:

Clicar no perfil > settings > SSH and GPG Keys.

Faço esse processo no CLI do GitBash e [neste link]([https://docs.GitHub.com/en/authentication/connecting-to-GitHub-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)) tem o passo a passo.

**Token de acesso pessoal**

É a segunda forma de autenticação segura que o GitHub me proporciona. O processo para gerar também é pelo domínio do GitHub.

Gero o token, guardo e sempre que for fazer algo no GitHub uso ele como senha.

É útil quando eu trabalho em uma máquina que não é confiável.

A diferença para a chave SSH é que o token eu tenho sempre que digitar na página quando for utilizar o GitHub, ele não autentica minha máquina automaticamente. Coloco meu usuário normalmente, e na senha coloco o token.

O caminho para gerar é:

Clicar no perfil > settings > developer settings > personal access tokens > generate new token.

Posso configurar data para expiração do token, marco a opção repo se só mexer nas opções padrão do GitHub.
