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
  * Possível usar `ToString` para mudar a formatação da data

### Conversões
* Para converter o tipo da variável é necessário fazer um “cast”
  * Usar a classe `Convert` (usar diretamente no valor) (preferível pelo tratamento dos valores nulos)
  * Possível também usar `tipo.Parse()` para fazer o cast no valor, porém ele não existe para tipos string
  * A diferença deles é sobre os valores nulos.
    * Alterar o "tipo" para algum dos tipos de variável que queremos transformar.
    * O convert funciona com valores nulos (transforma em 0 por exemplo)
    * O parse apresenta uma exceção quando receber nulo
      * A exeção vai, obviamente, parar toda a execução.
* Usar `ToString()` para transformar em string.
  * Esse método é herdado do object, por isso todos os tipos tem esse método.
* O cast implícito é uma conversão que é feita automaticamente.
  * Um exemplo é de int para double, apenas necessário declarar
  * Funciona quando o valor “cabe” no tipo
* Possível converter os tipos usando o `TryParse`, pois ele possui tratamento de erros, caso for tentada uma conversão inválida, o mesmo retorna 0.
  * Preciso usar ele como método retornando um valor, colocando o “out” nessa variável de retorno.
