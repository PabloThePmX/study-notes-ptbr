# Injeção de Dependências
É uma técnica que implementa um design chamado de IoC.

# Interface
Vai ter os métodos que vão ser utilizados pelo repositório.

# Repositório
É onde vai ser colocado o contexto.
* Precisa ter a sua interface.
* Por aqui, vai ser injetado o contexto pelo AddScoped.

### Criando Dependências (Obs.: cada requisição, é uma instância criada)
É colocado nos serviços que são executados ao iniciar a aplicação.
* `AddSingleton` sempre vai ter o mesmo Id.
* `AddScoped` vai ter o mesmo Id dentro da requisição, e cada requisição terá um Id diferente.
  * É o mais utilizado (?)
* `AddTransient` vai ter um Id novo pra cada requisição.