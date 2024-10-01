# Flexbox
* Existem algumas propriedades importantes e principais:
  * ### Para Container
    * `display: flex`: vai dizer que é do tipo flex, ou seja, vai colocar um plano cartesiano com x e y no elemento.
    * `flex-direction`: diz a direção dos itens dentro daquele container pai, o padrão é `row`, ou seja, os itens ficam ao lado um do outro.
    * `justify-content`: vai alinhar os itens no eixo x.
    * `align-items`: vai alinhar os itens no eixo y.
    * `flex-wrap`: define se todos os itens ficarão na mesma linha ou não, ou seja, se colocar-mos `wrap` ele vai espaçar os itens e colocar linhas adicionais se necessário para eles.
    * `flex-flow`: é um shorthand para unir as propriedades `flex-wrap` e `flex-direction`, ou seja, colocamos ambos os valores em uma propriedade só.
    * `align-content`: determina como as linhas em si vão ser espaçadas, aceita os mesmos valores do `justify-content` e funciona apenas quando temos o `wrap` e há itens sendo afetado por isso, ou seja, há mais de uma linha de itens.
    * `gap`: coloca distância entre os elementos.
  * ### Para os elementos em si:
    * `align-self`: funciona da mesma forma que o `align-itens` porém é para elementos únicos, ou seja, não deve ser usado no container pai, e sim em algum dos seus elementos.
    * `order`: todos os itens tem ordem 0, porém, podemos setar esse valor automaticamente e alterar a ordem, sendo que o 0 será o primeiro item à esquerda.
      * Podemos também usar números negativos quando queremos que um item esteja mais a esquerda que o item com `order` 0.
      * É perigoso usar isso, pois pode bagunçar a semântica do código.
    * `flex-grow`: faz um item crescer caso haja espaço disponível no container. (default é 0)
    * `flex-shrink`: diz o quanto um item deverá diminuir conforme a página muda de tamanho. (default é 0)
    * `flex-basis`: tamanho inicial que vai usar para determinar o `flex-shrink` e `flex-grow`, é quase um `width`.
    * `flex`: é o shorthand usado para definir essas três últimas propriedades, pois elas costumam sempre trabalhar juntas.
* As vezes, uma boa maneira de redimensionar e fazer com que os itens funcionem melhor em telas menores (celular) é retirar um `flex` após um determinado tamanho, pois assim, os elementos vão ser ordenados um em cima do outro, conforme o padrão.