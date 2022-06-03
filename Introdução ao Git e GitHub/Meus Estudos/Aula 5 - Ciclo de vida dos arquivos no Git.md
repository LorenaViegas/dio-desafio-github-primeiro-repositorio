*Ciclo de vida dos arquivos no Git*

**PASSO A PASSO NO CICLO DE VIDA**

Estados dos arquivos, como o Git identifica que um arquivo foi alterado ou não, e como manipulo de forma mais completa os arquivos.

Entender o ciclo de vida dos arquivos dentro do Git.

Desde então vimos falando repositório e diretório de forma indiscriminada.

​                               

A terminologia correta.

Esse comando, além de criar uma pasta .git, ele inicializa um conceito de Git chamado repositório. Quando uso esse comando git init estou criando um repositório Git dentro daquela pasta.

 

 

\1.  Untracked – são os arquivos que o Git ainda não tem conhecimento, ou seja, o arquivo ainda não existe para o Git;

\2.  Tracked – arquivos que são rastreados de fato pelo Git, pode se subdividir em três:

2.1.    Unmodified – arquivo que ainda não foi modificado;

2.2.    Modified – arquivo que sofreu modificação, ex. arquivo de texto que modifico alguma coisa, muda automaticamente de Unmodified para Modified;

2.3.    Staged – ficam os arquivos que estão se preparando para fazer parte de outro tipo de agrupamento, que é o de um commit.

São 4 tipos de atividade que um arquivo pode sofrer no processo:

**1.**  **Adicionar o arquivo** – quando utilizei o comando git init criei o arquivo “Strogonoff.md” que estava **untracked**, ou seja, eu tinha acabado de criar ele no repositório que iniciei, mas o Git ainda não sabia da existência dele. Quando rodei o comando git add o Git moveu o arquivo direto para o **Staged**, e partir desse momento ele está aguardando para entrar no palco, ou seja, ser comitado.

**2.**  **Editar o arquivo** – Arquivos **unmodified** são arquivos que tenho dentro do meu repositório no git que ainda não sofreram modificação. Quando abro o arquivo e modifico alguma coisa, muda automaticamente para **modified**. O git vai comparar o sha1 dos arquivos e vai identificar que o arquivo tem modificação.

**3.**  **“Stage” o arquivo** – Arquivo **modified**, quando executo o git add nesse arquivo ele vai para **Staged**, e entra nessa área especial que está aguardando para entrar em ação, para executar uma ação, para fazer parte de outro grupo, que é o commit.

**4.**  **Remove o arquivo** – um arquivo **unmodified**, ou seja, não sofreu alteração nenhuma, removo o arquivo com o comando git ..., volta para **untracked**, o git não tem ciência dele ainda.

**5.**  **Commit** – quando movo o arquivo para o **staged**, ele está se preparando para fazer parte de um commit. O commit é um objeto chave do Git. Quando executo um commit no arquivo, ou seja, envelopo todas as modificações, com significância, escrevo mensagem, que carrega autor e data, integram de fato o objeto commit, deixa de ser staged e vira commit. O commit retorna esse arquivo para **unmodified** para provar que é a última alteração feita naquele código, e então inicia o ciclo novamente. Se eu fizer nova modificação no arquivo, tenho que executar novo commit para salvar a alteração. O git commit pega todos aqueles arquivos, tendo acabado as alterações nele, e cria um snapshot, uma foto do código naquele momento. Voltam para unmodified aguardando novas modificações, e assim por diante.

Unmodified, modified e staged formam um ciclo que fica rodando entre os 3.

**O que os repositórios significam:**

Quando rodo o git init crio um repositório.

 

No processo de criação de um código, tenho dois ambientes:

\1.  Servidor – que é o remote repository (repositório remoto), onde armazeno meu código em nuvem, na Internet.

\2.  Ambiente de desenvolvimento – representa tudo que está em minha máquina, subdivide em:

2.1.    Working Directory – diretório de trabalho, que é onde estou trabalhando, são os arquivos untracked, unmodified e modified, é o que estou manipulando agora, criei o Livro de Receitas.

2.2.    Staging Area – área de preparação, que é o staged, onde o arquivo chega depois de um git add e fica aguardando um git commit. 

Os arquivos ficam alternando entre o Working Directory e o Staging Area à medida que vou modificando esses arquivos.

2.3.    Local Repository – é o meu repositório local, onde armazeno meus commits. Quando executo um git commit de um arquivo que está no Staged ele passa a integrar meu repositório local, que por sua vez pode ser empurrado para o Remote Repository.

O Git é um sistema distribuído, ou seja, tem a versão no servidor, no caso o GitHub, e tem a versão que está em minha máquina. Então as alterações que faço na minha máquina não repercutem imediatamente na versão do repositório remoto. Para repercutir, tenho que executar um conjunto de comandos específicos, empurrar a alteração do meu repositório local para o remoto. 

 

Quando adiciono um arquivo que era Untracked, ou seja, o git ainda não tinha ciência dele, e dou um git add, o arquivo é movido para o Staged.

Quando tenho um arquivo Unmodified e dou um git add ele também é movido para Staged.

Os arquivos ficam transitando entre Working Directory e Staging Area.

 

O importante é que os arquivos também transitam entre Staging Area e Local Repository. 

Quando executo o commit movo o arquivo do Staging Area para Local Repository, ou seja, torna um arquivo unmodified, crio um snapshot, populo meu repositório local. Ele só vai ser composto por commits.

Tudo que está em meu repositório local tem que ser commit, senão não consigo enviar para meu repositório remoto.

O GitHub é meu repositório remoto.

É o que acontece por debaixo dos panos.

Os seguintes comandos:

\1.  git add nomeArquivo

\2.  git add *

\3.  git add .

estou movendo o arquivo untracked direto para staged e arquivo unmodified e modified para staged, e ficam esperando para serem comitados. 

\4.  git commit -m “mensagem” – peguei todos os arquivos que estavam na staging area, envelopei em uma mensagem, dando significância e criei o objeto do Git chamado commit.