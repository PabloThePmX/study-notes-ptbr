# Compilação

### IL Code
* Durante a compilação, teremos um código intermediário (IL Code), com ele vai ser gerarado o .exe ou a .dll. 
  * O IL Code não depende da OS que está sendo usada, pois é um código abstrato

### JIT e CLR
* O **JIT Compiler** pega esse IL Code e transforma para a arquitetura específica da máquina.
* O **CLR (Runtime)** é como se fosse uma máquina virtual para rodar a aplicação.
  
### Transpilador
* Um transpilador transforma uma linguagem de alto nível para outra de alto nível. Ex.: TypeScript para JavaScript.
  * JavaScript não converte, ele é interpretado direto do código fonte (ou seja, ele possui um interpretador que é capaz de entender o código do jeito que está).

# IDEs

### Visual Studio
* Visual Studio é a principal IDE do .NET, porém é bem pesada.

### Visual Studio Code
* Visual Studio Code teoricamente é um editor de texto, e não uma IDE.
     * Podemos instalar as extensões para transformar em uma IDE de uma linguagem específica.
* No VS Code é preciso instalar uma extensão para ter o intellisense (para
mostrar os erros e sugestões) do C#
  * Extensão “C# extensions” para ter a criação de objetos mais clara

### JetBrains Rider
* JetBrains Rider é uma IDE para o .NET, sendo até mais completo que o
Visual Studio (muito integrado com Unity).
    * Ele também pode sugerir códigos para melhorar a performance.
    * É pago e é um software pesado

### SDK e Runtime
* Se eu quero desenvolver em .NET preciso pegar o SDK, se quero apenas
rodar o .NET, baixo apenas o runtime
  * O SDK é mais pesado
  * O SDK tem o runtime junto
  * O runtime é ideal para botar em servidores, já que os mesmos vão apenas rodar o .NET, e ele é mais leve.
* Temos vários tipos de projetos no .NET, como console, API, etc.

# CMD

* Usar o comando ```dotnet –-info``` (duas “-”) no cmd para ver as informações.dos .NET instalados na máquina.
* Para criar um projeto console no VS Code
  * Abrir o terminal e digitar ```dotnet new console```
* Usar o comando ```dotnet run``` para rodar o programa.

# Organização dos Arquivos em C#

* O `.cs` é o arquivo de classe.
* O `.csproj` possui os metadados do projeto.
  * O OutputType será o que vai sair na hora do build (se tem executável
ou não)
  * São tipos as opções, como o projeto deverá ser.
* Solution é um agrupamento de projetos.

### Bin e Obj
* Ao compilar, grande parte dos arquivos serão jogados na pasta “obj”.
* O "bin" é a pasta de binários
  * O build será enviado para cá (os `.exe`, `.dll`, etc.)
* Ambas são pastas que não precisam ser mexidas, nem salvas no versionamento. Pois ao executar o build, essas pastas serão geradas novamente.

# Conceitos Iniciais para o Projeto

### Abstração
* A abstração é o conceito de pegar um objeto do mundo real para transformá-lo em um objeto na programação.
  * Uma classe é um conceito representado do mundo real.
* Para simplificar os processos, é recomendado abstrair somente o necessário, ou seja, o que será usado de fato.

### Classe e Métodos
* Um método é uma ação que a classe vai fazer (ele tem parênteses no final).
* Uma classe tem os atributos e então os métodos, nessa ordem.
* Todo o nome de classe deve iniciar com maiúscula.
* O namespace é uma organização de classes.
  * Ao utilizar o namespace, é bom colocar com várias divisões (Ex.: Models.Conta.BancoSicredi, Models.Conta.BancoMafra)
* O atalho “Prop” é propriedade
  * A propriedade são as características da abstração, as variáveis por exemplo.
* Usar o “$” na frente de uma string para utilizar variáveis dentro da mensagem com “{var}”.
* O get e o set existem na declaração para definir que a variável pode ser armazenada e usada.
* Método e função são a mesma coisa, porém no C# é mais comum escutar método.
* É possível usar uma palavra reservada colocando um “@” na frente. (Melhor não usar)
* O Program.cs é o início do sistema.
* Para pegar um classe de outro namespace:
  * Colocar o using com o namespace da classe
  * Depois instanciar com: 
    ```C# 
    //nome da classe, variável = nova instância da classe
    Pessoa p1 = new Pessoa(); 
    ```
* Quando for instanciada a classe, o `new` irá dizer que aquela classe já foi feita (executada) e pode ser usada e alimentada como uma variável normal.
* Podemos ter classes com nomes iguais, porém os namespaces devem ser diferentes
* Evitar abreviações (convenção), para deixar mais claro o código.
* O nome do arquivo deve ser o mesmo da classe (convenção).

### Padrões de escritas (cases):
* O camelCase e PascalCase são os mais usando em C#.
  * `camelCase`
    * Variáveis
  * `PascalCase` 
    * Nomes de classes, métodos, propriedades
* `snake_case` 
* `spinal-case`

# Organização Estutural

### Csproj
* O arquivo csproj tem as infos do projeto
* Sem um csproj, não é possível executar o projeto
* FALAR MELHOR SOBRE O CSPROJ

### Sln (Solution)
* O arquivo sln é um agrupamento dos projetos
* Extensão **VSCode Solution Explorer** para criar sln no VSCode
  * Adicionar o csproj na solução criada
    * Só é necessário fazer isso quando a solução é criada após o projeto.
* Class Library é uma biblioteca de classes que vão ser usadas no código não gerando assim um executável próprio
  * Uma boa prática é colocar o nome + .Common pra dizer que vai ser um projeto referenciado por vários outros
  * O nome da pasta pode ser o mesmo do projeto
* Uma boa prática e separar os projetos em pastas e a solução fica fora da pasta
* Outra boa prática é colocar o namespace com o nome do csproj
  * Ir usando a hierarquia Pasta1 - Pasta2 - Pasta3, o namespace será Pasta1.Pasta2.Pasta3
* Dentro da sln, ao referenciar um projeto, é preciso ter seu caminho completo (com as pastas).
  * É preciso adicionar diretamente a referência do outro projeto (o outro csproj), e assim, é possível utilizar as classes do outro projeto também.
    * Isso me deixou em dúvida, ao referenciar, preciso colocar o using para chamar o outro projeto? “Chamados de referência quando um projeto precisa conhecer o outro para usar as suas classes.”
* O método Main() (que é a classe “principal e de entrada” de um projeto) está implícito nas versões 6+ do .NET
  * Nas versões antigas ele é explícito
  * Essa classe principal e de entrada é o Program.cs
    * Que nas versões mais antigas tem o Main()
* Pelo console, para especificar a versão do net ao criar um projeto, é necessário escrever `--framework net5.0`
  * Se não especificar, ele pega a última versão instalada na máquina