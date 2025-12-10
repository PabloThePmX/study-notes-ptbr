# VMs

## Criando VM
Para criar uma máquina virtual, devemos ir so serviço `Criar uma máquina virtual do Azure`
> O grupo de recursos é como se fosse uma pasta para separar os recursos.
> Deixar a opção de permitir as portas selecionadas, e deixar marcada a opção de `RDP`

## Para acessar a VM:
Clicar em conectar, e selecionar o RDP, ele vai baixar um arquivo, e ao executar, vamos precisar colocar as credencias que foram criadas.
> Caso tenha se esquecido da senha, podemos ir em `Redefinir Senha` para mudar.
> Dica: Para não consumir muito, mas deixar o servidor rodando, fazer logoff da conta do Windows na VM.

## Para apagar a VM
Não adianta apenas parar a máquina, ela vai continuar tendo custos pois ela cobra pelo uso do HD, portanto é necessário remover o recurso da VM, para isso:
* Ir em `Grupos de Recursos`, entrar no recurso e ver tudo que está sendo usado nele
> Ao criar uma VM, ele cria diversos outros recursos que são necessários para o funcionamento da mesma.
* Assim, devemos apagar o grupo de recursos por inteiro (tem um botão para realizar isso)

## Servidor WEB na VM
* Ir no Windows Server Manager na VM.
  * Depois ir em Add Roles and Features.
    * Vai abrir um wizard de implantação, e nele podemos ir clicando next.
    * Ao chegar na tela de Server Roles, selecionar a opção `Web Server (IIS)`, depois continua com o next
> Assim vai ser instalado o IIS para rodar um website.

### IIS    
Ir em sites, e clicar com o direito nos sites que aparecer, selecionar `explore` para ver os arquivos desse site.
* O site só esta rodando no local por enquanto, pois para rodar na web vai ser necessário liberar a porta do servidor.
> Pois por padrão, tudo é bloqueado de ter acesso externo.
    * Para liberar a porta:
      * No portal da azure, ir em `Rede`
      * Clicar para adicionar uma regra de entrada, e selecionar o serviço HTTP, após isso, só confirmar.
        * Para testar, colocar o IP do servidor público no navegador.
