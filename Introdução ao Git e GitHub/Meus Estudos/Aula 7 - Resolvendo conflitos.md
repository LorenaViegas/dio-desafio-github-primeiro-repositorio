*Resolvendo conflitos*



**COMO OS CONFLITOS ACONTECEM NO GITHUB E COMO RESOLVÊ-LOS**

Conflitos são comuns quando estou usando um sistema de versionamento de código, e vai acontecer várias vezes ao longo da minha carreira.

Não é um bicho de sete cabeças.

Tenho que saber:

\1.  O que são;

\2.  Como encontra-los;

\3.  Como ocorrem;

\4.  Fazer exercício prático para resolve-los.

Ex. de como os conflitos acontecem.

Quando tenho meu código no GitHub e baixo para minha máquina, ou acabei de enviar para lá, o código que está no repositório remoto é o mesmo que está no meu repositório local. As versões são correspondentes.

​                                

Se uma pessoa vai no meu Git hub e faz um clone dele, transfere para o repositório local dela, está pegando para fazer uma contribuição, ela também tem a mesma versão que eu e o GitHub.

  

Nesse momento, ninguém mexeu no código ainda e os três estão sincronizados, o repositório remoto, o meu repositório local e o repositório local dela.

  

= Sistema de versionamento de código distribuído, ou seja, todo mundo pode ter acesso, baixar para seu repositório local e fazer alterações concomitantemente

Em seguida abrimos os arquivos para começar a editar.

 

Não é possível duas pessoas fazerem a mesma edição ao mesmo tempo, no mesmo lugar. Sempre vai ter alguma mudança, por menor que seja, uma vírgula, um espaço, etc.

  

Ambas abrem o mesmo arquivo e fazem alteração nele. Agora não estamos mais em sincronia, pois as três versões são diferentes. 

O que complica ainda mais é quando as mudanças ocorrem na mesma linha, é aqui que ocorre o problema.

A pessoa continuou e empurrou o código que estava trabalhando para o GitHub novamente.

Eu continuei editando, trabalhando naquele mesmo arquivo.

 

Agora, o código que está no GitHub é o código que estava na maquina do contribuinte. E o meu código está desatualizado. O código que está no GitHub é diferente do código que está na minha máquina.

Quando empurro meu código para o GitHub ele vai identificar isso, vai identificar que meu commit está com data diferente, então a minha versão é mais antiga.

 

 

O GitHub vai me falar que antes de empurrar o código para ele, tenho que puxar a versão que já está lá, que outra pessoa fez alteração e enviou, e é o código que está armazenado lá, fazer comparação entre os dois arquivos para identificar qual o conflito, fazer as alterações necessárias, juntar o que trabalhei com o que a pessoa trabalhou, e só após isso vou poder empurrar os arquivos sincronizados para lá, porque ai sim o código que está na minha máquina vai representar a versão mais recente do código, das mudanças que ocorreram.

 

É nesse momento que ocorre o conflito de merge, quando o GitHub tenta juntar duas alterações de código que estão na mesma linha. O GitHub não vai inferir nada, não vai fazer alteração drástica nisso. Ele vai pedir que eu abra o arquivo na qual ocorreu edição na mesma linha, que eu resolva o conflito e envie o código para o GitHub. Eu que tenho que resolver o conflito e dizer para o GitHub qual é de fato a versão, ai sim o código pode ir para o GitHub e representar o estado mais atualizado do meu repositório.

 

 

**Na prática:**

Vou para o Git Bash e vou fazer uma alteração no README.md.

Vou adicionar mais uma receita, vou sair e voltar no terminal.

 

Executo git status e identifico que o arquivo README.md foi modificado.

 

Quer dizer que ele sofreu modificação, e ainda não está na área de Staging, então tenho que adiciona-lo primeiro para depois gerar o commit.

 

git add * - com asterisco adiciona tudo.

 

Agora indica que tem mudanças para serem comitadas, o arquivo README.md foi adicionado ao Staged.

Agora vou comitar esse arquivo.

 

Sem problemas.

Agora faço o git push, que é empurrar o arquivo da minha máquina para o GitHub

 

Pede a senha.

 

Ao tentar fazer essa ação, o GitHub tenta integrar os dois arquivos automaticamente, mas quando ele identifica que a duas alterações estão na mesma linha, ele não consegue fazer, e passa o bo pra mim. Não vai deletar código, não vai fazer nada.

Deu essa mensagem estranha. Indica que foi rejeitado. 

‘Falha ao enviar algumas referências para o repositório no GitHub’. As mudanças foram rejeitadas porque o repositório remoto contém algum trabalho que eu não tenho localmente. O Git explica o que está acontecendo.

Significa que o ultimo commit do GitHub tem uma data e um conteúdo diferente do meu, então significa que não está igual. 

Tenho que primeiro integra-los para depois empurrar novamente.

Tenho que puxar esse arquivo modificado para minha máquina.

O comando é git pull + apelido do link + master.

 

Puxou o commit e indica que tem um conflito de merge no arquivo README, porque alguém foi lá e fez uma alteração que não existia no meu repositório de trabalho quando eu fazia as minhas alterações.

O Git pede abrir a versão e resolver o conflito.

 

Abrindo o arquivo no Typora. Pegar o conteúdo e colocar no bloco de notas, para visualizar melhor.

 

No bloco de notas fica desconfigurado.

A parte (<<<<< HEAD) identifica a alteração mais recente que tenho, que no caso é a minha.

 

E da linha ==== para baixo é a alteração que está no GitHub.

O símbolo maior que (>) é usado no markdown para escrever comentários.

Logo, vou ter que modificar para dizer qual dos dois é o correto.

 

Deletar o desnecessário e integrar as alterações no bloco de notas, logo, copiar e colocar no Typora, para deixar a formatação correta.

 

Salvo e volto no Git.

 

Executo git status e indica que tenho 2 arquivos, ambos modificados. Ou seja, ainda tenho conflito, porque na versão que puxei tinha um arquivo editado, na versão que fiz, também tinha modificação.

Já resolvi o conflito, já abri e disse qual versão vai ficar.

É assim que resolvo o merge conflict: manualmente, abro os dois arquivos conflitados, vejo onde está as alterações, qual versão é importante, quais as alterações que vão permanecer, e commito o arquivo novamente.

 

git add * para adicionar o arquivo ao Staged.

git commit para comitar o arquivo.

 

Com o git push empurro a versão atual para o repositório remoto no GitHub.

 

 

 

Ficou assim no GitHub.

 

 

Histórico de commits, aqui está a edição do conflito.

 

 

 

Aqui estão os conflitos.

Foi um exemplo simples, mas no contexto de programação no dia-a-dia gera muito mais trabalho.

Qualquer modificação, por menor que seja, pode causar efeitos indesejados, logo, tenho que olhar manualmente.

 

**Como baixar código do GitHub para meu repositório local:**

 

 

 

Aqui é um repositório famoso do Pyton.

 

 

 

Nessa parte tem algumas opções, posso abrir das seguintes formas:

\1.  Codespaces – funcionalidade nova do GitHub;

\2.  GitHub desktop – a versão gráfica do GitHub para mexer com o Git;

\3.  Download zip;

\4.  Link HTTPS – clonar pelo terminal no Desktop.

 

 

 

Selecionar o link, copiar e colar no terminal do Git.

 

 

Fui para meu repositório base, que é workspace. 

Para clonar o repositório do GitHub na minha máquina o comando é git clone + url que copiei na plataforma.

Download terminado.

 

O que difere esse repositório de uma pasta comum? Quando clono ele vem de fábrica como um repositório de fato, não apenas uma pasta simples.

Significa que dentro do repositório cpython/ tem uma pasta .git/ que contém todo o versionamento de código e contém para onde o repositório está apontado.

 

O comando ls mostra todas essas pastas, mas não mostra as ocultas. Para mostrar as ocultas, e o .git/ é uma delas, o comando é ls -a

 

De fato tem a pasta .git/, significa que essa não é uma pasta comum, mas sim um repositório.

 

Comando git remote -v traz os repositórios remotos que esse repositório que acabei de baixar está apontando.

Se eu fizer alterações aqui, esse repositório já sabe para onde ele está apontado.

 

**A partir desse momento tenho que ser capaz de:**

\1.  Iniciar um repositório Git, entendendo todas as complexidades que isso envolve;

\2.  Entender os objetos que estão por traz do Git, mesmo que superficialmente;

\3.  Entender o conceito de versionamento de código, que é usado quando dou git init;

\4.  Entender a diferença entre Git e GitHub;

\5.  Saber como versionar o código;

\6.  Saber como usar os comandos básicos do dia-a-dia;

\7.  Saber os comandos de baixar e empurrar o código para o repositório remoto.

Dessa forma, tenho proficiência mínima para poder trabalhar e começar a versionar meu código.