# Conceitos Iniciais para o Projeto

### Abstração
* A abstração seria pegar um objeto do mundo real para transformá-lo em um objeto na programação.
  * Uma classe é um conceito representado do mundo real.
* Abstrair somente o necessário, o que será usado de fato.

### Classe e Métodos
* Um método é uma ação que a classe vai fazer (ele tem parênteses no final).
* Uma classe tem os atributos e então os métodos, nessa ordem.
* Todo o nome de classe deve iniciar com maiúscula.
* O namespace é uma organização de classes.
  * Ao utilizar o namespace, é bom colocar com várias divisões (Ex.: Models.Conta.BancoSicredi, Models.Conta.BancoMafra)
* O atalho “Prop” é propriedade
  * A propriedade são as características da abstração, as variáveis por exemplo.
* Usar o “$” na frente de uma string para utilizar variáveis dentro da mensagem com “{var}”.
* O get e o set existem na declaração para definir que a variável pode ser armazenada e usada.
* Método e função são a mesma coisa, porém no C# é mais comum escutar método.
* É possível usar uma palavra reservada colocando um “@” na frente. (Melhor não usar)
* O Program.cs é o início do sistema.
* Para pegar um classe de outro namespace:
  * Colocar o using com o namespace da classe
  * Depois instanciar com: 
    ```C# 
    <NomeClasse> <nome var> = new <NomeClasse>() 
    ```
* Podemos ter classes com nomes iguais, porém os namespaces devem ser diferentes
* Quando for instanciada a classe, o “new” irá dizer que aquela classe já foi feita (executada) e pode ser usada e alimentada como uma variável normal.
* Evitar abreviações (convenção), para deixar mais claro o código.
* O nome do arquivo deve ser o mesmo da classe (convenção).

### Padrões de escritas (cases):
* camelCase: para variáveis
* PascalCase: para nomes de classes, métodos, propriedades
* snake_case 
* spinal-case
* O camelCase e PascalCase são os mais usando em C#.

