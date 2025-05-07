# Single Page Application

* Imports e Declarations
  * Os `imports` são para declarar as dependências externas, enquanto as `declarations` são para componentes da aplicação.

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
  * Comunicação bi lateral, entre HTML e ts e ts e HTML.
    * Colocar isso em um input que vai alimentar a informação na propriedade no ts.
  * Usa a notação `[()]`, ou seja `[(ngModel)] = propriedade` para setar a propriedade e usar a interpolação para mostrar.
  * Precisa importar o `FormsModule` do core no `app.module`, e precisa colocar no imports também.
  * Podemos usar isso para enviar um item digitado para uma lista e depois mostra-lo (com o `ngFor` por exemplo).
* `ngTemplate`
  * É um template
  * Usar como se fosse um componente, com `<ng-template>`
  * Por padrão sempre vem desabilitado (oculto).
    * Só é mostrado se o `ngIf` dele for true (usar propriedade `isEnableComponente`). 
* `ngContent`
  * Permite que um componente pai passe algo para o componente filho, e nele o componente pode ser reajustado.
  * No pai, dentro da tag do componente, colocar as tags com seus respectivos conteúdos.
    * Podemos enviar outro componente também.
  * No filho, com a tag `<ng-content>` usando um `select="tag"` buscar a tag enviada pelo pai para renderizar.
  
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
* A partir das versões mais recentes do Angular, um novo fluxo (control flow) foi adicionado, agora, ao invés de utilizar diretivas de condição, podemos usar diretamente no HTML, `@if`, `@else`, `@else if`, `@for`, `@switch` etc. 

## Módulos (não são obrigatórios nas versões mais recentes do angular)
* O módulo vai guardar componentes, diretivas, pipes e services.
  * Por padrão, isso fica dentro do próprio arquivo ts nas versões após a 14.
* Precisa importar o `NgModule` do `core`.
* O `app.module.ts` é o principal.
* Podemos ter sub módulos, que deverão ser importados no módulo principal.
  * Neles temos os `exports`, para enviar o que os outros módulos irão usar.
* No declarator `bootstrap` serão colocados os componentes que irão irão iniciar automaticamente.
* Da pra criar um módulo a partir do comando `generate`.
  * Colocar o nome do módulo durante essa geração.
  * Os componentes precisam ser criados dentro da pasta que tem os módulos.
* Geralmente é separado com várias pastas de pages, e em cada uma delas tem o módulo.
* Convenção de pastas:
  * Pode-se criar uma pasta chamada `components`.
  * Geralmente se cria um módulo chamado `shared`, que terá componentes que serão usados em comum por diversas páginas.
  * Também teremos uma pasta chamada `pages` com várias pastas contendo módulos específicos de cada página.
    * A inicial se chama `home`. 
    * Vai ser uma junção dos componentes criados.