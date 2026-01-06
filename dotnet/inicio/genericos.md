# Classes Genéricas

* Uma classe genérica é uma classe que será definida pelo tipo que for enviado.
* Para definir um tipo genérico, ao invés de escrever o tipo da variável, escrevemos um `T` (na classe ficaria `ClasseExemplo<T>`)
  * Esse `T` é usado assim pois não sabemos o que ele representa, só saberemos quando ele for chamado com o tipo.
* Basicamente é uma classe que usa um tipo T no seus métodos e afins, entretanto o tipo dela só vai ser definido quando for instanciada em uma outra classe.
* E tudo que usar esse `T` dentro da classe (variáveis, métodos, etc), vai usar o tipo o qual a classe foi instanciada.
* Com as classes genéricas conseguimos reusar mais código.
* Sempre quando temos algo com `<>` devemos passar um tipo, pois se trata de uma classe genérica.
