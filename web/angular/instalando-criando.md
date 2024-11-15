# Instalando

* Precisa baixar e instalar:
  * NodeJS e NPM
  * Angular Language Service
  * Opcionais:
    * Auto Close Tag (pois creio que só tem esse funcionamento em html puro)
    * Auto Rename Tag (renomeia a outra tag, caso alguma delas for alterada).

## Para instalar o angular na máquina
  * Usar o comando `npm install -g @angular/cli`.
    * O `-g` diz que é global.
  * Para saber se instalou corretamente, ver se veio o `ng` (que é usado para criar/executar os scripts do angular).
    * Se o `ng help` mostrar os comandos, quer dizer que deu certo.
    * Geralmente no windows ele não funciona corretamente logo ao instalar, pois o windows desabilita isso (`Get-ExecutionPolicy --List` no powershell como admin, para ver se ele permite executar coisas de terceiros). 
      * Primeiramente desinstalar o pacote do angular.
      * Limpar o cache do npm com `npm cache clean --force` e `npm cache verify`.
      * No Powershell como admin:
        * Executar o comando `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`
          * Dizendo que é permitido que ferramentas remotas gerem scripts (como o ng) para o usuário atual.

## Ao criar o projeto
* O `.editorconfig` possui as opções do editor.
  * Alterar para dizer que a indentação será com o tab.
* A pasta `environments` vai permitir salvar variáveis globais, como senhas, chaves de API, chamadas "fixas", etc.
  * Possui um arquivo para produção e para desenv.
* 
  
## Comandos ng
* `ng generate [tipo] [nome]` para gerar uma estrutura de código do tipo especificado. 
  * Como componentes, classes, etc.
  * Caso for componente, ele cria o componente dentro de uma pasta, e atualiza o módulo para apontar para ele.
  * Para criar um componente usando alias, podemos usar o `ng g c [nome]`.
* `ng add <collection>` é usado para adicionar bibliotecas externas ao projeto.
* `ng new [nome]` cria um novo projeto.
  * Ele pergunta o que vai ser usado no projeto.
  * Colocar o nome do projeto em snake-case.
* `ng run <target>` executa o programa.
* `ng serve [project]` faz o build e cria um servidor da aplicação.
  * Então quando altera a aplicação, ele recompila para o mesmo servidor.
  * Se está na pasta do projeto, obviamente não precisa passar o caminho.
* Todos possuem aliases.