# Comandos Extras

* `git branch -r -d origin/branch-name`: Remove a branch remota localmente.
* `git stash clear`: Limpa tudo que tem em stash.
* `git rebase -i --root`: Vai deixar ordenar os commits, dessa forma, da ate pra mudar o commit inicial.
  * Pode ser perigoso, pois para enviar para o repositório remoto é necessário fazer um `-force`, dessa forma reescrevendo o flow atual.
* `git show`: Mostra o último commit realizado, incluindo as diferenças.
* `git log --oneline -n`: Mostra apenas as mensagens dos últimos n commits (o `n` é quantos commits para baixo serão mostrados).