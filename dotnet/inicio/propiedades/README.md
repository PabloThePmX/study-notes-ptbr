# Propriedades

**TODO: Faltam muitos exemplos práticos, falo deles, mas não mostro como é feito pelo código**

* Uma propriedade é um membro que oferece um mecanismo flexível para ler gravar ou calcular o valor de um campo particular.
  * A propriedade deixa criar “regras” para campos. (validações)
  * Para criar uma propriedade podemos digitar `prop` que a IDE vai autocompletar
      ```C# 
      //modificador de acesso, tipo da prop, nome, e quais ações ela pode realizar
      //essa sintaxe faz o get e o set aceitar qualquer valor.
      public int ValorInicial {get; set;}
      ```
      * O `get` é para pegar o valor, e o `set` para atribuir.
      * Por convenção, o nome da propriedade será em PascalCase, e sem o uso de caracteres especiais como “_”
  * No .csproj tem uma opção para desabilitar o warning dos nulos nas propriedades.
  * Para identificar uma propriedade, devemos ver se a mesma tem get ou set. (Pode ter só um)
    * Ao chamar pelo VS, a propriedade vai ter um ícone de chave inglesa.
* Para colocar validação no `set`:
  * Criar uma nova variável (fora da propriedade) do tipo privado (que só pode ser alterado dentro da classe atual), com o nome com underline na frente: `_valorInicial`
  * Agora transformar a propriedade criada antes, como se fosse um método
    * Abrir o set{} e colocar uma validação nele (usando o valor de “value”)
      * Lançar exceção como `throw new ArgumentException(texto)`
    * E depois alimentar a variável privada criada com o “value”
* No `get` teremos o retorno:
  * Neste momento usaremos o return na variável privada, e com isso podemos fazer modificações na mesma (Ex.: Colocar todas maiúsculas)
*  Propriedades somente com “get” são somente leitura, pois não tem como setar valores.
    * Possível usar para juntar duas propriedades (Ex.: Nome e Sobrenome).
* Obviamente, o método vai dentro da classe
* Para colocar o `using` do namespace no Program.cs, é só copiar o namespace completo da classe.
  * Instanciar a classe
    * Possível alimentar os valores de propriedades ao instanciar elas
      * Ou seja, ao criar uma propriedade é possível alimentar o valor da mesma em uma outra classe.

# Modificadores de Acesso
  **TODO: COLOCAR OS OUTROS**
  * `Public`: qualquer um pode utilizar/instanciar.
  * `Private`: é permitido acessar apenas dentro da classe instanciada.
    * Fica “protegida”, ou também chamado de “encapsulamento”
  * Assinatura de um método começa depois do public

# Expression Bodied Member (EBM) em Props
* No get e no set podemos resumir a declaração e colocar body expressions, que seria o “=>” (caso temos apenas uma linha de valores)
  * No get:
    ```C#
    public string Nome { get => Nome; }
    ```
  * No set:
    ```C#
    public string Nome { get => Nome; set => Nome = value; }  
    ```
  * Quando colocamos validações em apenas um dos tipos, precisamos usar o body expressions para “chamar” a variável privada. (não é necessário fazer nada mais além disso).