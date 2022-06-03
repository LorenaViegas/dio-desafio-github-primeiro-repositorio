*Introdução ao GitHub*

**TRABALHANDO COM GITHUB**

Saber como mover o meu repositório local para o ambiente remoto (GitHub).

Criar um repositório remoto, apontar meu código que está na minha máquina, no meu repositório local para o repositório remoto.

Saber qual comando especifico que uso para empurrar o código do meu repositório local para o repositório remoto, e fazer com que ele apareça no GitHub para que todos os desenvolvedores que tiverem acesso à plataforma possam olhar meu código e colaborar com ele.

 

Criar a conta no GitHub.

 

É interessante que minhas configurações no Git de user name e user email para criação de commits sejam as mesmas configuraçoes para autenticação no GitHub, porque quando faço os commits no meu repositório local, o Git vai atrelar meus dados, que são os que citei na configuração, automaticamente ao repositório no GitHub.

Facilita também em alguns processos específicos que vou fazer na plataforma do GitHub, quando eu criar commits na plataforma, ex.: 

\1.  corrigir merge,

\2.  fazer alteração em commit próprio, 

\3.  aceitar correções de alguém no meu commit dentro da própria plataforma. 

Em todos esses casos vou realizar commits na plataforma.

Não é obrigatório configurar os mesmos dados, mas facilita o processo, pois se eu estiver com configurações diferentes, vou usar credenciais diferentes e não acontece a vinculação automática.

Então o ideal é que as configurações sejam iguais.

Para saber quais as configurações de user name e user email que coloquei no Git, o comando é:

git config --list

O GitHub é:

\1.  um repositório remoto onde armazeno meu código em nuvem;

\2.  possibilidade de trabalhar em equipe no mesmo código;

\3.  possibilidade de disponibilizar meu código para que outras pessoas tenham acesso e possam contribuir;

\4.  várias funcionalidades;

\5.  loja de aplicações que posso integrar no meu fluxo;

\6.  rede social – posso seguir as pessoas, ver quais códigos e projetos estão engajadas.

\7.  Etc.

Com a conta criada sou redirecionada para esta página.

 

​                               

 

Ir para meu perfil

 

 

 

Posso pinar alguns repositórios.

 

 

 

Quadro de contribuições, repositórios que contribui.

 

 

 

Readme do meu próprio perfil, posso colocar informações complementares sobre mim.

Para criar repositórios, é o seguinte caminho:

Repositórios > New > Criar nome > criar descrição.

 

 

 

 

Posso deixar meu perfil público ou privado.

O check box de readme significa um arquivo que conta a história e funcionalidade do repositório.

Um GitHub quando encontra um arquivo markdown automaticamente ele formata e expõe para o usuário que vê o repositório esse arquivo.

Quando o GitHub encontrar uma pasta markedown ele vai fazer o mesmo.

Por convenção os arquivos que contam a história e funcionalidade do repositório são chamados READMES.

Nesse caso vou deixar desmarcado porque já criei um arquivo README no código armazenado no meu repositório local.

Com o repositório criado, o GitHub já sugere o que tenho que fazer.

 

 

É um repositório vazio e tenho que ir lá no meu repositório local e apontar o repositório local para o repositório do GitHub.

O endereço é uma URL:

 

 

Copiar esse caminho e levar para o repositório local, para minha pasta livro-receitas.

Se o repositório estiver visível (público) outras pessoas vão poder ter acesso a ele.

 

​                               

 

Tem um conjunto de funcionalidades do GitHub para tornar a colaboração mais agradável e eficiente.

 

 

 

Aqui ele já trouxe o README. Ele sempre vai procurar por um arquivo markdown em uma pasta externa, no caso ele encontrou esse arquivo, por convenção, nomeado README. Então a pessoa que acessar o repositório vai ver de cara o que escrevi no README. É por isso usei markdown, porque é a extensão de arquivo que utilizo aqui no GitHub.

Trouxe o titulo, a capa com os emoticons, e tem a pasta receitas com outro arquivo markdown, e vai estar formatado assim como no Typora.

 

 

 

Esse número é o início do sha1. Clicando nele consigo ver o histórico do commit, mais detalhes sobre ele, o dia que foi comitado, o autor, quantas mudanças, o que foi alterado. Então o GitHub traz a plataforma visual para ver o que estou realmente alterando no meu código.

 

 

 

 

Aqui tem os dados do commit.

O número identificador do commit e o parente que ele aponta. Posso clicar nele e ver o commit que está linkado, que é o commit anterior, logo, posso ver o histórico de commit dessa forma. Consigo ver isso no Git também.

 

 

 

Clicando em 3 commits também consigo ver o histórico de commits.

 

 

Me mostra quando eu fiz e a mensagem do commit. Clicando no sha do commit, consigo ver o conteúdo do commit, ou seja, o conteúdo craqueado pelas blobs, onde estão os arquivos e estão sendo alterados.

Isso vai montando a stack da branch.

 

Quando tenho um user name e use email diferentes configurado no ambiente de desenvolvimento do que tenho no GitHub:

 

 

 

Tenta buscar um usuário correspondente dentro do GitHub e não vai achar, então não vai conseguir linkar nenhum perfil, não mostra foto etc.

 

Posso também criar arquivos dentro do repositório na própria plataforma, e o GitHub faz isso respeitando as regras do Git, então cria commit para aquele arquivo também. Logo gero um commit na plataforma, que não existe ainda na minha máquina, e preciso sincronizar isso, tem comando especifico.

Os commits que faço na plataforma têm as credenciais do GitHub, e os commits que faço no meu repositório local também são linkados na plataforma do GitHub, mas os dados pessoais tem que ser os mesmos.