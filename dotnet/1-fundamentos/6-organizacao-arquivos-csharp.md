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