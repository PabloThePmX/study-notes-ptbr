# Testes Unitários

* Existem vários tipos de testes, e não só os unitários (integração, regressivo, segurança, etc).
* Os testes unitários são testes realizados diretamente no código fonte, pelo desenvolvedor.
  * Um código para validar o código.
  * Procurar testar a menor unidade de código possível.
  * Testar acertos e possíveis erros.
* O teste unitário é um projeto que referencia o projeto que vai ser testado.
  * Precisa adicionar essa referência manualmente.
* Criar um novo projeto do tipo de testes (`dotnet new xunit`).
* O teste é feito nac classe UnitTest (cenário de teste).
  * O nome da classe de teste pode ser o mesmo da classe que iremos testar (ClasseTestes).
* A anotação `[Fact]` diz que o "método" é um teste e precisa ser checado.
* O nome do método deve refletir o que vai ser testado ali.
* Temos tres coisas no método: `Arrange`, `Act` e `Assert`.
  * O `Arrange` prepara o cenário, alimentando parâmetros e afins.
  * O `Act` é para executar, chamando o método e gravando o valor em uma variável.
  * O `Assert` é para validar, verificando se o valor retornado esta correto (Na classe Assert).
    * `Assert.Equal` para verificar se o retorno é o correto.
* Precisa instanciar a classe que vai ser usada (pode ser privada).
* Ao rodar o teste, vai rodar os testes de todas as classes.
* Usar a anotação `[Theory]` (para dizer que um conjunto de cenários irão acontecer no mesmo teste) junto com a outra anotação `[InLineData()]` que por parâmetro vai receber o o valor que queremos usar para testar no método.
  * Usar uma anotação para cada valor que queremos usar.
  * Receber o valor por parâmetro, portanto, nao vai ser necessário arrange pois os valores serão pegos direto da anotação.
  * Da pra receber uma lista, objeto, etc.
    * Para ser uma lista, fazer um `new` e inicializar seus valores.
    * No parâmetro precisa ser alterado para o mesmo tipo.
    * Dai no teste da pra usar o `Assert.All`
      * Usar lambda no segundo parâmetro, com a condição que queremos atingir.
      * Vai pegar um item de cada.

## Frameworks de teste
* MSTest da Microsoft
* NUnit
* xUnit (um dos que tem mais documentação)
* Usa-se apenas um deles no projeto.