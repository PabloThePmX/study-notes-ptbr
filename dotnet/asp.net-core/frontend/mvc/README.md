# MVC

### O que é
O padrão de arquitetura MVC significa Model-View-Controller. Ele separa um aplicativo em três grupos que possuem responsabilidades diferentes e que se comunicam entre si: Modelos, Exibições e Componentes.
* Model: Representa a entidade.
* View: Representa apenas a visualização, ou seja, o que o usuário vai visualizar.
* Controller: É a conexão entre a view e a model, quase como se fosse uma API.

### Criando um projeto MVC
* Na linha de comando, para criar um novo projeto colocar `dotnet new mvc`
  * A estrutura é bastante parecida com o projeto de API
* Para executar o projeto, é possível utilizar o mesmo comando realizado para a API, `dotnet watch run`

### Estrutura dos projetos MVC (rotas)
* A pasta `views/home`, tem os HTMLs das páginas.
  * Os HTMLs são no formato `CSHTML`
  * O HomeController é o controller que controla o gerenciamento das views, das páginas.
* O método do Controller, vai retornar a view
  * Ele vai ver a partir do nome qual a pasta dentro de Views ele vai buscar, Ex.: HomeController busca na pasta Home que está dentro da pasta das Views
    * Os métodos vão obedecer ao nome das páginas, ou seja, o nome precisa bater.
      * Os métodos vão ser executados quando entramos nas páginas, e como nesses métodos temos o retorno da View, ele vai retornar o código HTML da página.
  * Basicamente, ele primeiro busca a controller, e depois ve se na controller existe o método que vai chamar a página buscada.
    * E a view vai buscar por alguma que tenha o mesmo nome do método, dentro da pasta que tem o nome da controller, que está dentro da pasta das views.
* O index é um caso especial, pois ele é o pronto de entrada.
  * Assim, ele pode ser omitido ao chamar pelo link.

### Configurando o Entity Framework
* Instalar os pacotes do SQLServer e do Design
  * Vai funcionar apenas se a ferramente do EF já tenha sido instalado na máquina.
* O processo é o mesmo de qualquer outro projeto com EF, alumas possíveis diferenças (me parece diferente ao menos):
  * Vai ser necessário criar a pasta do contexto.
  * As entidades vão ser criadas na pasta Models.
* Criar a migration (**TODO: VER SE PRECISA APENAS CRIAR QUANDO A BASE N EXISTE, OU QUANDO N EXISTE NO PROJETO**)
  * Executar o comando para atualizar a database.

### Controller
* Vai herdar da classe Controller
* Importar o AspNetCore.Mvc
* Nos métodos do IActionResult, retornar a view.
  * Cada método vai ser uma página.

## Exemplos de Telas de CRUD

* ### [Criando uma lista em CSHTML](criando-lista-cshtml.md)
* ### [Criando página para adicionar um registro](criando-add-cshtml.md)
* ### [Criando página para editar um registro](criando-edicao-cshtml.md)
* ### [Criando página para visualizar um registro](criando-detalhes-cshtml.md)
* ### [Criando página para deletar um registro]