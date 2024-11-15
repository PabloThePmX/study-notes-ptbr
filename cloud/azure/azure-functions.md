# Azure Functions

* Semelhante a uma API.
* Serverless: modelo de desenvolvimento nativo em nuvem para criação e execução de aplicações sem o gerenciamento de servidores.
  * Os servidores ainda são usados, mas são abstraídos.
  * Ou seja, só precisa se preocupar com a arquitetura que vai ser executado o programa.
    * Não importando quanto de RAM, armazenamento, etc, vai existir.
  * São os azure functions que implementam esse conceito.
* Escalam horizontalmente de forma automática.
  * Ou seja, se ajusta caso a carga necessária fique maior ou menor.
* No Azure, clicar em `Create Function`.
  * Escolher o runtime
  * Vai ter vários templates, como timer trigger (executa a cada x tempo), http trigger, etc.
  * O `HTTP Trigger with OpenAPI` já vem com o swagger.
    * OpenAPI tem as informações para o swagger exibir.
* Podemos definir o tipo de segurança da função.
  * Tipo anônimo qualquer um pode acessar.
  * Tipo function, funciona apenas ao passar uma chave.
  * Tipo admin