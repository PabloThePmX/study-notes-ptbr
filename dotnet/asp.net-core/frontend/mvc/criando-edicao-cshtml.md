### Criando tela de edição de registro
* Ela é muito parecida com a página de adição
* Podemos até usar o mesmo html
* Teremos que alterar apenas:
  * Mudar o `form asp-action` e o `submit` para o método de Editar da controller.
* Na controller, também criar dois métodos:
  * Primeiro o editar do tipo Get, que vai retornar a view com os valores buscados pelo id recebido por parâmetro:
  ```C#
  public IActionResult Editar(int id)
  {
    //vai buscar pelo registro com esse id
    var contato = _context.Contatos.Find(id);

    //caso n existir o registro, vai mostrar que a pagina n existe
    if(contato == null)
        return NotFound();
    
    //caso existir, vai retornar a view com os valores desse registro
    //carregado na página
    return View(contato);
  }
  ```
* Ele vai carregar os campos pois vai buscar do banco, os valores daqueles itens (por isso o nome do `asp-for` precisa estar correto)
* Ao invés de chamar o NotFound, podemos redirecionar diretamente para o index, assim evita que apresente uma tela de erro (que não encontrou o registro).
* Agora, devemos criar o método que vai fazer o Post:
    ```C#
    [HttpPost]
    public IActionResult Editar(Contato contato)
    {
        //vai receber o valor que foi preenchido nos campos (como foi feito na adição)
        //em outras palavras, vai atualizar o banco com o que foi recebido pelo front

        //vai salvar o resultado da busca pelo id em uma outra variável
        var contatoBanco = _context.Contato.Find(contato.Id)

        //atualiza os campos do banco
        contatoBanco.Nome = contato.Nome;
        contatoBanco.Telefone = contato.Telefone;
        contatoBanco.Ativo = contato.Ativo;

        //faz um update e salva no banco
        _context.Contatos.Update(contatoBanco);
        _context.SaveChanges();

        //retorna para a tela de Index
        return RedirectToAction(nameof(Index));
    }
    ```