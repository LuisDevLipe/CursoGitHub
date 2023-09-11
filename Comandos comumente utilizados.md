## Uso do Commit
Para fazer uma captura do estado atual da área de staging, executaremos o comando de "commit".
Devemos também acrescentar uma descrição para o "commit" vamos utilizar a flag ``-m`` seguido da descrição entre aspas duplas.

- ``git commit -m "Descrição da versão" ``

Agora temos uma "imagem" do do projeto, ou seja, uma cópia do nosso código desde o último commit até o momento atual.

## Uso do Status
Utilizando o comando:
- ``git status -s``.
Esta será a pasta que o GIT utilizará para criar áreas locais de staging do repositório.

## Uso do log
Para obter uma lista de todas as cópias que temos no repositório local, usaremos o comando:
- ``git log -online``

## Uso do Reset
Se quisermos restaurar o arquivo para uma versão anterior que tínhamos, ou seja, restaurar o arquivo, deveríamos usar o comando:

- ``git reset -hard 09f1c5``
Como podemos ver, temos que passar o código alfanumérico do commit que queremos recuperar.
Deve-se notar que, tendo voltado para um commit anterior que tivemos, as próximas versões que foram criadas após esse momento não existirão mais. Em outras palavras, podemos voltar a uma versão anterior, mas uma vez que fazemos isso, perdemos todas as versões após essa versão.
