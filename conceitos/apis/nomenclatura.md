# Nomenclatura de APIs

* Devem ser substantivos no plural.
  * Pois estamos tratando de uma coleção daqueles dados.
  * Até mesmo quando for um `post`, pois estaremos adicionando algo naquela coleção.
* Não deve ser utilizado verbo, pois isso estará explicito no tipo da requisição (`get`, `post`, etc).
* Evitar abreviações.
  * Alguns são aceitáveis, como ids.
* O `/` é usado para determinar a hierarquia.
  * Ex: `/users/123/first-name` está pegando o primeiro nome do usuário 123.
* Separar palavras com `hifens`.
* Sempre usar `lowercase`.
  * Isso é estabelecido em um padrão URI.

### Em ASP.NET
* Os métodos do controller terão o verbo, e seguirão o padrão de nomes de qualquer outro método.
  * Porém a chamada será feita diretamente com o nome do controller, ou seja, `Services`, vai ter o `GetService` e o `GetServicesById`, sendo ambos `GET`, porém um recebe parâmetro é o outro não. Portanto, a chamada de cada um deles vai ser: `/api/service` e `api/service/{id}`, ou seja, ambos são diferenciados não pelo nome, mas pelo seu parâmetro.
  * O nome dos métodos não serão os caminhos dos endpoints (url).
    * No geral, o controller vai seguir o mesmo padrão de nomenclatura de classes do C#, nomes em PascalCase.

https://learn.microsoft.com/en-us/aspnet/core/web-api/advanced/conventions?view=aspnetcore-8.0