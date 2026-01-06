# Herança e Polimorfismo em C#

## Herança

* A herança serve para reutilizar atributos, métodos e comportamentos de uma classe em outras classes.
  * Agrupa coisas do mesmo tipo mas que tem características diferentes.
  * Uma classe contendo as coisas mais "gerais" e outras classes que herdam desta classe mais geral, e aplicam suas respectivas propriedades e métodos.
  * Classe pai e classe filha.
* Ao tentar fazer herança, verificar o que há de comum entre as classes.
* Para utilizar a herança de uma outra classe:
  * Colocar `:` no nome da classe herdeira, e então dizer o nome da classe a dar essa herança, a classe pai (Ex.: `public class Aluno : Pessoa`).
    * As propriedades, métodos, etc criados na classe Aluno, são apenas dele.
* Herdar é como copiar o código da classe e colocar nesta outra (sem repetir o mesmo código, obviamente).
* É possível herdar de classes filhas, porém não é recomendado por causa da alta complexidade que isso pode acabar se tornando. (fica uma cascata de classes, cheia de dependências, as quais são melhores evitar).
  * As classes vão herdar todas as propriedades, métodos, etc das classes.
* Não pode herdar duas classes ao mesmo tempo.
  * Ou seja, uma classe só pode ter uma herança.
  * No C# não é possível, outras linguagens talvez deixem.
  
## Polimorfismo

* O polimorfismo significa muitas formas.
  * Com ele é possível sobrescrever métodos das classes filhas para que se comportem de maneira diferente e ter a sua própria implementação.
* Para permitir que o método seja sobrescrito é necessário colocar na sua declaração a palavra `virtual` antes do tipo que vai retornar. (Na classe pai) (Ex.: `public virtual void Método()`)
  * Na classe filha deverá ser declarado esse mesmo método com a palavra `override` antes do tipo do retorno. (Ex.: `public override void Metodo()`)
    * Dentro dele, modificar do jeito desejado.
  * Por baixo dos panos o compilador entende que existe aquele método na classe pai, mas que ele será sobrescrito por aquele da classe filha.

### Tipos Polimorfismo

* Existe o polimorfismo de overload, que é quando há métodos com nomes iguais mas parâmetros diferentes. (Ele não depende de herança) (Early Binding)
  * Polimorfismo em tempo de compilação.
* Enquanto o polimorfismo de override depende de herança (Late Binding)
  * Polimorfismo em tempo de execução


