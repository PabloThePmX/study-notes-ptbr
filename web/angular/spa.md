# Single Page Application

* Reatividade:
  * Qualquer alteração feita em algo vai atualizar automaticamente, visto que há uma "conexão" entre a ação e o item que está sofrendo essa ação.
    * Em outras palavras, qualquer alteração que ocorre na parte lógica, vai refletir no layout.
    * Ex:. Adiciona um item em uma lista, e não precisa fazer um for novamente pra mostrar esse item.


## Diretivas
* As diretivas são comandos para manipular a DOM dinamicamente.
* Dois tipos de diretivas, atributos e estruturais.
  * Precisam ser colocados com `*` na frente.
  
### Atributo
* Alteram o comportamento de um elemento em específico, de um componente ou de outra diretiva.
* `NgClass` - altera a classe css dinamicamente (dark e light mode).
  * Fazer um biding e alimentar com uma propriedade.
  * Vai usar a classe css que possui o mesmo nome que o valor setado na propriedade.
  * Usar isso para fazer o `toggle`.
* `NgStyle` - altera um conjunto de estilo.
  * Fazer um biding passando as propriedades css, e cada propriedade pode estar atribuída ao valor de uma propriedade ts.
  * Fazer interpolação para alterar os valores.
* `NgModel` - elemento de formulário se comunicam com o código ts.
  
### Estruturais
* Alteram a estrutura da DOM.
* `NgIf` - condicional que verifica se algum conteúdo deve ser exibido ou não.
  * Se quiser ocultar por completo, poderíamos colocar a condição dentro da tag do componente no root `app.component`.
  * Possível usar data biding de alguma propriedade.
    * `isAliveNomeComponente`.
  * Possível usar um bloco condicional usando a tag `<ng-template>` e usar o `#` dentro da tag, para dar um nome a esse bloco.
    * Esse bloco vai somente aparecer caso o isAlive for false, caso contrário, ele fica ocultado.
    * Ai dentro do `ngIf` é possível declarar um else e chamar esse bloco. 
      * `<componente *ngIf="isAliveComponente; else outroBloco"></componente>` e esse outro bloco é o `<ng-template #outroBloco>`.
* `NgFor` - repete um elemento para cada item em uma lista (loop for).
  * Usar no `<li>` e consequentemente ele vai repetir esse item da lista n vezes.
    * A sintaxe dentro do `<li>` será `*ngFor ="let p of produtos"` e a vai ser usada a interpolação do item para renderizar ele na tela.
  * Possível trabalhar com index.
    * A palavra é reservada, ou seja, se queremos pegar o index do item, é necessário alimentar o `index` em alguma variável pela tag.
      * Bom para usar quando queremos deletar um registro, pois ao clicar no registro, é retornado o index do item.
* `NgSwitch` - utilizado para alternar entre comportamentos alternativos (switch case).
  * Precisa atrelar a uma propriedade, e chama via data biding (não com o `*` e sim `[]`).
  * Cada condição dentro do switch, precisa ter declarado o `*ngSwitchCase` com algum valor para condicionar a partir do valor da propriedade do switch.
    * Precisa alimentar com aspas simples (dentro das aspas duplas).
  * O case default é o `ngSwitchDefault`