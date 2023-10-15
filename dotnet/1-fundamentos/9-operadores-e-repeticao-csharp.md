# Operadores e Estuturas de Repetição C#

* Com o operador lógico dentro do `WriteLine`, podemos mostrar os valores de condições diretamente.
* No VSCode da pra rodar o debug (canto esquerdo).
* No C# temos `else if`.
* Usar `Console.ReadLine()` para ler o que veio de input do usuário no console.
* A sintaxe do switch:
    ```C#
    //colocar a condição, e depois colocar os resultados no case
    int i = 2;
    switch (i) 
    {
        case 1: 
            //colocado o break para ele não executar mais o resto do switch
            break;
        case 2:
            //código (esse que vai ser executado nesse caso)
            break;
        default
            //código caso n entre em nenhuma condição
            break;
    }
    ```
    * O switch vai observar o valor da variável
* Operadores Lógicos
    * OR - `||`
    * AND - `&&`
    * NOT - `!`
* O módulo `%` vai retornar o resto de uma divisão
* A sintaxe do `for` é:
    ```C#
    //inicio contador; limite contador; incrementação contador
    for(int i = 0; i < valor.Length; i++)
    ```
* Já a sintaxe do `while` só é preciso colocar a condição do limite (“limite cont”), ou seja sempre que a condição for verdadeira.
    * Ele vai precisar ter o contador incrementado dentro do while, que vai ser incrementado depois de fazer o que queremos dentro do while.
    * Possível usar o “break” para fazer o while parar.
* O `Do While` vai primeiro fazer o laço e ao final vai verificar se a condição ainda é verdadeira ou não
    * A sintaxe do `Do While`: 
    ```C#
    //executa o código, enquanto i for menor ou igual a 5
    int i = 0;
    Do {
        i++;
    } while(i <= 5)
    ```
* Possível declarar várias variáveis do mesmo tipo numa única linha.
  ```C#
  //declarar com ou sem valores
  int i, j, k;
  int l = 10, m = 20, n = 30;
  ```
* No VSCode não é possível debugar usando o terminal (Console.ReadLine não funciona por exemplo)
    * No launch.json, alterar o console para “integratedTerminal”
    * Ao invés de usar o debug console, usar o terminal durante a debugação
* Usar `While(true)` para sempre ficar rodando
    * Para sair repentinamente, podemos usar `Environment.Exit(0)`
        * Isso termina com o programa inteiro.
    * Podemos fazer meenus no console, usando o laço de repetição dessa forma.

### Classe Math

* Declarar essa classe para ter vários tipos de operções
    * Como Log, potência, etc.
* Ela também tem as funções trigonométricas (seno, cosseno, tangente, etc)
    * A mesma tem o pi, para ser usada no cálculo para transformar o ângulo em radianos.
    * O método round vai arredondar os valores, nele é possível dizer quantas casas deve ser mostrado depois da vírgula
* Usar o método sqrt dela para calcular a raiz quadrada.
