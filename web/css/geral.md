# Geral
* O modelo cascata diz, que se houverem mais seletores iguais, a última vai ser utilizada.
  * Ou seja, se houverem dois pesos iguais (especifidade), ele vai pegar o último.
* Cada seletor tem uma especificidade (o peso):
  *  Tag: 0,0,1 = 001
  *  Id: 1,0,1 = 101 -> Mais pesado (forte)
  *  Classe (0,1,0) = 10
* Todas as tags são caixas (box model).
* Algumas tags tem visualização (display) em bloco (block), e outros em linha (inline)
  * O display block tem quebra de linha, enquanto o inline, como o nome já diz, não tem.
* Chamar a função `url` para determinar o caminho de um arquivo (imagem).
* Para centralizar uma caixa que tem uma largura fixa:
  * Usar a propriedade `margin: auto`
    * Só funciona para elementos do tipo `display: block`
* No seletor, podemos declarar mais itens, e o primeiro vai ser o item pai.
  * Ou seja, `#profile img {}` vai pegar todas as tags `<img>` dentro do id profile.
* No css geralmente não precisa colocar altura, pois ela geralmente segue o conteúdo da página.
* O `display: block` vai dar toda a largura que o elemento tem disponível (um `width` fixo por exemplo), forçando o proximo elemento a ir para fora dessa caixa, já o `display: inline` deixa tudo em linha.
  * Alguns elementos tem padrão `block`, e outros `inline`.
    * `<div>` é block.
* Todos os elementos `inline`, vão deixar que o pai defina o seu alinhamento.
  * Ou seja, se usar um `text-align: center`, os elementos filhos da tag vão estar centralizados, independente de serem `inline` ou `block`.
* Usar o `*` no seletor, quer dizer que ele vai aplicar as propriedades para todas as tags dentro daquela tag declarada.
  * Se usar apenas o `*` vai ser tudo.
    * Podemos usar isso para tirar a margem e o padding padrão do navegador.
* O `font-size` padrão do navegador é 16px.
* Para dizer a distância entre as linhas, usar `line-height`.
* Usamos o `box-sizing: border-box` para dizer que os tamanhos que definidos, são definidos para não só o conteúdo da caixa, como também o padding e bordas.
  * O `context-box` usa o valor para apenas o conteúdo, adicionado valores "a mais" para o padding e a borda.
* O shorthand dos cantos segue o sentido horário, top, left, bottom e right.
* O display: flex:
  * Vai tornar os elementos flexíveis.
  * Por padrão, ele deixa os elementos alinhados em linha, e caso algum deles for retirado, ele vai reajustar as distâncias.
    * Podemos determinar a distância entre cada elemento usando a propriedade `gap`.
* No `block` e `flex`, podemos usar o `justify-content` para alinhar os elementos.
* O `align-itens` vai fazer o item alinhar-se no meio da linha do flex.
  * Só funciona caso tiver espaço "não centralizado" para cima ou para baixo dos itens da caixa.
* Para declarar um pseudo-selector para as propriedades aplicadas durante o hover, devemos declarar o seletor com `ul li a:hover {}`
  * Usar a propriedade `transition` no seletor normal, para declarar uma transição para o hover.
* Ionicons.
* O `border-radius` com 50% se torna uma bolinha perfeita.
* Podemos definir variáveis em css.
  * Geralmente definimos na raiz do projeto (html) com `:root{}`
  * Para declarar a variável, colocar `--` na frente.
    * Ou seja `--text-color: white` está definindo o valor `white` para essa variável, e podemos usa-la então em qualquer seletor.
      * Para usar em alguma propriedade: `var(--text-color)`.
* O `display: inline` não aceita algumas propriedades, como `width`.
* Usar o `position: absolute` para permite que o elemento seja sobreposto por outras camadas (elementos).
  * E para mudar a camada `z-index` (que funciona apenas com o `absolute`).
  * Pode-se usar as propriedades `top`, `left`, etc.
  * Caso for setada a opção `position: relative` na tag pai, o elemento vai ser absoluto relativo apenas ao elemento pai.
  * A propriedade `transform` possui diversas funções, e algumas delas são:
    * Girar o elemento.
    * Mover o elemento baseando-se pelo eixo x ou y.
      * Que vai poderá ser relativo ao elemento pai.
    * Para alinhar o item horizontalmente:
      * `transform: translateY(-50%)` `top: 50%`
    * Verticalmente:
      * `transform: translateX(-50%)` `right: 50%`

### Background
* Por padrão uma imagem de fundo se repete.
  * Para isso podemos usar a propriedade `background-repeat: no-repeat`
* E para posicionar uma imagem de fundo, usamos o `background-position: top center`, para centraliza-la conforme o eixo x e y.
* Para cobrir todo o espaço visível da tela com a imagem de fundo, usar `background-size: cover`.
* Para usar tudo em apenas uma propriedade de background, seguir o shorthand:
  * `background: color image repeat position/size`