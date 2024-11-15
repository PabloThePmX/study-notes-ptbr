# Entity Framework

### O que é
É uma framework ORM (Object Relational Mapping) criado para facilitar a integração com o BD, mapeando as tabelas, gerando comandos SQL automaticamente, etc. O EF estará presente na camada chamada de Data Layer, que é a mais próxima do BD. Com ele, o usuário não precisa colocar o comando SQL manualmente para cada ação que necessita interação com o BD.
* Ele consegue mapear as tabelas do banco.
* Ele vai reconhecer as alterações feitas na tabela via código C#.
  * Ele cria a tabela automaticamente baseando-se na classe e suas propriedades.
* Tem tanto para .NET Framework, quanto para o Core.
**TODO: COLOCAR IMAGEM**

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
      * O nome vai ser singular, pois o EF cria o nome no plural dentro do BD, propriedade `name` no `CreateTable` da migration.
  * As propriedades adicionadas nessa classe, serão criadas como colunas no banco pelo EF.
    * Dessa maneira, devemos colocar uma prop que vai ser o nosso ID (a PK da tabela).
  * Caso existir colunas que irão se repetir em várias entidades, existe a possibilidade de criar uma classe contendo apenas elas, e depois herdar o que foi colocado nessa classe pai (princípio de encapsulamento).
    * Um exemplo seria colocar o Id na classe pai, e todas as filhas que herdarem dela, já teriam a propriedade Id.
  
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
  * Agora, criar uma propriedade com o tipo da classe criada em `Entities`, que vai estar se referindo a uma tabela no banco.
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
      "ConexaoPadrao": "Server=localhost\\sqlexpress; Initial Catalog=Agenda; Integrated Security=True"
    }
    ```
    * Resumindo a sintaxe: Nome que iremos dar para conexão, o ip do banco (nesse caso, sql server express), o nome do banco de dados  e que há autenticação para esse bd (se tiver usuário e senha, precisa passar nessa string)
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

* ### Migrations (**TODO: TALVEZ ESTUDAR MAIS SOBRE O QUE É**)
  * É um mapeamento que o EF faz para transformar as classes em tabelas.
  * O BD deve estar rodando
  * No terminal rodar:
    * `dotnet-ef migrations add CriacaoTabelaContato`, esse valor no final, é o nome que vamos dar para a migration, é bom ter um nome que faça ajudar a saber o que é
      * Ele cria uma pasta para a migration, com as migrations feitas
  * Depois de rodar, as classes criadas tem dois métodos, o Up e o Down
    * Up: Cria a tabela
    * Down: Faz um rollback, dando um drop na tabela
  * Agora, com a migration criada, rodar o comando `dotnet-ef database update` para "aplicar" essas migrations no banco.
    * Ele vai criar o comando SQL e rodar ele no BD.
  * Toda vez que queremos mudar algo do banco, precisamos criar uma migration nova e rodar o update no banco.

### Criando a Controller para o EF
* Criar na pasta da controller como as outras
* Colocar a ApiController e a Route também, com as importações necessárias, e herdar da ControllerBase também.
* **TODO: O QUE É INJEÇÃO DE DEPENDÊNCIA?**


### Relations
* Usar a navegação (colocar o objeto da FK na entidade) nas relações é o equivalente ao usar `JOIN` no banco.
  * Não é obrigatório ter navegação, porém, isso vai aumentar a complexidade, e o mesmo query que seria feito com `JOIN` vai ser feito com vários `SELECT` e `WHERE`