### Criando tela de deletar
* Existem várias maneiras para fazer o delete de um registro.
* Geralmente, o ideal é colocar uma mensagem para que o usuário confirme que realmente deseja deletar o registro.
* O código html é muito parecido com aquele da tela de detalhes, pois só precisa visualizar os valores do registro.
* Porém, o ideal seria utilizar um form para fazer a confirmação do delete:
```HTML
<form asp-action="Deletar">
    <input type="submit" value="Deletar" class="btn btn-danger"/>
</form>
```
* O `value` no input é o nome que vai aparecer no botão.
  * Enquanto o form, com o `asp-action` é o que vai estar usando para buscar o controller, ou seja, o valor do `value` não importa para a controller.
* A controller do deletar vai ser exatamente igual ao método de detalhes, trazendo os valores do registro para o usuário.
* É necessário também, criar uma controller do tipo Post para deletar o registro.
  * Ele será muito parecido com o de editar, mudando apenas o método e retirando as alimentações.
  ```C#
  [HttpPost]
  public IActionResult Deletar(Contato contato)
  {
    var contatoBanco = _context.Contato.Find(contato.Id)

    //faz um delete e salva a alteração no banco
    _context.Contatos.Remove(contatoBanco);
    _context.SaveChanges();

    //retorna para a tela de Index
    return RedirectToAction(nameof(Index));
  } 
  ```
* 