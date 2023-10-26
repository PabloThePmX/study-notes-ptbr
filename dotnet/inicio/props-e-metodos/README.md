# Propriedades

* Uma propriedade é um membro que oferece um mecanismo flexível para ler gravar ou calcular o valor de um campo particular.
  * A propriedade deixa criar “regras” para campos. (validações)
  * Para criar uma propriedade podemos digitar prop que vai autocompletar
    * Sintaxe: “public <tipo> <nome> {get; set;}”
      * O get é para pegar o valor, e o set para atribuir
      * Essa sintaxe faz o get e o set aceitar qualquer valor.
  * No .csproj tem uma opção para desabilitar o warning dos nulos nas propriedades.
  * Para identificar uma propriedade, devemos ver se a mesma tem get ou set. (Pode ter só um)
    * Ao chamar pelo VS, a propriedade vai ter um ícone de chave inglesa.
* Obviamente, o método vai dentro da classe
* Por convenção, o nome da propriedade será em PascalCase, e sem o uso de caracteres como “_”
* Para colocar o “using” do namespace no Program.cs, é só copiar o namespace completo da classe.
  * Instanciar a classe
    * Possível alimentar os valores de propriedades ao instanciar elas
      * Ou seja, ao criar uma propriedade é possível alimentar o valor da mesma em uma outra classe.
* Para colocar validação no set:
  * Criar uma nova variável (fora da propriedade) do tipo privado (que só pode ser alterado dentro da classe atual), com o nome com underline na frente “_<nome da variável do get, set>”
  * Agora transformar a propriedade criada antes, como se fosse um método
    * Abrir o set{} e colocar uma validação nele (usando o valor de “value”)
      * Lançar exceção como “throw new ArgumentException(texto)”
    * E depois alimentar a variável privada criada com o “value”
* No get teremos o retorno:
  * Neste momento usaremos o return na variável privada, e com isso podemos fazer modificações na mesma (Ex.: Colocar todas maiúsculas)
* No get e no set podemos resumir os {} e colocar body expressions, que seria “=>” (caso temos apenas uma linha de valores)
  * Quando colocamos validações em apenas um dos tipos, precisamos usar o body expressions para “chamar” a variável privada. (não é necessário fazer nada mais além disso).
* Modificadores de acesso:
  * Public: qualquer um pode utilizar/instanciar.
  * Private: é permitido acessar apenas dentro da classe instanciada.
    * Fica “protegida”, ou também chamado de “encapsulamento”
* Propriedades somente com “get” são somente leitura, pois não tem como setar valores.
  * Possível usar para juntar duas propriedades (Ex.: Nome e Sobrenome).

# Lista
* Dentro do “<>” da lista, podemos usar “tipos” vindos de outras classes instanciadas.
  * São como os tipos “normais” como string, int, bool, etc.
* Assinatura de um método começa depois do public
* O “Remove” e “Add” de uma lista podem retornar booleanos de sucesso ou não.

# Construtores
* Os construtores permitem que o programador defina valores padrão, limite a instanciação e grave códigos flexíveis e fáceis de ler.
  * Permite colocar valores padrão em uma classe no momento de sua instanciação.
  * Obriga o usuário a enviar os valores para o construtor
* Por convenção, o construtor é o primeiro item a ser declarado em uma classe.
  * A sintaxe para criar um construtor: “public <nome da classe atual>() {}”
  * O construtor não tem retorno.
  * Como parâmetro do construtor, é preciso declarar as variáveis das propriedades que queremos usar nele (diferente das já declaradas na classe).
    * Assim, na hora da declaração, podemos passar os valores que queremos usar por parâmetro.
  * Podemos criar o mesmo construtor (com o mesmo nome) porém sem parâmetros também, assim, cabe a nós decidir se queremos enviar valores no parâmetro ou não.
    * Ou seja, ele tem overloads
* Dentro do construtor, alimentar as propriedades com os valores vindo por parâmetro.
  * Ou seja, dentro do construtor será definido onde esses valores irão ir e como serão usados.
* Nos parâmetros enviados, podemos colocar “<nome>:” antes do valor para dizer o que é.
  * Porém precisa ser igual ao nome da variável na declaração do construtor.
