# Preços

* Três fatores de custos com a AWS: Computação, armazenamento e transferência de dados (a entrada de dados e a transferência entre servidores da mesma região são gratuitos).
* Pague pelo que usar.
* Preços em camadas para serviços como S3, EBS ou EFS, ou seja, quanto mais usar, menos se paga por GB.
* Serviços sem custo: VPC, Elastic Beanstalk, Auto Scaling, CloudFormation, IAM.
  * Porém pode haver cobranças de serviços que são "chamados" por eles.
* Na infra tradicional, tem muitos custos capitais.
  * Esse valor não existe na cloud.
* Alguns serviços permitem instancias reservadas (RIs), e ao fazer a reserva existe uma economia maior pois você está dizendo pra AWS não cobrar mais por uso, e sim cobrar um valor X por um tempo pre determinado.
  * Instancia reservada com pagamento total antecipado (AURI)
  * Instancia reservada com pagamento antecipado parcial (PURI)
  * Instancia reservada com pagamento antecipado (NURI)
* TCO - Custo total de propriedade.
  * Estimativa financeira para ajudar a identificar custos diretos e indiretos de um sistema.
  * Usado para criar um orçamento de um caso de negócios para migrar para a nuvem.
* A AWS possui uma calculadora mensal para estimar e reduzir custos.
* O gerecimento de cobrança possui serviços como orçamento da AWS, relatório de custos e explorador de custos (AWS Cost Explorer).
* Existe um painel para analisar os custos e usos no mês, o que está saindo mais caro, etc.
  * Da pra criar notificações e limites para valores no mês.
* Da pra mandar relatórios de custo para o S3 e atualiza-lo todos os dias.
* Da pra criar e salvar relatórios personalizados.
* O budget é onde vai ser colocado o alerta de uso.
  * E é so um alerta, ele não vai parar nada.

## AWS Organizations
* Junta a cobrança de múltiplas contas.
  * Pode gerenciar contas baseando-se em políticas ou grupos.
* Árvore organizacional onde cada filial representa um time ou departamento.
* Pode utilizar APIs para automatizar o gerenciamento das contas.
* Da pra usar com o IAM para negar o acesso de serviço a contas especificadas.
* Para fazer o uso: Criar a organização, criar as unidade organizacionais, criar politicas de controle e fazer os testes dessas restrições (existem simuladores de IAM).
  * Para criar a organização, precisa já existir pelo menos dois membros na conta.