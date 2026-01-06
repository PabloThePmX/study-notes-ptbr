# Tipos Anônimos

* Os tipos anônimos permitem representar diversos valores em uma única variável como se fosse uma tupla.
* São propriedades somente leitura depois de declarados.
* Sua sintaxe é parecida com a da tupla: `var <nome variável> = new {<nome propriedade1>: <valor propriedade>, <nome propriedade2>: <valor propriedade>};`
* Não precisa declarar o tipo de cada propriedade
* É acessado como um construtor, chama a variável e vai mostrar as propriedades que podem ser selecionadas.
* É comum usar em retorno de coleções.
* Usando quando não queremos pegar o valor de todas as propriedades de um JSON por exemplo.
* Para pegar a propriedade específica de uma lista:
  * Declarar uma variável do tipo var e fazer um select na lista
    * O parâmetro do método select deverá ser `x => new {x.prop1, x.prop2}`
    * E a declaração com o `new` é o tipo anônimo
  * Dessa forma, podemos designar quais valores serão salvos nessa variável do tipo anônimo.
* Depois que pegou a propriedade específica, é só iterar usando essa variável do tipo anônimo como a lista, pois ela será como uma nova lista que possui apenas as propriedades escolhidas no tipo anônimo.
* Bom para usar com LINQ e quando queremos que o objeto seja de um tipo de referência.
  * Na maioria dos casos, tupla vai ser melhor e mais otimizado.