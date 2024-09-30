* O `document` é um objeto, que representa a página em si (o HTML por inteiro).
  * Por se tratar de um documento, ele tem métodos e propriedades (DOM - Document Object Model).
    * O navegador lê o DOM como se fosse uma hierarquia.
* O `classList` do `documentElement` tem o método `toggle`, que tira uma classe caso ela não exista, ou remova caso ela já exista.
  * Bom para ser usado em dark mode.
* Usar o método `querySelector()` para buscar os elementos que possuem aquele seletor.
* Para mudar o atributo, usar o `setAttribute()`.
* Shadow DOM: criar (sub) árvores de documento dentro do DOM.
  * Encapsula os elementos e depois anexa essa árvore na árvore principal.
    * Ou seja, isola um documento, virando um componente.