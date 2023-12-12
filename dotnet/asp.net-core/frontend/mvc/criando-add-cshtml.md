### Tela de adição de registro
* Criar um novo método na controller
* Chamar o model no cshtml
  * Dessa vez não é do tipo lista, visto que é criado um registro por vez
* Um exemplo de html que foi usado para criar o form:
    ```HTML
    <div class="row">
        <div class="col-md-4">
            <form asp-action="Criar">
                <div class="form=group">
                    <label asp-for="Nome" class="control-label"></label>
                    <input asp-for="Nome" class="form-control" />
                </div>
            </form>
        </div>
    </div>
    ```
* Cada campo será uma div diferente, que vai conter o label e o input
* Criar um campo de input para enviar os dados:
```HTML
<div class="form-group">
    <input type="submit" value="Criar" class="btn btn-primary">
</div>
```
* Agora, para criar um botão que volta para a tela anterior, devemos colocar como ação do `asp-action` o nome da tela.
    ```HTML
    <a asp-action="Index">Voltar</a>
    ```
### Criando o registro do novo contato
* Na controller, precisamos adicionar o método que vai receber os dados do input da tela de criação)por parâmetro e fazer o save.
  * Usar o mesmo nome da tela, porém com overload
  * Teremos que dizer que é um método POST
* No MVC ele coloca o método GET por padrão, por isso, como esse método vai ser POST, precisamos dizer
* O método vai ser:
    ```C#
    [HttpPost]
    public IActionResult Criar(Contato contato)
    {
        //vai ver se as informacoes recebidas sao validas (tem as informacoes obrigatorias e afins)
        if(ModelState.IsValid)
        {
            //vai adicionar e salvar
            _context.Add(contato);
            _context.SaveChanges();
            //vai ir para o metodo chamado index (que chama a tela inicial)
            return RedirectToAction(nameof(Index));
        }
        //caso n der certo, vai voltar para tela atual com os dados
        return View(contato);
    } 
    ```