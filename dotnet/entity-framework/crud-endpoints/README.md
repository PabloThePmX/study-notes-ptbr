# CRUD Endpoints

* ### Create (Insert)
  * Criar uma propriedade privada, somente leitura do tipo do context.
  * No construtor, alimentar a propriedade com o valor da variável.
  * O método CREATE:
    ```C#
    public ContatoController(AgendaContext context)
    {
      _context = context;
    }
    ```
    * Criar o endpoint (método) do Create
    * O método ficará:
      ```C#
      //vai ser Post, pq estamos enviando uma informação
      //o contato é a entidade (classe que gera a tabela)
      [HttpPost]
      public IActionResult Create(Contato contato)
      {
        _context.Add(contato);
        _context.SaveChanges();

        //vai chamar o método do SELECT, retornando o novo id com a informação do contato, esse retorno vai ser o link do registro para ser acessado
        return CreatedAtAction(nameof(ObterPorId), new {id = contato.Id}, contato);
      }
      ```
      * No post, não precisa enviar o ID no JSON, pois ele é uma constraint, ou seja, é incrementado automaticamente quando recebe o valor no insert.
      * Ao executar, ele vai gerar o SQL do insert para executar diretamente no banco. (como aconteceu com a criação da tabela) **TODO: ACHO QUE NÃO PRECISA DISSO**

* ### Read (Select)
  * Na assinatura do método, o parâmetro a ser recebido, vai ser o valor da coluna que estamos buscando no select.
  * Vai ser um Get, e como parâmetro dele, vai ser o parâmetro que colocamos para o método.
    * Pois vamos receber pela endpoint da API, para poder ser usado no método.
  * O método SELECT:
    ```C#
    //método que vai buscar o id enviado por parâmetro no banco
    [HttpGet("{id}")]
    public IActionResult ObterPorId(int id)
    {
      //usa a config para se conectar e buscar o id no banco
      var contatoBanco = _context.Contatos.Find(id);

      //caso n exista o id enviado, retorna dizendo que não existe
      if(contato == null)
        return NotFound();

      //TODO: VER SE É ISSO O RETORNO, POIS ACHO QUE DEVERIA SER A VARIÁVEL QUE RECEBEU O FIND DO ID
      return Ok(contato);
    }
    ```
  * Outro método, que ao invés de buscar por id, ele busca pelo registro que contém a string que foi enviada por parâmetro:
    ```C#
    [HttpGet("ObterPorNome")]
    public IActionResult ObterViaNome(string nome)
    {
      //no plural, pois poderá retornar mais que 1 registro
      //vai usar LINQ para buscar todos os registros que contém a string recebida
      var contatos = _context.Contatos.Where(x => x.Nome.Contains(nome))
      return Ok(contato);
    } 
    ``` 
    * Até se caso for enviada apenas uma letra, ele busca todos os nomes que possuem aquela letra.
    
* ### Update
  * Esse método terá seu início parecido com o do Select, pois ele vai buscar o registro pelo id, porém depois, ele vai atualizar os valores das propriedades do banco com os valores que foram recebidos por parâmetro.
    * Depois de alimentar, aplicar o "commit" do update
  * Vai ser usado o método PUT.
    * Ele vai pedir pra mandar um json junto com o id.
  * O método UPDATE:
    ```C#
    [HttpPut("{id}")]
    public IActionResult Atualizar(int id, Contato contato)
    {
      //vai buscar o registro pelo id
      var contatoBanco = _context.Contatos.Find(id);

      if(contatoBanco == null)
        return NotFound();

      //vai atualizar os valores do registro, com os valores que foram recebidos por parâmetro
      //a variável contato, recebida por parâmetro, vai ser um json
      contatoBanco.Nome = contato.Nome;
      contatoBanco.Telefone = contanto.Telefone;
      contatoBanco.Ativo = contato.Ativo;

      //vai atualizar e aplicar o commit
      _context.Contatos.Update(contatoBanco);
      _context.SaveChanges()

      return Ok(contatoBanco)
    }
    ```
  * ### Delete
    * Ele vai ser como os outros, primeiro busca o registro pelo id, deleta e aplica o commit.
    * O método DELETE:
      ```C#
      [HttpDelete("{id}")]
      public IActionResult Deletar(int id)
      {
        //vai buscar o registro pelo id
        var contatoBanco = _context.Contatos.Find(id);

        if(contatoBanco == null)
          return NotFound();
        
        //vai remover e aplicar o commit
        _context.Contatos.Remove(contatoBanco);
        _context.SaveChanges();

        //vai retornar com nada, pois o registro foi deletado (código 204)
        return NoContent();
      }
      ```