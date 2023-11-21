# Entity Framework

### O que é
É uma framework ORM (Object Relational Mapping) criado para facilitar a integração com o BD, mapeando as tabelas, gerando comandos SQL automaticamente, etc. O EF estará presente na camada chamada de Data Layer, que é a mais próxima do BD. Com ele, o usuário não precisa colocar o comando SQL manualmente para cada ação que necessita interação com o BD.
* Ele consegue mapear as tabelas do banco.
* Ele vai reconhecer as alterações feitas na tabela via código C#.
  * Ele cria a tabela automaticamente baseando-se na classe e suas propriedades.
* Tem tanto para .NET Framework, quanto para o Core.
**TODO: COLOCAR IMAGEM**

**TODO: TOPICOS**
# Como Usar

# Criando os Endpoints

### Como Usar

* ### Instalando
  * Primeiramente, sera preciso instalar a ferramenta do Entity Framework
    * Para isso, executar o comando `dotnet tool install --global dotnet-ef` no terminal
    * Ele **NÃO** instala somente para o projeto, ao instalar, ele estará automaticamente disponível em outros projetos, ele está a nível global, nível de máquina.
  * Logo após isso, devemos instalar os pacotes do EF
    * Para isso, podemos executar os comandos `dotnet add package Microsoft.EntityFrameworkCore.Design`, `dotnet add package Microsoft.EntityFrameworkCore.SqlServer`
      * A nível de projeto, ou seja, são pacotes como qualquer outro do nuget.
      * Se for para utilizar em outro banco, será necessário que instalar o pacote do respectivo banco.
  
* ### Criando a Classe Entidade
  * Criar uma classe dentro de uma pasta chamada de `Entities` (com esse nome, para dizer que tudo que tem dentro dessa pasta se refere a tabelas do banco).
    * O nome entidade refere-se a uma tabela que além de estar no banco, também é uma classe.
  * As propriedades adicionadas nessa classe, serão criadas como colunas no banco pelo EF.
    * Dessa maneira, devemos colocar uma prop que vai ser o nosso ID (a PK da tabela).
  
* ### Criando o Contexto
  * Criar uma pasta chamada `Context` e criar uma classe com o nome do BD + Context, ex.: `AgendaContext`
  * Dentro dessa classe, primeiramente precisaremos buscar os métodos da classe `DbContext`, para isso herdamos do mesmo (devemos fazer a importação do pacote do EF).
  ```C#
  using Microsoft.EntityFrameworkCore;

  namespace ModuloTesteEntity.Context
  {
    public class AgendaContext : DbContext
    {

    } 
  }
  ```
  * Após isso, precisamos criar um construtor, para colocar a conexão com o banco de dados (isso será configurado no tópico de configuração de conexão).
    * Ao fazer isso, a conexão vai ser enviada para o `DbContext` via construtor, e é no DbContext que vai ser realizada a conexão com o banco.
  ```C#
  //vai receber a conexão do banco e vai passar para o base (que é a classe pai, a classe que está herdando)
  public AgendaContext(DbContextOptions<AgendaContext> options) : base(options)
  {

  }
  ```
  * Agora, criar uma propriedade com o tipo da classe `Entities`, que vai estar se referindo a uma tabela no banco.
  ```C#
  //criando uma prop da tabela Contato
  //devemos criar a prop para a tabela que queremos nos conectar
  public DbSet<Contato> Contatos {get; set; }
  ```

* ### Configurando a Conexão
  * Há o `appsettings.Development` e o `appsettings`, um deles é as configs para o desenvolvimento, e o outro para a produção, tudo que seja configuração, será colocado nesses arquivos.
    * Vai ser neles que vamos colocar a conexão com o banco.
  * Como estamos testando no desenvolvimento, no `appsettings.Development`, logo após as configurações padrão (Logging) colocar o **Connection String** (botar uma `,` para separar as chaves no JSON):
    ```JSON
    "ConnectionStrings" : {
      //nome que iremos dar para conexão, o ip do banco (nesse caso, sql server express), o nome do banco de dados e que há autenticação para esse bd (se tiver usuário e senha, precisa passar nessa string)
      "ConexaoPadrao": "Server=localhost\\sqlexpress; Initial Catalog=Agenda; Integrated Security=True"
    }
    ```
  * Então, precisamos configurar o context para saber que ele vai usar essa string de conexão:
    * No `Program.cs`, importar o conetext e o EF
      * Onde consta o `Add Services` (é bom colocar essa conexão bem no início do código, pois quando ele for dar o Run, já tem que estar configurado), colocar:
          ```C#
          //colocar o nome do arquivo de contexto e o nome da conexão que foi criada no appsettings
          builder.Services.AddDbContext<AgendaContext>(options => 
              options.UseSqlServer(builder.Configuration.GetConnectionString("ConexaoPadrao")));
          ```
          * O código diz basicamente pra ele adicionar um DbContext do tipo AgendaContext e passando as opções.
            * Dizendo para o contexto que criamos (nesse caso a agenda) qual vai ser o banco que vai ser usado e qual a configuração de conexão (ConnectionString) que vai ser usada (nesse caso, a "ConexaoPadrao").

* ### Migrations
  * É um mapeamento que o EF faz para transformar as classes em tabelas.
  * O BD deve estar rodando
  * No terminal rodar:
    * `dotnet-ef migrations add CriacaoTabelaContato`, esse valor no final, é o nome que vamos dar para a migration, é bom ter um nome que faça ajudar a saber o que é
      * Ele cria uma pasta para a migration, com as migrations feitas
  * Depois de rodar, as classes criadas tem dois métodos, o Up e o Down
    * Up: Cria a tabela
    * Down: Faz um rollback, dando um drop na tabela
  * No C# colocamos as classes no nome singular, no banco colocamos no plural **TODO: MUDAR ISSO E COLOCAR EM OUTRO LUGAR**
    * Com o EF, ele cria automaticamente no plural, propriedade `name` no `CreateTable`
  * Agora, com a migration criada, rodar o comando `dotnet-ef database update` para "aplicar" essas migrations no banco.
    * Ele vai criar o comando SQL e rodar ele no BD.

### Criando a Controller para o EF
* Criar na pasta da controller como as outras
* Colocar a ApiController e a Route também, com as importações necessárias, e herdar da ControllerBase também

### Endpoints CRUD

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
        return Ok(contato);
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

      return Ok(contato);
    }
    ```
    
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