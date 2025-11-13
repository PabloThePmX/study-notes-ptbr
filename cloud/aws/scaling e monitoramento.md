# Auto Scaling e Monitoramento

## Elastic Load Balancing
* Distribui o tráfego de entrada do aplicativo/rede entre vários destinos em uma única zona ou várias zonas de disponibilidade.
* Escala o load balancer a medida que o tráfego muda.
* Três tipos de load balancers, baseado nas camadas do modelo OSI:
  * Application Load Balancer: Balanceamento de carga de tráfego HTTP e HTTPS.
  * Network Load Balancer: Balanceamento de carga em tráfego TCP, UDP e TLS.
  * Classic Load Balancer (geração antiga): Balanceamento de carga em HTTP, HTTPS, TCP e SSL.
* Para o application e network load balancer, é registrado um destino em grupos de destino, enquanto no clássico são registradas as instancias com load balancer.
* O listener verifica se há solicitações de conexão.
* Da pra monitorar o load balancer usando as métricas do CloudWatch, logs de acesso e logs do CloudTrail.

## Amazon CloudWatch
* Com o CloudWatch é possível monitorar, coletar informações, criar alarmes e disparar eventos sobre os recursos usados.
* Nele da pra setar uma métrica que caso bater, ou ficar abaixo, vai disparar um evento para o SNS, lambda, EC2, etc.
* Os alarmes são enviados pelo SNS (Amazon Simple Notification Service).

## EC2 Auto Scaling
* A escalabilidade é a habilidade de aumentar ou diminuir a capacidade baseando-se na demanda.
* Importante para "flutuar" a capacidade.
* Adiciona ou remove automaticamente instâncias do EC2 de acordo com as condições definidas.
* Substitui automaticamente instâncias danificadas.
* Várias opções de escalabilidade: Manual, programada, dinâmica ou sob demanda e preditiva.
* Um grupo de Auto Scaling é um conjunto de instâncias do EC2 que são tratadas como um agrupamento lógico para fins de escalabilidade automática e gerenciamento.
  * Da pra especificar o número mínimo e máximo de instâncias.
    * Tamanho mínimo, desejado e máximo.
* É usado com uma configuração de execução.
* A escalabilidade preditiva precisa de pelo menos 1 dia para que possa estudar o padrão de usos, para que possa prever e fazer a escalabilidade automaticamente e preditivamente.
* Da pra usar o CloudWatch para disparar um evento e acionar o Auto Scaling.
* O Auto Scaling chama o Load Balancing para avisar das novas instâncias.
* Existe também o AWS Auto Scaling.
  * Ele é usado para escalar vários recursos, como ECS, DynamoDB e Aurora.