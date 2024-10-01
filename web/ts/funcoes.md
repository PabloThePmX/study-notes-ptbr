# Funções
* Tipar os parâmetros `function addNumber(x: number, y: number){}`
* Tipar o retorno `function addNumber(x: number, y: number) : number{}`
  * Implicitamente, ele vai tipar o método conforme o tipo do valor retornado.
* Podemos usar multi-tipo para o retorno ou o tipo do parâmetro:
  * `function Teste(phone: string | numer) : string | null {}`
* Função assíncrona é usada para "esperar" alguma outra coisa para poder continuar.
  * Para tipar esse tipo de função `async function GetDatabase(id: number) : Promise<string | number> {}`
    * Async retorna sempre `Promise`.
* O keyword `function` pode ficar implícito.