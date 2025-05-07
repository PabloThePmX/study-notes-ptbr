# Blazor

* Uma framework baseada em componentes.
  * Ou seja, quando é feita a requisição do site, ele vai chamar o componente `root`, e dentro dele vai carregar cada componente, e cada um desses componentes pode ser trabalhado individualmente.
    * Ele vai juntar isso em um código HTML padrão e vai enviar de volta para o browser rederizar.
* É Spa (Single page application)
  * Vai renderizar apenas o que mudou, deixando o que está igual sem precisar carregar novamente.

> O jeito novo de criar apelicações Blazor, é com o Blazor Web App, pois o WebAssembly era usado antigamente.

* **Não usar interactividade por agora**

* No program, vai iniciar serviço dos componentes razor 
  * O program funciona igual ao program do aspnet core, que inicia os serviços necessários.

* O app.razor vai ter as tags `<HeadOutlet />` e `<Routes/>`
  * Essas tags serão substituidas pelos arquivos de páginas, os quais estão sendo buscadas pelo arquivo das rotas.
  * Assim, esses serão os únicas tags html a ser atualizadas quando o usuário acessa a página.

* Routes.razor vai receber as informações do componente. **(TODO: VER EXATAMENTE O QUE FAZ)**

* Para rodar (vai ser como debug):
  * No VSCODE, clicar F5, selecionar o C# e selecionar o perfil que vai rodar a aplicação.
* Sem ser debug, usar o `dotnet run` ou `dotnet watch` no terminal.
  * Podemos tirar o redirect para o https no program, assim ele não irá tentar redirecionar a aplicação para https (que acaba mostrando um erro no terminal)
* No launchSettings, se deixar a tag launchBrowser como false, vai evitar que toda vez que for rodar a aplicação, abra uma nova aba do navegador.
