# Guards

* Verifica se o usuário tem acesso a aquela determinada rota.
* Da pra gerar um arquivo guard com o `ng g g <NOME-GUARD>`.
  * Geralmente se cria uma pasta `guards` para colocar eles.
  * Fica com a extensão `.guards.ts`
  * Vai mostrar 4 tipos que podem ser escolhidos (pode ser escolhido mais de um):
    * `CanActivate`
    * `CanActivateChild`
    * `CanDeactivate`
    * `CanLoad`
  * Cada um desses tipos vai ser um método que será gerado na classe.
* Os métodos de verificação dos guards vão estar retornando boolean, ou seja, vão estar dizendo se pode ou não passar. 
* Para ativar esse guard, precisa colocar no objeto das rotas, ou seja, além de conter o path e o component, vai verificar também a função definida no guard.
  * Colocar a propriedade desse guard, e alimenta-lo com o arquivo guard criado. `canActivate: [<ARQUIVO GUARD>]`.
    * Pode até ser mais de um arquivo.
* A rota sera bloqueada caso o retorno da função guard for false.
  * Então é dentro dessa função do guard que vai ter a lógica verificando se o usuário pode ou não acessar a url.
    * Por exemplo: verificar se existe ou não token, dessa forma retorna um boolean dizendo se o usuário fez o login ou não.
* 