# OAuth 2.0

* Protocolo usado para conectar aplicativos sem que as informações de login sejam enviadas para o servidor.
* Comunica usando chaves, e não as informações de login/senha
  * Ou seja, o aplicativo verifica se aquela senha tem autorização para acessar a conta.
* Segue o padrão de dono e cliente.
* Resource e Authorization Server.

## OAuth Flow
* Existem diversas rotas em que podemos dar autorização a um app, sendo a mais comum delas a `Authorization Code Flow`.
  * Essa flow usa servidores, url de redirect, scope (acessos permitidos para a autorização), etc.