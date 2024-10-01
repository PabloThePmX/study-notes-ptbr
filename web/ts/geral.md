### Geral
* o TypeScript é um superset do JavaScript.
  * Ele adiciona mais coisas ao JS.
  * Tudo que funciona no JS, vai funcionar também no TS.
* Adiciona tipagem.
* Erros em tempo de desenvolvimento (pois não é interpretado como o JS).
  * Dessa forma, ele garante uma maior confiança durante o desenvolvimento.
* É transpilado (compila e traduz) para JS.
  * O Node que faz isso.
* Podemos instalar com `npm` (globalmente) ou `npx`, como dependência do projeto que será feito.
  * Colocar como dependência, permite que cada projeto possua uma versão diferente caso necessário.
* Para iniciar o projeto `npm init -y`.
* Para colocar o TS no projeto `npm install typescript -D`
  * A flag `-D` diz que a dependência deverá ser apenas para o ambiente de desenvolvimento.
    * Teoricamente é pra isso que o TS serve, para trabalhar com ele na hora de desenvolvimento.
      * Pois ao executar, será sempre JS.
* Para executar o TS, utilizar o comando `npx tsc Caminho/Arquivo`.
  * Onde o `tsc` é o compilador do TS.
  * Isso vai gerar um arquivo JS, que será o nosso arquivo compilado.
  * Depois de gerar o arquivo compilado, executar como um JS normal, `node Arquivo/JS`.
* Usar underline para atributos privados.
* Jogar exceções com `throw new Error` quase como no C# 

### Interfaces ou Types
* A `interface` é muito parecida com o `type`.
* A interface é usada mais para classes, enquanto o `type` é usado mais para objetos (`const` ou `let`).
* Uma propriedade suporta multi-tipos também.
* Pode ter propriedades `readonly`, que são alimentadas apenas na criação.
* Interfaces podem ter métodos.
  * Tipar o retorno desse método.

### Classes
* Para declarar uma classe `class Personagem{}`
* Para declarar um método `NomeMetodo(): void{}`
  * Como no JS, dentro de classe não tem o keyword `function`.
* Para declarar um atributo `name: string`
  * Usar camelCase.
  * Se não atribuir o valor direto na propriedade, é necessário alimentar no construtor
    * Para declarar o construtor `constructor(name: string) {this.name = name}`
  * Para deixar uma propriedade opcional, é necessário colocar o `?`, ou seja `name?: string`.
    * Dessa forma, na hora de instanciar a classe com o `new`, não é necessário passar o valor opcional.
* As classes do TS tem modificadores de acesso, sendo eles:
  * `public`
  * `private`
  * `protected`
    * Só pode ser enxergado pela classe ou suas subclasses, que herdam.
  * Por padrão, sem não passar nada, é `public`
* Podemos declarar os atributos com `private` e fazer os métodos `get` e `set`. 
* Para usar uma interface, declarar `class Teste extends InterfaceTeste{}`
* **Herança**
  * Para herdar, declarar conforme foi feito para a interface.
  * Para chamar a classe pai (superclass), usar o `super()`.
    * Principalmente no construtor.

### Generics
* Usado para especificar o tipo de algo durante o runtime.
* Da pra passar o tipo por parâmetro ao invocar algum método.
  * Para isso, o método precisa ser declarado com `<>`, sendo assim: `function testeArray<T>(...itens: T[]): T[] {}`
    * E na invocação desse método: `testeArray<number[]>([1,5], [2])`