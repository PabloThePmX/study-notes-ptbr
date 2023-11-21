# API

**TODO: Ajustar e colocar a palavra "Endpoint" onde estaria correto**

### O que é uma API
* Application Programming Interface é uma comunicação que ocorre entre softwares e computadores.
  * A API é a intermediação dessa comunicação.
  * A API pode ser online ou offline, existem dos dois tipos.
* Exemplo do restaurante
  ***TODO: COLOCAR A IMAGEM AQUI**
  * O cliente faz o pedido, o garçom recebe, envia para a cozinha e aguarda receber o que foi pedido, logo após, o garçom pega o pedido e envia de volta para o cliente.
* Outro exemplo: Sistemas de ecommerce costumam usar APIs para enviar a confirmação da compra para a empresa de transporte, confirmado para onde o produto X deverá ser enviado.
  * Quando queremos saber quanto tempo vai demorar para chegar um produto, é feita também uma requisição para a empresa de transportes, que vai retornar essa estimativa.
  * Ambas as empresas, não irão consultar diretamente o banco de dados uma da outra, vai ser a API a responsável por fazer isso.
* APIs podem ser internas, ou seja, que não estão expostas na internet, e estão disponíveis apenas dentro de uma organização.  
  * Podemos também ter APIs externas, que estão expostas na rede, e podem ser acessadas por terceiros, que estão fora da organização.

### Request e Response
* O requisito é aquilo que estamos enviado.
  * Devemos seguir exatamente o que a requisição pede, enviando os parâmetros corretos para enviar um erro 404 (que não encontrou nada)
* A response vai ser a resposta contendo os valores requisitados.
* Isso tudo pode ser encontrado nas documentações das APIs
* **TODO: Explicar Fetch** 

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

### Controller
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

* ### Ação do Controller
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

# Exemplos de APIs

### Nager.Date (TODO: COLOCAR LINK)
* É uma API que retorna os feriados públicos de todos os países.
* Retorna até os feriados por diferentes anos
* Ela espera receber por parâmetros o ano e o código do país (BR)
* O resultado vai ser um JSON contendo todos os feriados e as datas do ano designado daquele país.

### DogApi
* Imagens aleatórias de cachorros
* Vai retornar uma imagem JPEG
* Nos parâmetros, podemos especificar qual a raça de cachorro que queremos que retorne nas fotos