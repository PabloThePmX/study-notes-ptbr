* Componentes lógicos não tem a parte visual, apenas a lógica em si.
* É apenas um pedaço da composição do layout, e por isso, podem ser reutilizáveis em páginas diferentes.
* Componentes "começam" no TS.
* Nada mais são que uma função TS que monta html, css e js.
  * Na função, vai ter um decorator (tipo uma anotação), que vai dizer o nome do seletor (ou seja, como vai ser o nome da tag), qual o html e qual o css dele.
    * O css pode ter mais de um arquivo.
    * As propriedades podem ser definidas inline.
      * Porém a propriedade deve ser escrita com um nome sem o sufixo `Url`.
    * É um objeto com propriedades.
  * Vai exportar uma classe ts.
    * Nome da classe em PascalCase.
    * É nessa exportação que serão definidos os parâmetros (interpolação de dados).
      * As propriedades e o seu tipo, pois é ts.
        * Todos os tipos, até arrays e objetos.
      * Para chamar esses parâmetros e pegar o seu valor, usar `{{nomePropriedade}}` dentro da tag que invoca esse componente.
      * Possível definir um valor padrão nessa declaração, caso a propriedade não seja alimentada com algum valor. (?????????)
* A composição dos componentes é montada a partir da injeção de dependências.
  * Todos os componentes são injetados no `app-root` (componente principal) e esse componente é então injetado no `index.html`.
  * Por isso que ao abrir o dev tools, aparece apenas o index com o `app-root`, pois os outros componentes estão sendo injetados dinamicamente dentro dele.
* Importar o `component` do `@angular/core` no ts, esse `component` é uma interface.
  * Isso vai dizer que precisa do decorator `@Component`.
* Uma dica para ter css responsivo, é a de ter dois css no componente, um normal, e outro `.responsive`, e nele tendo o `media queries`.
  * Lembrar de passar o novo css no decorator do component.
* Agrupar componentes globais em uma pasta, e componentes de página, dentro da pasta da página (cada página seria um módulo caso usasse da maneira antiga sem ser standalone).
* Se o componente for útil apenas para um outro componente, da pra cria-lo dentro da pasta desse componente pai.
  * Colocar o nome do componente com o nome do componente pai e usar o `-` para dizer o nome do filho. (Nem todo mundo faz assim).
* O decorator `@Injectable` da classe, diz que aquela classe está visível e pode ser injetada por outras.
  * E o `providedIn` diz onde essa classe esta sendo fornecida, geralmente sendo `root`, significando que desde a raiz, todo mundo enxerga essa classe.

## Estrutura do projeto
* Dentro da pasta `src` são colocados os códigos em si.
  * O `index` vai apontar apenas para um componente, que é o componente root (`my-app`).
  * O `main.ts` vai iniciar o angular.
  * O `polyfills` é pra aumentar a compatibilidade com navegadores mais antigos.
  * Dentro da pasta `app` temos os componentes.
    * Os componentes seguem a convenção de nome `nome.component.html/css/ts`.
      * Tudo minúsculo.
    * Criar uma pasta apenas para colocar os componentes.
* O que está fora da `src` são arquivos de configuração. (src out)
  * Configurações do TS.
  * Configurações do NodeJS.
    * O node que vai transpilar o TS.
  * Configurações do Angular.
  * Configurações de algumas outras dependências instaladas.
  * O `style.css` é o css global da aplicação.
    * O css sempre da preferência pro scoped, ou seja, o css específico do componente vai sobrescrever o valor do global.
* O arquivo de módulo é responsável por agrupar todos os componentes.
  * Precisa importar os componentes aqui.
    * Não precisa dizer o formato do arquivo no caminho da importação.
  * Declarar no decorator `@NgModule`.

## Data Binding
* Passa algo da parte lógica, para a parte visível, passa de um lado para o outro.
* Para dizer que vai receber valor do componente pai, na exportação do componente filho, definir a propriedade (precisa inicializar) com um decorator `@Input()` no início, 
  * Na hora de chamar, definir o valor da propriedade nas tags, ou seja `<nova-tag [label]="valorLabel">` (geralmente essa é utilizada com maior frequência).
    * Ou `label="{{valorLabel}}"`.
      * O `{{ }}` indica que está esperando uma variável (propriedade).
    * Com colchetes funciona apenas com variáveis, e não com uma string normal (como um texto).
  * Precisa importar o `input` do core.
* Podemos definir valores no componente pai, nas propriedades, e então usar essa variável definida para alimentar a propriedade.
* Para chamar via evento (`event biding`), na tag, colocar o tipo do evento (por exemplo `(click)`, com os parênteses) e ali chamar uma função, função essa que deverá ser exportada junto no componente pai.
  * Os eventos são os do próprio HTML, e a única diferença é que eles precisam estar dentro de parâmetros.
  * Os eventos podem ter parâmetros.
* Para fazer o two way, precisa setar o valor de alguma das propriedades, dentro da tag, ou seja `<input (input)="nomeProp = novo Valor"/>`
  * O evento `input` só é chamado nesse caso pois é necessário setar o valor a propriedade durante o seu uso, visto que esse evento já é usado implicitamente pela tag `<input>`.
  * Onde ele está setando o valor da propriedade ao digitar no campo de input.
  * Ex. mais explicado: `<input [value]="nomeProp" (input)="nomeProp = $any($event.target).value"/>`, ou seja, ele está mostrando o valor de `nomeProp` no `value` da tag, e setando um novo valor para a mesma a partir do que está sendo escrito no campo de input, pois está alimentando o valor da propriedade.
    * Em resumo, usar o `[]` para mostrar, e `()` para setar.
  * Podemos fazer de uma maneira mais fácil (diretivas do angular), pois faz de uma vez só:
    * Ao utilizar o `[(ngModel)] = "nomeProp"`, ele junta os dois comportamentos em uma coisa só.
  * Para mostrar esse valor em algum local, utilizar a interpolação normalmente.
  * Esse `ngModule` vem da classe dos módulos do angular, e ela funciona a partir de um módulo importado de uma lib de forms do angular (`FormsModule`).
* O CSS pode ser dinâmico.
  * Usar o property biding no `style`.
    * Se for setar algum valor específico, pode ser algo tipo `[style.color]`

### Tipos de Data Bindings
* Componentes enviam pro HTML (parte lógica para o HTML)
  * Interpolação
    * `{{nomeProp}}`
  * Property Biding
    * `[propriedade do html] = "nomeProp"`
* Evento do html envia algo para o componente
  * Event Biding
    * `(evento) = "método()"`
* Ambos
  * Two Way Data Biding
    * `[(ngModel)] = "propriedade"`
    * Alimenta a propriedade com o valor, dentro da tag

## Ciclo de Vida do Componente (LifeCycle Hooks)
* Existem 8 no Angular.
* São interfaces presentes no `angular/core`.
* Por se tratar de interface, elas precisam ser implementadas.
* Implementar na classe que é exportada.
  * A classe pode implementar mais que um hook.
* `OnInit`
  * Vai implementar o método `ngOnInit()`.
    * Ele é disparado quando o componente é iniciado (start).
    * Existe tanto o construtor, quanto esse método chamado ao inicializar.
      * O construtor é antes de receber os valores vindos como parâmetros.
* `OnChanges`
  * Vai implementar o método `ngOnChanges()`.
    * Executa quando acontece alguma mudança em alguma das propriedades.
      * Precisa passar pelo `@Input`, onde quer dizer que algum outro componente que alterou a propriedade.
    * Pode até ser chamado antes do init, pelo fato de que o valor da propriedade pode ser alterado antes mesmo de iniciar o componente.
* `DoCheck`
  * Executa quando uma propriedade do componente é verificada.
  * Tem 4 sub cheques
    * Cada um vai checar em um determinado momento, depois de inicializar, depois de criar, etc.
    * Todos precisam ser importados.
  * Sempre faz o `OnInit` primeiro, e depois um check.
    * Existe um check (`ngAfterContentInit`) que executa apenas depois que o `OnInit` for executado.
  * Ao detectar uma alteração, é feito o check logo após a alteração do componente, depois acontece o check que verifica o conteúdo, e por fim acontece o check da visualização desse conteúdo.
    * Ou seja: Checked -> Content -> View.
* `OnDestroy`
  * Executa assim que o componente é destruído.
  * Usado juntamente com propriedades `isAliveNomeComponente` para garantir que seja limpa a memória dos componentes que não estão mais sendo usados.
  * O `ngIf` na tag é responsável por dizer se um componente está existindo na tela ou não, o recomendado seria atrelar essa propriedade ao seu valor, assim, toda vez que alterar o valor da propriedade para false, o componente é dispensado (destruído), e consequentemente chama o `OnDestroy`.