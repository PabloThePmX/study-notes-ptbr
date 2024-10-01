### Listagem em HTML
* Declarar uma lista da model.
* Primeiramente, devemos declarar a nossa model 
  ````C#
  //aqui está pegando a entidade Contato presente no projeto "ProjetoMVC" como lista
  @model IEnumerable<ProjetoMVC.Models.Contato>
  ```
* Usar o `@` para dizer que vamos implementar algo em C#.
* Para alterar o título da página na aba do navegador:
  ```C#
  @{
    ViewData["Title"] = "Listagem de Contatos";
  }
  ```
* Para fazer o redirecionamento de algo, colocar o asp-action:
```HTML
<a asp-action="Criar">Novo Contato</a>
```
* Agora em HTML, para criar a tabela:
```HTML
<table class="table">
  <thead>
    <tr>
      <th>
        @Html.DisplayNameFor(model => model.Id)
      </th>
      <th>
        @Html.DisplayNameFor(model => model.Nome)
      </th>
      <th>
        @Html.DisplayNameFor(model => model.Telefone)
      </th>
      <th>
        @Html.DisplayNameFor(model => model.Ativo)
      </th>
    </tr>
  </thead>
  <tbody>
    @foreach(var item in Model){
      <tr>
        <td>
          @Html.DisplayFor(model => item.Id)
        </td>
         <td>
          @Html.DisplayFor(model => item.Nome)
        </td>
         <td>
          @Html.DisplayFor(model => item.Telefone)
        </td>
         <td>
          @Html.DisplayFor(model => item.Ativo)
        </td>
         <td>
          <a asp-action="Editar" asp-route-id="@item.Id">Editar</a> |
          <a asp-action="Detalhes" asp-route-id="@item.Id">Detalhes</a> |
          <a asp-action="Deletar" asp-route-id="@item.Id">Deletar</a>
        </td>
      </tr>
    }
  </tbody>
</table>
```
* Cada header, é uma propriedade que foi definida na model
* No body, estaremos lendo o Model que foi declarado na tela (por isso ele está como Model e não model)
  * Nesse body, iremos ler cada registro desse model, e alimentar na table data `<td>`
* As tags de ancoras, são os botões que vão ir na tabela, eles vão ter a ação, e o valor do registro que vai enviar pela rótula, que no caso seria a PK, o ID.
  * No código usa o `|` somente para fazer a separação esteticamente.
* Usar`@` no id da rota, para que fique dinâmico 
* Agora na controller:
  * Colocar o context
  * No index (que é onde terá a lista):
    * Alimentar uma variável com o nome da tabela (fica no plural), com o valor da tabela do contexto no formato de lista, e depois retornar essa variável pra view.
    ```C#
    public IActionResult Index()
    {
      //context é a variável privada da propriedade do tipo do contexto.
      var contatos = _context.Contatos.ToList();
      return View(contatos);
    }
    ```
* Caso apresente um erro ao rodar esse código (se estiver usando o watch), executar o projeto novamente.