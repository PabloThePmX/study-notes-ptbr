### Criando página de detalhes
* É apenas um display das informações.
* Criar uma tela, com model também (como os outros)
* Para o display:
 ```HTML
 <div>
    <dl class="row">
        <dt class="col-sm-2">
            @Html.DisplayNameFor(x => x.Nome)
        </dt>
        <dt class="col-sm-10">
            @Html.DisplayFor(x => x.Nome)
        </dt>
    </dl>
 </div>
 <a asp-action="Editar" asp-route-id="@Model.Id">Editar</a>
 <a asp-action="Index">Voltar</a>
 ```
 * A tag `<dl>` significa definition list.
 * Como foi na lista, precismos colocar o `DisplayNameFor` para colocar a legenda (label), e o `DisplayFor`, para colocar o valor.
   * Repetir isso para todas as colunas do banco.
 * O `asp-route-id` é para enviar o valor do id pela rota.
 * Para o controller:
    ```C#
    public IActionResult Detalhes(int id)
    {   
        //busca o registro pelo ID
        var contato = _context.Contatos.Find(id);

        //se n encontra, volta pra pagina de index (teoricamente, n faz nada)
        if(contato == null)
            return RedirectToAction(nameof(Index));
        
        return View(contato);
    }
    ```
* 