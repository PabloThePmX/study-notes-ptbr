# Operadores e Estuturas de Repetição C#

* Com o operador lógico dentro do `WriteLine`, podemos mostrar os valores de condições diretamente.
* No VSCode da pra rodar o debug (canto esquerdo)
* No C temos `else if`
* Usar `Console.ReadLine()` para ler o que veio de input do usuário no console.
* A sintaxe do switch pode ser “switch (var) {case “valor”: break}”
    * O switch vai observar o valor da variável
    * Tem a condição default também
* Operadores Lógicos
    * OR - `||`
    * AND - `&&`
    * NOT - `!`
* O módulo “%” vai retornar o resto de uma divisão
* Dentro da classe Math temos vários tipos de operações
    * Como Log, potência, etc.
* A classe Math também tem as funções trigonométricas (seno, cosseno, tangente, etc)
    * A mesma tem o pi, para ser usada no cálculo para transformar o ângulo em radianos.
    * O método round da classe Math vai arredondar os valores, nele é possível dizer quantas casas deve ser mostrado depois da vírgula
* Usar o método sqrt da classe Math para calcular a raiz quadrada.
* A sintaxe do `for` é:
    ```C#
    //inicio contador; limite contador; incrementação contador
    for(int i = 0; i < valor.Length; i++)
    ```
* Já a sintaxe do `while` só é preciso colocar a condição do limite (“limite cont”), ou seja sempre que a condição for verdadeira.
    * Ele vai precisar ter o contador incrementado dentro do while, que vai ser incrementado depois de fazer o que queremos dentro do while.
    * Possível usar o “break” para fazer o while parar.
* O “Do While” vai primeiro fazer o laço e ao final vai verificar se a condição ainda é verdadeira ou não
    * A sintaxe: “Do {} while()”
* Possível declarar várias variáveis do mesmo tipo numa única linha.
* No VSCode não é possível debugar usando o terminal (Console.ReadLine não funciona por exemplo)
    * No launch.json, alterar o console para “integratedTerminal”
    * Ao invés de usar o debug console, usar o terminal durante a debugação
* Usar “While(true)” para sempre ficar rodando
    * Para sair repentinamente, podemos usar “Environment.Exit(0)”
        * Isso termina com o programa inteiro
    * No exemplo, isso foi usado para fazer um menu
        * Depois foi usada uma flag para fazer isso
