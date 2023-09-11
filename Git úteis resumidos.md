# Criar etiquetas assinadas ou não assinadas.
Por que assinamos um código? A razão é que ele mostra a autoridade do código, quem o escreveu e quem deve ser responsabilizado. Para criar uma tag simples:
- `git tag exemplo`.
Isto cria uma tag baseada na versão atual do repositório.
Para criar uma etiqueta (tag) não assinada contendo uma mensagem:
- `git tag -a nome_da_tag -m "mensagem da tag"`.
Finalmente, se quisermos assinar uma etiqueta(tag):
- `git tag -s minhaTag`.
Para verificar uma etiqueta assinada:
- `git tag -v minhaTag`.
## Remoção de uma etiqueta.
Para remover quais "tags", navegamos até o repositório GitHub local e digitaremos o seguinte comando no terminal: 
- `git tag -d <nome_da_tag>`.
- `git push origin :nome_da_tag`.

# Git Checkout.
Este comando é utilizado para se movimentar entre ramos (branches).

-`git checkout nome_da_branch`.

# Git Push.
Este comando é utilizado para empurrar arquivos para o repositório remoto.
- `git push -f origin master`.

# Git Fetch.
Útil quando se interage com um repositório remoto. Basicamente, este comando é usado para recuperar o trabalho feito por outroas pessoas e atualizar nosso projeto local em conformidade.
- `git fetch nome_remoto`.

# Git Pull.
Este comando serve para quando um desenvolvedor deseja solicitar que as mudanças no repositório remoto sejam consideradas para inclusão no repositório local.
- `git pull nome_remoto`.

# Verificar registros anteriores.
Para ver todos os commits que foram feitos em um repositório, podemos usar:
- `git log`.
Por padrão se não forem passado argumentos. Ele exibirá os registro em ordem cronológica reversa.
Ex: `git log --oneline`.
