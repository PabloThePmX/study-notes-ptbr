# Azure Functions

* Semelhante a uma API.
* Ela é mais barata e inclui um número de requisições gratuitas por mês.
* Algo complementar, ou tarefas que devem ser executadas em um período especifico de tempo.
  * Usar para CRUD não vale a pena, pois teria que fazer mais requisições e não seria tão performático.
* Serverless: modelo de desenvolvimento nativo em nuvem para criação e execução de aplicações sem o gerenciamento de servidores.
  * Os servidores ainda são usados, mas são abstraídos.
  * Ou seja, só precisa se preocupar com a arquitetura (Linux ou Windows) que vai ser executado o programa.
    * Não importando quanto de RAM, armazenamento, etc, vai existir.
  * São os azure functions que implementam esse conceito.
* Escalam horizontalmente de forma automática.
  * Ou seja, se ajusta caso a carga necessária fique maior ou menor (load balancer).
* Vão ser disparadas a partir de algum gatilho.
* No Azure, clicar em `Create Function`.
  * Escolher o runtime
  * Vai ter vários templates, como timer trigger (executa a cada x tempo), http trigger, etc.
  * O `HTTP Trigger with OpenAPI` já vem com o swagger.
    * OpenAPI tem as informações para o swagger exibir.
* Podemos definir o tipo de segurança da função.
  * Tipo anônimo qualquer um pode acessar.
  * Tipo function, funciona apenas ao passar uma chave.
    * Configurar essa chave no próprio serviço no Azure.
  * Tipo admin.
* Nas anotações do método, da pra definir se vai ser recebido via path, o nome, a descrição do swagger, o retorno, etc.
  * A sintaxe padrão do método é um pouco diferente, onde um dos parâmetros vai ser a requisição em si, e ela vai conter informações como métodos aceitos, tipo, rota, etc.
* Usar a implementação do `ILogger` para log (método `LogInformation`).
* Um projeto de Azure Function, pode ter uma ou mais funções (cada uma é uma classe, como se cada uma fosse uma controller).
  * Método `Run` é o ponto de entrada de cada classe.
* Ao criar o serviço na Azure, deixar o plano como "Consumo (Sem servidor)" pois é serverless e queremos que seja cobrado apenas pelo uso.
  * A configuração do serviço  é bem mais simples, so tem que definir a linguagem e o SO.
* O deploy pode dar um erro, dependendo é so rodar o processo novamente.
  * O deploy em si é igual ao de um `AppService`.
  * Se enviar com swagger, da pra acessa-lo para testar.
* Da pra executar diretamente pelo site da Azure.
  * Bem como obter o endpoint de alguma função.