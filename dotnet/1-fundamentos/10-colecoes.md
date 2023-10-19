# Coleções

### Array 
* Um array trabalha apenas com valores do mesmo tipo
* Para declarar um array: 
  ```C#
  //pode ser declarado de qualquer uma dessas maneiras
  int[] var = new int[] {valores}
  int[] var = new int[tamanho]
  int[] var = {valores}
  ```
* O índice é a posição de um elemento
  * No C# começa no 0.
* Usar o `.length` no array para ler todos os seus valores
  * Quando for lido usando o comando “for”
* Possível usar o “foreach” para ler a coleção
  * A sintaxe para isso: “foreach(int value in valuesCollection)”
  * A desvantagem é que ele não tem contador como no “for”
    * Porém da pra colocar um contador “manual”, que é incrementado dentro do código
* Usar o “for” quando precisa controlar o contador, e o “foreach” quando não precisa.
* Para mudar o tamanho do array em runtime:
  * “Array.Resize(ref array, novo tamanho)”
    * Um exemplo para dobrar o tamanho da coleção “arrayValues”: “Array.Resize(ref arrayValues, arrayValues.length*2)”
  * Esse resize tecnicamente cria um novo array, copiando os elementos antigos para o novo array.
* Passar uma variável por referência (ref) significa que você não vai passar o valor dela, e sim o seu endereço de memória.
* Usar o “Array.Copy()” para copiar valores de um array para outro.
  * O último parâmetro é a quantidade de números a serem copiados, e se for o total da coleção, o jeito mais prático é usar o length
  
### List
* Uma lista pode ser mais fácil que um array
  * Lista não precisa ter capacidade máxima definida anteriormente como o array
  * Tentar sempre usar a lista quando possível por ser menos complexa
* Sintaxe de lista:
    ```C#
    List<string> listaString = new List<string>()
    ```
* Usar o método `Add` para adicionar os itens 1 por 1, ou AddRange para botar vários.
* Dá pra percorrer a lista como o array
  * Porém no “for” não usar “length” e sim “count”
* Uma grande diferença da lista para o array são os seus métodos mais variados
  * Internamente uma lista é um array também
