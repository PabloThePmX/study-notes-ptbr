# Tipos de Listas

# Queue

* Coleções do tipo fila (classe `Queue`), o primeiro que entra vai ser o primeiro a sair, etc. (FIFO - First in, first out).
* Percorrer a mesma igual é feita com array ou lista.
* Método `Enqueue()` para adicionar e `Dequeue()` (sem parâmetro, remove o primeiro elemento) para remover o item.
  
# Stack

* Coleção do tipo pilha (classe `Stack`) (Ex.: pilha de roupas?), o último que entra vai ser o primeiro a sair (LIFO - Last in, first out)
* Método `Push()` para adicionar um item no topo da pilha e `Pop()` para remover o item do topo.

# Dictionary

* Uma coleção `Dictionary` é uma coleção do tipo chave-valor.
* A sintaxe dele é: `Dictionary<tipo1, tipo2> = new Dictionary<tipo1, tipo2>()`.
* Ao ler usando o `foreach`, o tipo do item deverá ser `KeyValuePair`.
* Para remover, é só passar a chave por parâmetro.
* Para alterar um item, é preciso passar a chave com [] e alimentar o valor da coleção com o novo valor que desejamos.
* Usar o método `ContainsKey()` para verificar se já existe a chave.

# Tupla 

* Uma tupla oferece uma sintaxe concisa para agrupar vários elementos de dados em uma estrutura de dados leve.
  * Não é uma coleção, mas pode ser uma.
* Cria vários itens, um para cada valor passado
* Para declarar uma tupla: `(<tipo1 e nome>, <tipo2 e nome>, etc) <nome variável> = (<valor1>, <valor2>, etc)`. 
* Dessa forma é melhor para a legibilidade pois podemos colocar o nome na declaração dos tipos.
* Outra sintaxe é usando o `ValueTuple`, ou `Tuple.Create`.
* As tuplas podem fazer métodos retornarem mais de um valor.
* Colocar a declaração das variáveis (com o tipo) no momento de declarar o tipo do retorno no método, a declaração é basicamente igual a das tuplas como variáveis.
* No return colocar os valores todos juntos, igual quando valores são alimentados na tupla.
* Usar `_` na variável de retorno da tupla caso queiramos descartar aquela variável e não usar seu valor na classe em que ela foi chamada.