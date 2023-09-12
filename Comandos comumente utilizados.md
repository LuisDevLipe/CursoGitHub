# Uso do Init.
Para iniciar um projeto com GIT, abriremos o terminal, e iremos para o diretório de trabalho, ou seja, onde temos nosso projeto e, a partir daí, executaremos o comando:
- `git init`.
Este comando só é executado uma vez, no início de nosso projeto ou quando queremos que o GIT comece a acompanhar nosso projeto.
# Uso do Add.
Para cada mudança que fazemos no repositório local, nós iremos realizar um "commit" das nossas mudanças. Para realizar esta etapa por sua parte, devemos antes adcionar os arquivos que forem modificados a área de "staging".
Para fazer isso podemos utilizar o comando:
- `git add .`.
Este irá adcionar todos os arquivos modificado à área de "staging".
- `git add <nome_do_arquivo>`.
Este irá adcionar somente os arquivos escolhidos.
# Uso do Commit.
Para fazer uma captura do estado atual da área de staging, executaremos o comando de "commit".
Devemos também acrescentar uma descrição para o "commit" vamos utilizar a flag ``-m`` seguido da descrição entre aspas duplas.

- ``git commit -m "Descrição da versão" ``

Agora temos uma "imagem" do do projeto, ou seja, uma cópia do nosso código desde o último commit até o momento atual.
Se quisermos adcionar todos os arquivos a staging area e realizar um "commit", podemos utilizar o comando:
- `git commit -am "Descrição do commit"`
# Uso do Status.
Utilizando o comando:
- ``git status -s``.
Esta será a pasta que o GIT utilizará para criar áreas locais de staging do repositório.

# Uso do log.
Para obter uma lista de todas as cópias que temos no repositório local, usaremos o comando:
- ``git log -online``

# Uso do Reset.
Se quisermos restaurar o arquivo para uma versão anterior que tínhamos, ou seja, restaurar o arquivo, deveríamos usar o comando:

- ``git reset --hard 09f1c5``
Como podemos ver, temos que passar o código alfanumérico do commit que queremos recuperar.
Deve-se notar que, tendo voltado para um commit anterior que tivemos, as próximas versões que foram criadas após esse momento não existirão mais. Em outras palavras, podemos voltar a uma versão anterior, mas uma vez que fazemos isso, perdemos todas as versões após essa versão.

# Uso de Push.
O comando "push" é usado para enviar conteúdo do repositório local para o remoto.
Sintaxe: git push <remote> <branch>
- `git push`
Enviar o branch especificado juntamente com todos os commits e objetos locais necessários.
Git não permitirá que os commits sejam feitos se o repositório remoto conter outros commits que possam gerar conflitos com um arquivo existente.

- `git push <remote> --force`
É o mesmo comando que o anterior, mas obriga o envio mesmo que o resultado gere possíveis conflitos.
# Não devemos usar --force a menos que estejamos absolutamente cientes e seguros do que estamos fazendo.
Git nos impede de sobrescrever o histórico de commits remotos, recusando-se a realizar um push quando haja diferença de commits na hora da fusão. Portanto, se a história remota for diferente de nossa história, teremos que sicronizar o repositório local com o repositório e depois realizar os commits e por fim `git push`.
- a tag `--force` anula este comportamento e faz com que o repositório remoto coincida com o local, removendo assim todas as mudanças no repositório remoto que ocorreram desde o último commit.

# Devemos ter absoluta de que nenhum colega de equipe incorporou mudanças no repositório antes de usar a tag `--force` 

- `git push <remote> --all` 
Envia todos os commits locais para o repositório remoto especificado.

## Uso do Pull
Este é um dos quatro comandos que solicitam interação em red por GIT. Por padrão, o "git pull" faz duas coisas:
- Ele atualiza o branch de trabalho atual.
- Ele atualiza as referências dos repositórios remotos;
_git pull_ recupera (*git fetch*) os novos commits e une-os (*git merge*) em seu repositório local.

## A sintaxe para este comando é a seguinte.
- `git pull opções repositório refspec`
Onde:
    - Opções sãos as opções de comando,tais como: `--quiet` ou `--verbose`
    - Repositório é o URL do nosso repositório remoto.Exemplo: https://github.com/usuariox/repositorio.git
    - Refspec especifica quais referências a serem recuperadas e quais referências locais a serem atualizadas. Exemplo: _NomeRemoto_ é o nome do nosso repositório remoto. Ex: origin.
    _NomeBranch_ é o nome da nossa branch. Ex. develop.
### Se tivermos mudanças não "commitadas", a fusão falhará e nossa branch local permanecerá intacta.
Há algumas coisas a serem levaddas em conta para o git pull funcionar corretamente.
O repositório local tem um repositório remoto vinculado.
 - confirme isso executando `git remote -v`.
 - S houverem vários controles remotos. "git pull" pode não ser suficiente. Talvez precisaremos enviar o comando:
 - `git pull origin`
    ou
- `git pull upstream`
# Uso do fork
Serve basicamente para criar uma cópia de repositório remoto qualquer, para a nossa conta no GitHub.
Este repositório copiado será basicamente um clone do repositório no qual foi realizado o fork, mas a partir desse momento o fork viverá em um espaço diferente e será capaz de evoluir de maneira diferente.
# Uso do Clone
Existem diversas formas de obter uma cópia de um repositório remoto para podermos trabalhar nele localmente. Uma delas é utilizando o comando:
`git clone <URL do Repositório remoto>`
# Diferença entre o clone e o fork.
Se fizermos um clone normal de um repositório, o
espaço GitHub desse clone permanecerá associado
ao repositório que clonamos. Portanto, se fizermos
mudanças no clone e quisermos publicá-las no
GitHub, provavelmente não conseguiremos carregá-
las.
Obviamente, se clonarmos um repositório que fosse
nosso, podemos fazer mudanças localmente e
carregá-las para o GitHub sempre que quisermos.
Mas se o repositório pertencesse a outro
desenvolvedor e não tivéssemos permissões de
escrita sobre ele, então não seríamos capazes de
carregar as mudanças, porque o GitHub não nos
permitirá fazê-lo. É aqui que precisamos de um garfo.

# Uso de Branches (ramos)
Os ramos ou Branches são linhas do tempo que serão formadas por todos os "commits" que fizemos ao logo da evolução do nosso projeto.
## Criar uma Branch
Para criar uma branch, devemos usar o comando "branch" e especificar o nome que queremos atribuir à essa branch.Ex:
- `git branch developBranch`.
Criamos agora nossa branch. Se fizermos um `git log -online` para ver o status do nosso projeto.Podemos ver que já existe uma referência à nossa branch recém-criada.
Com o comando:
- `git branch`
Veremos os ramos do projeto e em que ramo estamos.
Para mudarmos de branch, utilizaremos o comando:
- `git checkout <nome_da_branch>`.
Ex: `git checkout developBranch`.
Podemos verificar se estamos atualmente na nova branch utilizando o comando citado anteriormente.
- `git branch`.
De agora em diante, quaisquer mudanças que eu fizer em meu código serão refletidas apenas no ramo (*branch*) recém-criado. Os arquivos no ramo principal permanecerão inalterados.
## Se tivermos que fazer mudanças no projeto, teríamos que executar um "add" e um "commit".
Como vimos anteriormente, podemos fazer as duas operações ao mesmo tempo com o comando:
- `git commit -am "Descrição do commit"`
Já temos agora uma primeira mudança feita no ramo que estamos trabalhando.
Mas o ramo mestre não vai refletir essas mudanças. De fato se mudássemos para o ramo (*branch*) principal não veríamos nenhuma mudança. Ou seja os commits ficam retidos somente dentro da branch que trabalhamos naquele momento do "commit".
### Eliminando uma branch.
Para eliminar uma branch utilizamos o comando:
- `git branch -d <nome_da_branch>`.
Ex: `git branch -d developBranch`.

# Uso do Merge
Com o comando de "merge", podemos juntar um ramo (*branch*) que criamos ao ramo mestre.
Em nosso projeto criamos o ramo "developBranch". Para juntar este ramo com o ramo mestre, devemos usar o comando "merge" junto com o nome que queremos fundir.
A primeira coisa a fazer é mudar para o ramo mestre, visto que, qualquer "merge" que quisermos fazer deve partir sempre do ramo "mestre".
Para realizar o merge utilizamos o seguinte comando:
- `git merge <branch>`
Ex: `git merge developBranch`
Nesse momento o GIT detectará possíveis conflitos. Caso exista mudanças em uma linha de código em ambos os ramos, antes de fazer a fusão o git perguntará o que fazer com as divergências. Depois de resolver as divergências por meio da nossa IDE. Teremos que salvar, fazer o "commit" e depois o "merge".