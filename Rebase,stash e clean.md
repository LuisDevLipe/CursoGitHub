# Fusão de ramos (branches).
No Git há duas maneiras de juntar branches, " _git merge_ " e " _git rebase_ ". A maneira mais conhecida é a primeira, que realiza uma fusão de três vias entre os dois últimos "commits" de cada ramo e o ancestral comum a ambos, criando um novo "commit" com as mudanças fundidas.
O " _git rebase_ " basicamente faz é coletar uma a uma as mudanças em um ramo, e replicá-las em outro ramo. O uso do rebase pode nos ajudar a evitar conflitos desde que seja aplicado em cmomits locais e não tenha sido carregados em nenhum repositório remoto. Se não tivermos __cuidado__ com isto e um colega usar as mudanças afetadas, estamos fadados a ter problemas, já que tais conflitos são geralmente difíceis de reparar.
## Como regra geral este comando é usado para:
    - Editar commits anteriores.
    - Combinar vários commits em um só.
    -Remover ou reverter os commits que não são mais necessários.
# Uso do Rebase
"Rebase" é um processo de integração de um conjunto de "commits" sobre outro local base. Ele pega todos os "commits" de um ramo (*branch*) e os acrescenta aos "commits" de um novo ramo.
A sintaxe técnica do "Rebase" é a seguinte:
- `git rebase [-i --interactive] [opções][--exec cmd][--onto newbase | --Keep-base][upstream[branch]]`.
### Utilização
O principal objetivo do rebase é manter um histórico de projetos progrssivamente mais limpo e linear. O "Rebase" resulta em um histórico de prejeto perfeitamente linear que pode acompanhar o "commit" final até o incío do projeto sem ramificar-se. isto facilita a navegação no projeto. Usar o "Rebase" depois de enviar os commits para o repositório remoto é considerado uma má prática, porque mudar o seu histórico de "commits" pode tornar coisas difíceis para todos os outros que usar o repositório.

## Rebase contra um ramo (branch) a partir da master.
Para organizar todos os "commits" entre outras branch e o estado da branch atual, podemos entrar com o comando:
- `git rebase --interactive <nome_da_branch>`.
Ex: `git rebase -i developBranch`.

## Rebase dos últimos commits.
Para reorganizar os últimos "commits" em nosso ramo atual, podemos entrar com o seguinte comando:
- `git rebase -i HEAD~7`.

## Comandos disponíveis.
    - Pick : Significa que a descrição do commits está incluída.

    - Reword : Semelhante a _pick_, mas depois de usá-lo, o processo de "Rebase" para e lhe dá a oportunidade de modificar a descrição do "commit".

    - Edit : Teremos a oportunidade de modificar o "commit", podemos acrescentar ou alterar todo o "commit". Também podemos assumir mais commits antes de continuar com a reorganização. Nos permite dividir um grande "commit" em menores ou remover alterações errôneas feitas a um "commit".

    - Squash : Este comando permite juntas dois ou mais "commits" em um só. Um "commit" é combinado com o "commit" acima dele. GIT nos dá a oportunidade de escrever uma nova mensagem de "commit" descrevendo as mudanças.

    - Fixup : Semelhante ao _squash_, mas o commit a ser fundido não terá descrição. O commit é simplesmente fundido com o commit anterior e a mensagem de descrição anterior é usada para descrever ambas as mudanças.

    - Exec : Permite-nos executar comandos de shell arbitrários contra um "commit".

## Exemplos de uso do rebase.
Iniciaremos o exemplo com o comando:
- `git rebase -i HEAD~7`.
Nossa IDE exibirá as seguintes linhas:
 pick 1fc6c95 Patch A
 pick 6b2481b Patch B
 pick dd1475d Algo que quero separar
 pick c619268 Uma mudança em Patch B
 pick fa39187 Algo que quero adcionar ao patch A
 pick 4ca2acc Uma descrição para reword
 pick 7b36971 Algo para mover antes do patch B.

 Neste exemplo faremos o sequinte:
 - Combine o quinto commit (fa39187) com o commit "Patch A" (1fc6c95), usando _squash_ (combinando).
 - Mova o último commit (7b36971) para cima antes do commit "Patch B" (6b2481b) e mantenha-o como um _pick_.
 - Fundir o commit "A change in Patch B" (c619268) com  o commit "Patch B" (6b2481b) e pular a mensagem de confirmação usando o _fixup_.
 - Separe o terceiro commit (dd1475d) em dois commits menores usando a _edit_.
 - Corrigir a mensagem de confirmação mal escrita do commit (4ca2acc), usando _reword_.
 
 #### Para começar, teremos que modificar os comandos no arquivos para que apareçam da seguinte forma:

pick 1fc6c95 Patch A
squash fa39187 Algo para adcionar ao patch A
pick 7b36971 Algo para mover antes do patch B
pick 6b2481b Patch B
fixup c619268 Uma mudança no Patch B
edit dd1475d Algo que será divido em commit menores
reword 4ca2acc Uma descrição para reword.

Podemos modificar o commit agora com:
- `git commit --amend`.
Uma vez que tenhamos feito o "commit" das mudanças, executamos:
-`git rebase --continue`.
Nesse momento podemos editar qualquer um dos arquivos do nosso projeto. Para cada mudança executaremos novamente: 
_ `git commit --amend`.
E então : 
- `git rebase --continue`.

## Carregando o código de Rebase para o |GitHub.
Como modificamos a história de GIT, a origem comum do comando: `git pull origin` não vai funcionar.
Teremos que modificar o comando executando um "push forçado" de nossas últimas mudanças.
    Não sobreescrever mudanças.
- `git push origin main --force-with-lease`.

    Sobreescrever mudanças.
- `git push origin main --force`.

# Stash.
Git tem uma área chamada "Stash" onde podemos armazenar temporariamente imagens de nossas mudanças sem "commitá-las" no nosso repositório. É separado do diretório de trabalho (working three), da área de "staging", ou do repositório remoto.
Esta característica é útil quando fizzemos mudanças em um ramo (*branch*), e não estamos prontos para realizar um commit, mas precisamos mudar para outra "branch".

## Salvar mudanças no stash.
Para salvar nossas mudanças no stash, nós usamos o seguinte comando:
- `git stash save "Descrição opcional"`.
Isto salva as mudanças e reverte o diretório de trabalho para o que parecia no nosso último commit. As mudanças saçvas estão disponíveis em qualquer ramo (*branch*) daquele repositório.
_Observe que as mudanças que deseja salvar devem estar nos arquivos rastreados (*git add*)._

## Ver mudanças guardadas no stash.
Para ver o que está em nosso "_stash_", nós usaremos o seguinte comando:
- `git stash list`.
Este comando retorna uma lista de nossas mudanças salvas no seguinte formato:
`stash@{0} branch-stashed-changes-in:Descrição`
A parte do `stash@{0}` é o nome do "stash" e o número em chaves é o índice. 
Se esquecermos as mudanças que fizemos no stash podemos ver um resumo delas com :
- `git stash show <nome_do_stash>`
Ex: `git stash show -p stash@{0}`

Se quisermos ver o layout "diff" podemos incluir a tag "-p"

## Recuperando mudanças no stash.
Para recuperar as mudanças do stash e aplicá-las ao ramo (*branch*) atual em que estamos trabalhando, temos duas opções:
 - `git stash apply <nome_do_stash>`.
    Aplica as mudanças e deixa uma cópia no "stash".
- `git stash pop <nome_do_stash>`.
    Aplica as mudanças e elimina os arquivos do "stash".
Podem haver conflitos ao aplicar as mudanças, podemos resolver os conflitos da mesma forma que resolvemos os conflitos em "merges".

## Apagar mudanças salvas no stash.
Se quisermos remover as mudanças guardas no stash sem aplicá-las, executaremos o seguinte código: 
- `git stash drop <nome_do_stash>`.
Para limpar tudo do stash:
- `git stash clear`.

# Clean.
Enquando trabalhamos em um repositório, podemos adcionar a ele arquivos qeu não fazem parte do nosso diretório de trabalho ( working three), arquivos que não devem ser adcionados ao repositório remoto.
O comando "clean" age sobre arquivos não rastreados, que são arquivos que estão no diretório de trabalho (working three), mas ainda não foram adcionados ao índice de rastreando ( `git add`).

- `git clean`.

Verifique quais arquivos serão removidos:
- `git clean --dry-run`.

Entretanto, a execução do comando "clean" pode resultar em um erro. Pois a configuração global do GIT requer a utilização da opção de "força". Este é um mecanismo importante de segurança, pois este comando não pode ser desfeito.
- `git clean [-f --force]`.

