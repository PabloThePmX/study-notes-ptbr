# Métodos de Extensão

* Serve para "estender" um determinado tipo com algum comportamento.
* Vai ser uma classe estática, pois não deverá ser instanciada.
* No método, quando for declarada a variável de entrada, colocar o `this` antes do tipo, pois isso dirá que aquele tipo deverá receber essa extensão.
  * Então, qualquer variável daquele tipo declarado poderá chamar a extensão.
* Isso basicamente estende o comportamento do tipo a partir de um método criado.
