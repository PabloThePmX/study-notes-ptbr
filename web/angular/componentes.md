# Componentes (sem framework)

* Todo componente nada mais é que uma **função JS**, que vai retornar JS, HTML e CSS.
  * Conjunto de elementos, com seu próprio estilo, propriedades (pra deixar o componente dinâmico, basicamente vai receber um parâmetro para alimentar a propriedade) e scripts.
* Utiliza a shadow DOM, ou seja, cada componente é um DOM diferente.
* Geralmente a estrutura do projeto é `src/Components/NomeComponente.js`
* Criar uma classe em JS:
  * `class Nome extends HTMLElement{}`
    * Ela herda todos os elementos do HTML.
      * E vai funcionar como um elemento HTML.
* Para chamar o construtor:
  * `constructor {super()}` ou seja, chamando o construtor da classe base (pai).
* Para criar um shadow Dom, dentro do construtor da classe colocamos:
  * `const shadow = this.attachShadow({mode: "open"});`
    * Criando a sombra e dizendo que o JS externo pode modifica-la (por causa da definição do `mode`).
  * Assim, para escrever alguma tag, escrevemos dentro do `innerHTML` dessa sombra.
    * `shadow.innerHTML = "<h1>Hello World</h1>"`.
* Para criar o componente, usar o `define` do `customElements`, dando um nome (o seletor), e especificando qual a classe que está criando esse componente.
  * Isso fora da classe.
  * Importante sempre ter um `-` no nome, para diferenciar das tags padrões.
* Ao chamar o script, colocar a propriedade `defer` para executar esse componente apenas depois que o DOM padrão da página seja criado.
* Para usar o construtor, chamar como se fosse uma tag, ou seja, o seletor definido no customElement, vai ser o nome da tag.
* Para criar uma variável com uma tag, utilizamos o `document.createElement("TAG")`, e dessa forma, podemos alimentar as suas propriedades conforme achamos necessário.
  * Fazer assim para criar um estilo próprio para o componente, usando a tag `style`.
    * No `text-content` do style, é bom usar a crase para o valor, pois podemos assim deixar esse valor dinâmico, por causa da interpolação.
      * Esse style vai ser igual a um css normal, com os seletores e suas propriedades.
        * Porém serão os seletores do componente em si.
* Para colocar (anexar) o novo elemento no shadow DOM, usar o `appendChild` com o novo elemento nele.
* Para trabalhar com propriedades:
  * Definimos que o valor de algo vai ser buscado por um atributo com o `this.getAttribute(novo-atributo)`
    * Para usar isso, colocar o nome do atributo na tag, contendo o valor desejado, como em `<titulo-dinamico titulo="teste de valor de propriedade"></titulo-dinamico>`.
  * Para setar um valor pelo componente, chamamos o método `setAttribute()` no elemento que queremos setar, contendo o tipo (ou seja, class, id, etc) e o valor.
  * Para setar valores em tags que possuem propriedades (como `<img>` e `<a>`):
    * O próprio elemento vai deixar acessa-lo para setar, `elementoImagem.src = getAttribute("url-imagem")`
* Podemos usar métodos para os componentes.
  * Geralmente são criados os métodos `style()` e `build()`.
    * Ou seja, podemos chamar o `appendChild` para o retorno de cada método.
      * No final tem que sempre retornar o componentRoot.
  * Dentro do `build`, podemos criar vários métodos para cada um dos tipos de elementos e seus filhos.
* Hierarquia vai funcionar com o `appendChild`, ou seja, criamos vários elementos, e vamos fazendo o append conforme são os filhos, até chegar no componentRoot.
  * Teoricamente, cada elemento com uma classe diferente, vai ser um elemento que devemos criar e anexar no root.
* Ao mexer com as propriedades, podemos colocar uma condição `OR` para definir um valor padrão, ou seja, se não enviar algum valor, vai usar o default.
* A classe seletora principal geralmente é chamada de `app-root`.