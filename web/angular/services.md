# Services 

* Arquivos TS para colocar as regras de negócio, um provedor de dados.
* Podem estar servindo a mais de um componente.
* Usa o sufixo `.service`.
* Optar por services menores, e não um service com muitos métodos "aleatórios".
* Criar um pasta apenas para os services.
* O arquivo `environment` serve para guardar valores de variáveis tanto pra debug como para produção.
  * Podemos salvar nele a url da API (o root da url, sem os endpoints e afins).
  * Importar no service que vai utiliza-lo.
* Para gerar um arquivo service, é possível usar o comando `ng g s` no terminal.
  * Ele cria com o sufixo `service` no final.
* O serviço é um conteúdo injetável.
  * Antigamente era injetado nos providers do módulo.
  * Injetar no construtor das classes que irão usar o serviço.

## Requisições HTTP
* Importar o `HttpClientModule` no componente app, de entrada.
  * Ele está obsoleto, usar `provideHttpClient(withFetch())` nos providers do `app.config.ts`.
* Injetar o `HttpClient` no construtor do service.
  * Esse `HttpClient` terá os métodos http.
    * Nele, coloca a URL base e complementar com os parâmetros a serem enviados usando o template string.
    * Da pra mandar um objeto com as opções também.
* Angular trabalha com `observables` (um design pattern).
  * Ele fica "vigiando" algo, esperando acontecer.
  * Da pra até colocar que o método vai retornar esse tipo.
  * Vem de uma biblioteca do js chamada `rxjs`.
  * Paradigma funcional.
  * Como o observable aceita tipos genéricos, é necessário criar uma pasta `models` que contenha o tipo do retorno, ou ao menos, as informações do retorno que queremos (recomendado apenas se for pegar propriedades uma a uma). 
    * Como é um tipo, precisa ser algo como `export type tipo = {}`.
    * Caso não for possível pegar o tipo, da pra usar o `any` (não recomendado).
  * Possível tipar o método do Http, para dizer qual é o tipo a ser observado.
    * Ex.: `this.http.get<tipo>();`
  * Na hora de chamar o service, colocar um `subscribe` no método, para dizer que ele vai estar vigiando aquilo, qualquer alteração vai ser avisado.
    * Dentro desse subscribe, podemos pegar a resposta caso de certo usando o `subscribe({next: () => console.log("deu certo" + res)})` e caso deu erro, colocar junto ao next a propriedade `error` e buscar o valor da mesma forma que a resposta correta.
      * Ao invés de pegar toda a resposta, podemos pegar propriedades específicas, Ex.: `res.id`, e dessa forma, alimentar o tipo somente com as informações que desejamos.
  * Os tipos precisam ser inicializados, podendo ser tanto na declaração, quanto no construtor.