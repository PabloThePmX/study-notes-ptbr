# Decorators
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