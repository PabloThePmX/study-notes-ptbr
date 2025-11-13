# Rotas

* No `app.routes`, dentro do array, abrir um objeto (transformando o array em um vetor) contendo os itens `path` e `component`.
  * No `path`, colocar o caminho, e no `component` dizer o nome de qual página deverá ser renderizada.
    * Sem usar o `/` no `path`.
  * No path, caso for usada alguma variável para o path, colocar `/:nomeVar`
* No `app.component` retirar o conteúdo e deixar apenas a tag `router-outlet`.
  * Possível colocar o `header` e o `footer` aqui também, visto que estes serão os mesmos em todas as páginas.
  * A parte dinâmica fica dentro dessa tag.
* Ao usar as rotas para navegar usando o `<a>`:
  * No TS do componente que vai usar, importar o RouterModule.
  * Na tag `<a>` colocar o biding `[routerLink]="['path']"` ao invés de `href`.
    * Se precisar passar algum parâmetro pelo link, passar como `'path', id`.
      * O parâmetro é uma variável, portanto não precisa estar em aspas simples.
    * Para buscar o valor dos parâmetros enviadas ao componente clicado, no construtor do componente, receber um atributo privado do tipo `ActivatedRoute`
      * No `ngOnInit`, usar o `paramMap` desse `ActivatedRoute` e chamar o método `subscribe` e com o lambda, pegar o valor dos parâmetros.
        * Para pegar um valor especifico, usar o `get("nomeItem")` nas propriedades.
          * Salvar isso em uma propriedade (usando o `this.prop`) e talvez seja necessário dizer que a propriedade é nullable.
  * Criar uma função para setar os valores pegos no construtor, no componente.
    * Fazer um where (filter) no banco e salvando em uma constante.
      * Pegar o primeiro valor retornado, pois vai retornar um array (pois pode ter mais que um resultado).
    * Chama-la logo após pegar o valor da propriedade que vem por parâmetro.
    * Nessa função, alimentar o resultado da busca no banco nas propriedades.* No `app.routes`, dentro do array, abrir um objeto (transformando o array em um vetor) contendo os itens `path` e `component`.
  * No `path`, colocar o caminho, e no `component` dizer o nome de qual página deverá ser renderizada.
    * Sem usar o `/` no `path`.
  * No path, caso for usada alguma variável para o path, colocar `/:nomeVar`
* No `app.component` retirar o conteúdo e deixar apenas a tag `router-outlet`.
  * Possível colocar o `header` e o `footer` aqui também, visto que estes serão os mesmos em todas as páginas.
  * A parte dinâmica fica dentro dessa tag.
* Ao usar as rotas para navegar usando o `<a>`:
  * No TS do componente que vai usar, importar o RouterModule.
  * Na tag `<a>` colocar o biding `[routerLink]="['path']"` ao invés de `href`.
    * Se precisar passar algum parâmetro pelo link, passar como `'path', id`.
      * O parâmetro é uma variável, portanto não precisa estar em aspas simples.
    * Para buscar o valor dos parâmetros enviadas ao componente clicado, no construtor do componente, receber um atributo privado do tipo `ActivatedRoute`
      * No `ngOnInit`, usar o `paramMap` desse `ActivatedRoute` e chamar o método `subscribe` e com o lambda, pegar o valor dos parâmetros.
        * Para pegar um valor especifico, usar o `get("nomeItem")` nas propriedades.
          * Salvar isso em uma propriedade (usando o `this.prop`) e talvez seja necessário dizer que a propriedade é nullable.
  * Criar uma função para setar os valores pegos no construtor, no componente.
    * Fazer um where (filter) no banco e salvando em uma constante.
      * Pegar o primeiro valor retornado, pois vai retornar um array (pois pode ter mais que um resultado).
    * Chama-la logo após pegar o valor da propriedade que vem por parâmetro.
    * Nessa função, alimentar o resultado da busca no banco nas propriedades.* Arquivo para armazenar as rotas.
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
  * Para buscar o parâmetro em rotas filhas, usar a propriedade firstChild (com nullable) antes de chamar a propriedade `params` ou `queryParams`.
  * Da pra colocar guards apenas para o filhos, com o `canActivateChild`

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