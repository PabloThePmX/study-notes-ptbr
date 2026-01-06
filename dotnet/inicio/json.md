# Trabalhando com JSONs

* Usar a classe `File` para criar um arquivo JSON (usar o método `WriteAllText()`) e enviar o JSON criado para salvar o conteúdo nele.
* A ISO 8601 padroniza a representação de datas entre sistemas
  * Por isso fica em um formato "estranho" ao passar DateTime para o JSON.
* Ao ler um JSON, cada um dos seus atributos serão uma propriedade (`get`, `set`) de uma classe.
* Se o JSON possuir uma coleção, devemos declarar uma lista do tipo da classe que possui as props dessa lista.
* Usar o método `DeserializeObject()` do `JsonConvert` para alimentar essa lista criada (chamar a lista no método, e nele como parâmetro será passada a leitura completa do JSON pega com o método `ReadAllText` do `File`).
* Depois será possível ler essa coleção do JSON com o tipo da classe como se fosse uma lista normal.
* Quando não queremos que uma propriedade no C# precise usar o nome que há definido na propriedade no JSON, podemos usar um atributo.
  * Logo na linha de cima da propriedade no C# que queremos alterar, podemos usar o método `[JsonProperty("<nome do atributo no json>")]`, e assim, é possível dar qualquer nome a propriedade pois a mesma "pega" o valor que foi injetado por esse método `JsonProperty`.
  * Esse atributo é um metadata, ou seja, ele está adicionando uma informação adicional para a propriedade no C#. (Basicamente uma instrução que diz para pegar aquele valor específico)
