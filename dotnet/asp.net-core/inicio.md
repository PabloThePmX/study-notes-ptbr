# Criando uma API no .NET

* No CMD, para criar um projeto de api: `dotnet new webapi`
  * Para executar a API: `dotnet watch run` **TODO: COLOCAR ISSO NO TOPICO DE CMD**
    * O watch fica observando os arquivos da API, e caso ele detectar uma alteração, ele vai compilar novamente.
    * Quando colocar um arquivo novo, precisa fazer um restart da aplicação.
* Em um projeto do tipo API, o .NET cria automaticamente um frontend chamado de Swagger UI, usado para facilitar o teste das APIs.
  * Da pra colocar a documentação da API nele. (**TODO: VER MAIS SOBRE ISSO**)
  * É opcional.
  * Ele é atualizado de acordo com os controllers que criamos.
  * Clicar primeiro em "Try it out" para habilitar o uso da API no swagger.

## Controller
* É uma classe que vai agrupar as requisições HTTP
  * Ela vai ser um agrupamento de ações em comum, por exemplo: UsuarioController, ComprasController, ProdudoController, etc.
    * Dentro de cada uma dessas controllers, teremos agrupado as ações/métodos específicos de cada uma delas.
* Criar os arquivos dentro da pasta Controller, e por convenção, colocar o nome "Controller" no final do nome da classe.
* Ela herda de ControllerBase, e tem dois atributos: o identificador e a rota.
  * Para os atributos, antes da declaração da classe colocar:
    * O identificador: `[ApiController]`
    * A rota: `[Route("[controller]")]`
  * Precisa também referenciar (using) o AspNetCore.Mvc para usar o controller
* Vai ser a porta de entrada para a API.

* ## Ação do Controller
  * Melhor usar métodos assíncronos.
    * A `Task` nada mais é do que uma `promise`.
  * Antes de criar o método, colocar um atributo dizendo o que vai ser: "GET", "POST", etc
  * O nome visível para o método na requisição HTTP, vai ser exatamente o nome que foi definido no atributo.  
    ```C#
    //dentro desse atributo, colocar o nome do parâmetro
    //não precisa ter o mesmo nome do método que vai estar usando isso
    //quando for chamado, vai executar o respectivo método
    [HttpGet("ObterHoraAtual")]
    ```
  * Exemplo de link HTTP para o método: `LocalHost:7275/Controller/NomeAtributo`
    * O Controller no link, vai ser apenas o nome, sem o sufixo "Controller" presente no nome dessa classe
  * Na criação do método, utilizar o Retorno `IActionResult`
    * No return, podemos colocar um `return Ok(obj)`, onde a variável `obj`, vai ser a variável que iremos alimentar nesse método
      * O `Ok` é um método dessa interface `IActionResult`
    * Como iremos retornar apenas uma variável, podemos criar ela e "colocar dois valores", criando assim um JSON:
      ```C#
      //o retorno da requisição, vai ser exatamente assim (com essa estrutura de json)
      var retorno = new
      {
        //métodos de datetime que retornam apenas a data e a hora respectivamente
        Data = DateTime.Now.ToLongDateString(),
        Hora = DateTime.Now.ToShortTimeString()
      };
      ```
    * Podemos também colocar parâmetros nesses métodos, da mesma forma que um método normal.
      * A única diferença vai ser no atributo
      ```C#
      //o que está em {}, é o parâmetro a ser recebido
      [HttpGet("Apresentar/{nome}")]
      ```