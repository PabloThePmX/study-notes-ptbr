# Garbage Collector

* Um serviço em background que limpa a memória automaticamente quando for necessário.
  * Em linguagens como C, isso precisa ser feito manualmente para evitar memory leak.
* Existe uma área chamada "Gen 0", e quando essa área estiver cheia, o GC vai rodar.
* Da pra chamar manualmente com `GC.Collect()`, mas não é recomendado, pois o GC já sabe o melhor momento para limpar.
* Não é possível determinar o momento que o GC vai rodar.
* Ele busca por objetos que não tem mais referências para outros objetos.
  * Ao encontrar, ele marca aquele objeto como garbage.
  * Depois, ele pega a memória de volta.
* Para ter um código performático, buscar escrever de uma forma que não precise ficar alocando memória, para que o GC seja chamado o menos possível.
  * Mas não adianta fazer algo tão complexo também, pois vira um trade off.
* Um método "finalizer" é chamado quando um objeto é limpo pelo GC, e para cria-lo, usar `~Metodo() {}`.
  * É um destructor.
  * Ele pode deixar a coleta mais devagar.
* Em um servidor, a thread do GC ganha uma prioridade maior que a do programa em si.
  * Setar a variável de ambiente `DOTNET_gcServer` com o valor `0` para ativar o GC de workstation, que é o default em containers docker.
    * Mas não é recomendado, pois o que ele faz é liberar a memória logo que for usada, mas isso nem sempre é melhor, pois toda vez que precisar da memória de novo, ela vai precisar ser buscada/alocada novamente.

## Generations (Heaps)

* Todos os objetos recém criados são agrupados como Generation 0.
  * Costuma ser pequeno, pois a maioria dos objetos não duram muito tempo.
* Depois existe a Generation 1, que são todos aqueles que "sobreviveram" a geração 0.
  * O GC percebe que se o objeto está aqui, quer dizer que provavelmente não será uma variável de acesso rápido, portanto o scan é feito com menos frequência.
* E por fim, a Generation 2, para objetos de longa duração.
* Funciona com heap pointers, no momento em que um novo objeto vai pro coletor, ele vai ser "armazenado" na posição que o pointer está.