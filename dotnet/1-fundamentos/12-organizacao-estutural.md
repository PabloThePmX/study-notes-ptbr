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
