# Tipos de Dados
* Possível declarar a variável como qualquer um desses tipos.
* **Primitivos**
  * `boolean`
  * `number` (com ou sem decimal).
  * `string`
  * Para tipar as variáveis: `let ligado:boolean = false`.
* **Tipos especiais**:
  * `null`
  * `undefined`
* **Tipos abrangentes**:
  * `any`, aceita qualquer valor
    * Usado para valores imprevisíveis, ou seja, quando não sabemos exatamente o que vai ser retornado.
  * `void`, quando a função não retorna nada
* **Tipo object**
  * A variável precisa usar as `{}`, pois é um objeto em si.
  * Porém não é recomendado pois nunca sabemos como vai ser o objeto em si, para isso, devemos tipar exatamente o jeito que a struct do objeto é formado:
    * Criar um tipo com `type ProdutoLoja {nome: string; preco: number; unidades: number; }`
      * Assim, ao declarar a variável, usamos o tipo desse objeto `let meuProduto: ProdutoLoja = {nome: "Tênis", preco: 99, unidades: 5}`
        * Dessa forma, caso alguma dessas propriedades seja omitida, vai acusar um erro, por não estar respeitando o tipo.
* **Arrays**:
  * Temos duas maneiras para declara-lo:
    * `let dados: string[] = ["nome1", "nome2"]`
    * `let dados2: Array<string> = ["nome1", "nome2"]`
  * Podemos declarar arrays com múltiplos tipos (usar o OR):
    * `let infos: (string | number)[] = ["Pablo", 24]`
      * Porém é melhor criar um objeto ao invés de fazer dessa forma.
* **Tuplas**
  * É um vetor multi-tipo com uma ordem exata.
  * Para declarar, colocamos a ordem dos tipos, como `let boleto:[string, number, number] = ["conta água", 190.90, 1234556]`
    * Ou seja, o tipo vai ser a ordem desses tipos.
* **Datas**
  * É uma interface do tipo `Date`.
  * Usa-se o padrão "ao contrário"
  * Para declarar `let aniversario:date = new Date("2000-03-01 04:00")`
    * O `Date` pede horário também.