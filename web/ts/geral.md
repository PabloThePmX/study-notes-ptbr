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

### Arquivo config
* Para criar um arquivo de config, executar o comando `npx tsc --init`.
* No `tsconfig.json`:
  * Alterar a `rootDir` para `./src`, para indicar qual a pasta raiz que vão estar os componentes (caso seja omitido o caminho na hora de transpilar).
    * Dessa forma. ao executar o comando `npx tsc`, ele vai dar build em todos os arquivos dentro da pasta.
  * Alterar o `outDir` para `./build`.
  * Temos também a opção `removeComments`, que remove os comentários do arquivo compilado quando é feito o build.
* No `package.json`:
  * Criar um novo scrip chamado `start`, com o valor `npx tsc && node build/index.js`
    * Assim, ao rodar o `npm run start`, ele vai transpilar e executar o código.
* Jeito mais fácil de rodar o código TS (`TS Node Dev`):
  * Primeiro instalar o pacote `npm install ts-node-dev -D`.
    * É um servidor local que entende TS, e por causa disso não precisa gerar build (ele gera em memória).
  * Criar um script novo no `package.json` chamado de `"start:dev"` contendo o valor `ts-node-dev --respawn --transpile-only src/index.ts`.
  * Para executar o novo script `npm run start:dev`
  * Por se tratar de um servidor, ele vai atualizar conforme forem ocorrendo as alterações.

### Tipos de Dados
* Possível declarar a variável como qualquer um desses tipos.
* **Primitivos**
  * `boolean`
  * `number` (com ou sem decimal).
  * `string`
  * Para tipar as variáveis: `let ligado:boolean = false`.
* **Tipos especiais**:
  * `null`
  * `undefined`
* **Tipos abrangentes**:
  * `any`, aceita qualquer valor
    * Usado para valores imprevisíveis, ou seja, quando não sabemos exatamente o que vai ser retornado.
  * `void`, quando a função não retorna nada
* **Tipo object**
  * A variável precisa usar as `{}`, pois é um objeto em si.
  * Porém não é recomendado pois nunca sabemos como vai ser o objeto em si, para isso, devemos tipar exatamente o jeito que a struct do objeto é formado:
    * Criar um tipo com `type ProdutoLoja {nome: string; preco: number; unidades: number; }`
      * Assim, ao declarar a variável, usamos o tipo desse objeto `let meuProduto: ProdutoLoja = {nome: "Tênis", preco: 99, unidades: 5}`
        * Dessa forma, caso alguma dessas propriedades seja omitida, vai acusar um erro, por não estar respeitando o tipo.
* **Arrays**:
  * Temos duas maneiras para declara-lo:
    * `let dados: string[] = ["nome1", "nome2"]`
    * `let dados2: Array<string> = ["nome1", "nome2"]`
  * Podemos declarar arrays com múltiplos tipos (usar o OR):
    * `let infos: (string | number)[] = ["Pablo", 24]`
      * Porém é melhor criar um objeto ao invés de fazer dessa forma.
* **Tuplas**
  * É um vetor multi-tipo com uma ordem exata.
  * Para declarar, colocamos a ordem dos tipos, como `let boleto:[string, number, number] = ["conta água", 190.90, 1234556]`
    * Ou seja, o tipo vai ser a ordem desses tipos.
* **Datas**
  * É uma interface do tipo `Date`.
  * Usa-se o padrão "ao contrário"
  * Para declarar `let aniversario:date = new Date("2000-03-01 04:00")`
    * O `Date` pede horário também.

### Funções
* Tipar os parâmetros `function addNumber(x: number, y: number){}`
* Tipar o retorno `function addNumber(x: number, y: number) : number{}`
  * Implicitamente, ele vai tipar o método conforme o tipo do valor retornado.
* Podemos usar multi-tipo para o retorno ou o tipo do parâmetro:
  * `function Teste(phone: string | numer) : string | null {}`
* Função assíncrona é usada para "esperar" alguma outra coisa para poder continuar.
  * Para tipar esse tipo de função `async function GetDatabase(id: number) : Promise<string | number> {}`
    * Async retorna sempre `Promise`.
* O keyword `function` pode ficar implícito.

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

### Decorators
* Decora um método, e coloca um gatilho para executa-lo em determinado momento.
  * Injeta coisas (durante o runtime) que não existiam originalmente na classe, como funções ou atributos.
* Habilitar a opção `experimentalDecorators` no `tsconfig.json`.
* Para criar um método decorator `function ExibirValor(target: any) {}`
  * Para chama-lo, colocar como uma anotação de uma classe `ExibirValor`
    * Isso é o **Class Decorator** que sempre é executado quando colocado acima de uma classe
  * **O target, vai ser o nome da classe, atributo, etc anotada.**
* Nem sempre vai funcionar ao tentar transpilar, porém funciona no servidor.
* São muito usadas, funções que retornam outras funções (utilizando arrow function `=> {}`).
* **Attribute Decorator**
  * Um decorador colocado em um atributo, usado para colocar comportamentos ou validações.
  * **O key vai ser o valor do classe, atributo, etc anotado**.
* Criar getter e setter dentro de funções decorator:
  * `const getter = () => _value;`
  * `const setter = (value: string) => {_value = value}`
    * O `= () =>` é os parâmetros.
* Ao definir as funcionalidades, injetar elas novamente no objeto (classe) com `Object.defineProperty(target, key, {get: getter, set: setter})`
  * Essa definição, está colocando métodos acessadores, mesmo após a criação do objeto.