# Tipos de Variáveis

### Numéricos
* No C# podemos usar o tipo char para representar UM caractere.
* O byte vai de 0 até 255 numérico.
* uint, short, ulong e long são variações do **int** (o int é 32bits, que é bilhões)
  * uint e ulong não têm negativos, por esse motivo os valores podem ser maiores (o dobro)
* decimal, double e float são valores com decimais.
  * decimal é geralmente usado para valores monetários
* **long**, **int**, **decimal** e **double** são os numéricos mais usados.
* Casas decimais separadas por ponto.
* Ao alimentar um valor decimal diretamente, é preciso colocar um “M” no final do valor.
* O double é melhor não utilizar para casas decimais, pois ele ignora o último zero.
  * Valores monetários SEMPRE representar com decimal

### Data
* DateTime é o tipo de variável de tempo
  * DateTime também é um “struct” (DateTime.Now), é possível adicionar valores nesse método também.
  * Possível usar `ToString()` para mudar a formatação da data

## Declaração
* Para declarar uma variável, colocamos o tipo, o nome da variável, e o valor inicial dela:
  ```C#
    int i = 0;
    bool ehUmTeste = false
    string variavelTexto = ""
  ```
* É também possível declarar várias variáveis do mesmo tipo numa única linha.
  ```C#
  //declarar com ou sem valores
  int i, j, k;
  int l = 10, m = 20, n = 30;
  ```

# Conversão de Variáveis
* Para converter o tipo da variável é necessário fazer um “cast”
  * Usar a classe `Convert` (usar diretamente no valor) (preferível pelo tratamento dos valores nulos)
  * Possível também usar `tipo.Parse()` para fazer o cast no valor, porém ele não existe para tipos string
  * A diferença deles é sobre os valores nulos.
    * Alterar o "tipo" para algum dos tipos de variável que queremos transformar.
    * O convert funciona com valores nulos (transforma em 0 por exemplo)
    * O parse apresenta uma exceção quando receber nulo
      * A exceção vai, obviamente, parar toda a execução.
* Usar `ToString()` para transformar em string.
  * Esse método é herdado do object, por isso todos os tipos tem esse método.
* O cast implícito é uma conversão que é feita automaticamente.
  * Um exemplo é de int para double, apenas necessário declarar
  * Funciona quando o valor “cabe” no tipo
* Possível converter os tipos usando o `TryParse`, pois ele possui tratamento de erros, caso for tentada uma conversão inválida, o mesmo retorna 0.
  * Preciso usar ele como método retornando um valor, colocando o “out” nessa variável de retorno.

# Padrões de escritas (cases):
* Dentro das linguagens de programação, temos padrões de escrita seguidos para nomear as nossas variáveis, classes, etc
* Dentre eles temos:  
  * `camelCase`
    * Variáveis
  * `PascalCase` 
    * Nomes de classes, métodos, propriedades
  * `snake_case` 
  * `spinal-case` 
* O camelCase e PascalCase são os mais usando em C#.

# Operadores e Estruturas de Repetição em C#

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
    * Possível usar o `break` para fazer o while parar.
* O `do while` vai primeiro fazer o laço e ao final vai verificar se a condição ainda é verdadeira ou não
    * A sintaxe do `do while`: 
    ```C#
    //executa o código, enquanto i for menor ou igual a 5
    int i = 0;
    do {
        i++;
    } while(i <= 5);
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
* Usar `while(true)` para sempre ficar rodando
    * Para sair repentinamente, podemos usar `Environment.Exit(0)`
        * Isso termina com o programa inteiro.
    * Podemos fazer menus no console, usando o laço de repetição dessa forma.

# Coleções

* Coleções de tipos que podem ser lidas a partir de um laço de repetição.

### Array 
* Um array trabalha apenas com valores do mesmo tipo
* Para declarar um array: 
  ```C#
  //pode ser declarado de qualquer uma dessas maneiras
  //no {} coloca valores
  //no [] coloca o tamanho
  int[] var = new int[] {1,2,3,4};
  //são 3 valores, porém o índice começa no 0
  int[] var = new int[3];
  int[] var = {5,6,7,8};
  ```
* O índice é a posição de um elemento
  * No C#, ele começa no 0.
* Usar o `Length` no array para ler todos os seus valores
  * Quando for lido usando o comando “for”
* Possível usar o `foreach` para ler a coleção
  * A sintaxe para isso: 
  ```C#
  //da pra usar "var" como tipo de variável, pois ai n importa o tipo da coleção
  foreach(int value in valuesCollection)
  ```
  * A desvantagem é que ele não tem contador como no `for`
    * Porém da pra colocar um contador “manual”, que é incrementado dentro do código
* Usar o `for` quando precisa controlar o contador, e o `foreach` quando não precisa.
* Para mudar o tamanho do array em runtime:
  ```C#
  //faz um resize do array, recebendo a referência do array antigo e dobrando o tamanho dele
  //o array ajustado é o mesmo que foi enviado (myArr)
  Array.Resize(ref myArr, myArr.Length*2)
  ```
  * Esse resize tecnicamente cria um novo array, copiando os elementos antigos para o novo array.
* Passar uma variável por referência (ref) significa que você não vai passar o valor dela, e sim o seu endereço de memória.
* Usar o `Array.Copy()` para copiar valores de um array para outro.
  * O último parâmetro é a quantidade de números a serem copiados, e se for o total da coleção, o jeito mais prático é usar o length
  
### Lista
* Uma lista pode ser mais fácil que um array
  * Lista não precisa ter capacidade máxima definida anteriormente como o array
  * Tentar sempre usar a lista quando possível por ser menos complexa
* Sintaxe de lista:
    ```C#
    //dentro do <> da list, vai ser o tipo (que além dos tipos normais, pode ser uma classe também)
    List<string> listaString = new List<string>()
    ```
* Usar o método `Add` para adicionar os itens 1 por 1, ou `AddRange` para botar vários.
* Dá pra percorrer a lista como o array
  * Porém no `for` não usar `length` e sim `count`
* Uma grande diferença da lista para o array são os seus métodos mais variados
  * Internamente uma lista é um array também
* O `Remove` e `Add` de uma lista podem retornar booleanos de sucesso ou não.

# Comentários

* O comentário `<summary>` permite documentar classes, métodos, parâmetros, etc.
  * Aparece ao passar o mouse
  * Nas settings do VSCode, se habilitar a opção “Format on type”, ao escrever “///” já será colocado o summary
  * Precisa fechar a tag com o `</summary>`
  * Colocar logo em cima da classe, método que vai ser explicado
  * Quando tem parâmetros, precisa colocar `<param name=”var”>` (e fechar) para dizer o significado de cada parâmetro.
  * A tag `<returns>` vai dizer o que é o valor retornado
* Comentários não são compilados.
* Se algo é simples de entender, não precisa de comentário para poluir tanto.
* Às vezes ao invés de comentar, ver se não é possível deixar os nomes das variáveis, métodos, etc mais claros para entender.
