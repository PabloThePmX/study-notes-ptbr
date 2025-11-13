# Infraestrutura Global

* Uma região da AWS é uma área de dados.
  * Uma região normalmente consiste em duas ou mais zonas de disponibilidade.
    * Isso é uma partição totalmente isolada da infraestrutura da AWS (datacenters distintos). 
    * São conectadas a outras zonas de disponibilidade usando redes privadas.
* Os dados são replicados dentro da região, e não para fora dela.
  * Isso se torna responsabilidade de quem gerencia a AWS (recomenda-se essa replicação para fins de resiliência).
* Existem regiões limitadas apenas para china, bem como outras para governos transferir dados sensíveis.
* BExistem 4 fatores a serem analisados ao selecionar uma região:
  * Governança de dados e requisitos legais.
    * Alguns locais possuem leis que não deixam os dados estarem em outro país ou região.
    * Leis de proteção de dados diferentes por regiões.
  * Proximidade com os clientes.
    * Cloudping para testar a latência.
  * Serviços disponíveis na região.
  * Custos, pois eles variam por região.
* Da pra usar mais de uma região.
* Normalmente um único datacenter tem cerca de 50000 a 80000 servidores físicos.
* Amazon CloudFront
  * Pontos de Presença (Edge Locations) para reduzir a latência usando melhores rotas.
    * Não precisam estar localizados na mesma área das regiões
  * São usados caches para buscar o conteúdo.
* A infra é elástica e escalável, tem tolerância a falhas e alta disponibilidade.

## Serviços
* Existem 23 categorias de serviços, e cada uma delas tem os seus serviços próprios.
* Serviço de Armazenamento: S3, EBS, EFS e Glacier.
  * O Glacier permite que sejam armazenados conteúdos que não são mexidos com tanta frequência, saindo mais barato.
  * Da pra armazenar sites estáticos no S3, e sai mais barato.
* Serviço de Computação: EC2, EC2 Auto Scaling, ECS, EC2 Container Registry (ECR), Elastic Beanstalk, Lambda, EKS, Fargate.
  * O EC2 é uma máquina virtual.
* Serviços de Banco de Dados: Relacional (ARDS), Aurora, Redshift, Dynamo DB.
  * Aurora é para mysql e postgresql.
  * Redshift é para performances analíticas.
  * Dynamo é para bancos não relacionais.
* Rede AWS e serviço de entrega de conteúdo: VPC, Elastic Load Balancing, CloudFront, Transit Gateway, Route 53, Direct Connect, VPN.
  * VPC são redes isoladas de serviços, parecido com a network do docker.
  * Route 53 para DNS.
* Serviços de Segurança: IAM, Organizations, Cognito, Artifact, Key Management e Shield.
  * IAM gerencia o acesso aos recursos.
  * Cognito autenticação para apps e sites.
  * Shield é tipo um firewall.
* Serviços de Gerenciamento de Custos: Custo da AWS e relatório de uso, Orçamento (budgets), Custo da AWS Explorer.
* Serviços de de Gerenciamento e Governança: Console de Gerenciamento, Config, CloudWatch, Auto Scaling, CLI, Trusted Advisor, Well-Architected Tool, CloudTrail.
  * Cloudwatch é usado para monitorar recursos.
  * O Cloudtrail monitora o uso das APIs.