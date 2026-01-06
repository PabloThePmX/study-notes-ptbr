# Classes Abstratas

* Uma classe abstrata tem como objetivo ser exclusivamente um modelo para ser herdado, não podendo ser instanciada.
  * Possível implementar métodos ou deixá-los a cargo de quem herdar.
* Servirá como um "molde", Ex:. a classe "Conta", que deverá ser definida se é corrente ou poupança, usando os atributos gerais que existem na classe da conta em si (que não será instanciada, apenas herdada)
  * Dentro dessa classe abstrata, podemos ter métodos abstratos também.
  * E desse métodos, podemos pegar eles como moldes e usar o polimorfismo para alterá-los conforme o necessário.
* Na declaração da classe, utilizar a palavra `abstract` antes do tipo do retorno.
  * Ele não tem corpo, ou seja, não precisa abrir e fechar chaves como os outros métodos.
    * Não tem implementação, é apenas uma abstração.
  * Quem herdar a classe, deverá implementar os métodos abstratos.
    * Usar o `override` na declaração desses métodos.
* O tipo de proteção `protected` deixa a variável ser alterada apenas por suas classes filhas.
  * Ou seja, a variável é visível em classes que foram herdadas.
* Ao usar um construtor na classe pai, devemos colocá-lo obrigatoriamente nas classes filhas também
  * Criar o construtor e depois do `()` da declaração colocar: `: base(variável)`.
    * Declarar a variável nos parâmetros do construtor e na base só colocar o nome dela (vai ser a variável usada no construtor da classe base).
  * Aquele base significa que a variável está sendo enviada para a classe pai (a base).
  * O construtor da classe filha pode ter mais parâmetros, que aí seriam os parâmetros do construtor apenas dessa classe filha
* Dá pra ter sobrecarga de construtores.

# Classe Selada

* Uma classe selada tem como objetivo impedir que outras classes façam uma herança dela.
  * Também existem métodos e propriedades seladas.
* Usar o termo `sealed` na declaração para que seja uma classe/método selado
  * Ela até pode ser a classe filha de outra, só não pode ser a pai
* Todas as classes criadas herdam da classe `System.Object` do .NET.
  * Derivam direta ou indiretamente dessa classe, e ela tem como objetivo prover serviços de baixo nível para suas classes filhas.
    * Métodos mais de baixo nível.
  * É literalmente a mãe de todas as classes do .NET.
  * Equals, ToString, etc vem do object.
* Dá pra fazer um `override` nesses métodos do object.
