# Interfaces

* A interface implementa, e não herda.
* Uma interface obriga (como se fosse um contrato), as classes implementadas a terem pelo menos os mesmos métodos declarados na interface.
* A interface permite uma classe ter várias implementações, diferente do conceito de herança.
* A interface contém apenas métodos, propriedades, etc, enquanto a classe abstrata pode ter isso e também variáveis, const, etc.
* Criar uma nova pasta para ter apenas as interfaces.
* Usa o "I" no início do nome da Interface (Ex.: `ICalculadora`).
* A declaração é feita com `public interface INome`.
* Interfaces não tem assessores (public, private).
  * Pois teoricamente sempre será public.
* Métodos da interface podem não ter implementação.
  * Ou podem, aí não é mais necessário implementar na classe
* Para implementar, colocar os `:` da mesma forma que são feitas as heranças na declaração das classes.
* Como a classe abstrata, ela não pode ser instanciada.
  * Porém podemos instanciar chamando um `new` na classe que tem ela implementada (Ex.: `ICalculadora = new Calculadora()`)
* O VS tem um comando para implementar todos os métodos da classe automaticamente.