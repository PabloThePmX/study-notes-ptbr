# Rotas

* Arquivo para armazenar as rotas.
* Ele carrega todos os componentes, e altera os componentes dinamicamente, não precisando recarregar toda a página, isso é o princípio do SPA.
* O `Routes` é um array de objetos de rota. 
* No objeto, podemos usar a propriedade `pathMatch`, que terá os valores `full` e `prefix`.
  * Ele irá dizer, se a rota tem que ser exatamente igual `full`, ou se já contendo o valor, já renderiza o respectivo componente.
  * A url de entrada geralmente precisa ser `full`.
  * É `prefix` por padrão.
* Rota coringa é uma rota que vai ser renderizada quando a url não existir, e para isso, usar o `**` no path.
  * Da pra colocar um `redirectTo` no objeto da rota, para que possa redirecionar para outra tela.
* As rotas ficam dinâmicas apenas dentro da tag `<router-link>`.
* As rotas são feitas com o `routerLink` ao invés do href.
* O `routerLinkActive` é para setar uma classe a parir da url atual, ou seja, se for aberta url A, carrega a classe, se for a url B, carrega a classe apenas na B.
  * Da pra colocar que, ao clicar em alguma opção de menu, vai pintar a opção de outra cor, pois vai estar naquela url, portanto a classe será usada.
  * Junto com ele, existe o `routerLinkActiveOptions` em que é possível dizer que a classe definida vai ser setada apenas quando a url for exatamente aquilo.
  * Pode setar várias classes.
* Possível ter rotas com filhas
  * No arquivo das rotas, cada rota por ter uma propriedade `children` que vai ter um array de rotas que irão complementar o pai, ou seja, se o pai + filha for igual a uma das rotas, renderiza aquele componente em específico.
    * Não precisa colocar o `/` nos filhos.
  * Para buscar o parâmetro em rotas filhas, usar a propriedade firstChild (com nullable) antes de chamar a propriedade `params` ou `queryParams`

## Rotas com parâmetros
* Nas rotas, colocar `/:id` sendo que o `id` será o parâmetro.
* Para pegar o valor desse parâmetro:
  * No componente, injetar o `ActivedRouted` e usar a propriedade `params` com o método `subscribe`:
    * Com o lambda, pegar o valor da resposta (o parâmetro).
  * O `ActivedRoute` permite trabalhar com a url atual.
* Para recuperar query params (variáveis em url)
  * Usar a propriedade `queryParams` e fazer o subscribe também.

## Redirecionar
* Injetar o `Router`
* Dentro de um método, de uma diretiva, etc, usar o `navigate` e colocar a rota que ele precisa ir.