# Banco de Dados na Azure
 
## Criando o banco
Ir até o recurso `SQL Database` no painel do azure.
* Colocar tanto o banco, quanto a aplicação, no mesmo grupo de recursos.
* Vai ser preciso criar o servidor também
  * No servidor, utilizar o sistema de autenticação do SQL
* DTUs é o desempenho do banco, ou seja, quanto mais, melhor (porém mais caro)
  * O tamanho máximo do banco não altera o custo.
* Utilizar a Redundância Local (ao menos momentaneamente).
* Na configuração de rede do banco:
  * Alterar a conectividade para `Ponto de Extremidade Público`
  * Além disso, quando aparecer as opções das regras do firewall, devemos aplicar a opção `Permitir que serviços e recursos do Azure acessem este servidor`
    * Isso significa que estamos permitindo outros serviços da Azure a acessar o nosso banco de dados.

## Acessando o banco
Se formos na visão geral do servidor SQL, ir até o final da página, é possível ver quais bancos estão presentes naquele servidor.
* Pegar o endereço copiado da URL pública do servidor, e colar no SMMS, e selecionar a opção do SQL Server Authentication.
  * Colocar o login e a senha criados para o banco de dados.
* Caso não tenha sido colocada a regra do firewall para liberar o IP, devemos ir na aba de `Rede` do Servidor, descer e clicar na opção `Adicionar o endereço IPv4 do cliente`
* Caso a senha tenha sido esquecida, é possível redefinir a mesma.
* 
