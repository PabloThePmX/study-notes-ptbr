# Redes VPC

* O IPv4 é 32 bits e o IPv6 é 128 bits.
* O CIDR informa quantos bits de um IP são fixos.
* O VPC é um serviço que permite provisionar uma seção isolada pra executar recursos da AWS em uma rede virtual
* Fornece controle sobre intervalos de IP, sub redes, rotas e gateways dentro do VPC.
  * Da pra criar sub redes públicas (que possuem acesso a internet) ou privadas.
* Pode usar várias camadas de segurança.
* Cada sub rede pode estar presente em uma zona de disponibilidade diferente.
  * Porém uma sub rede não pode ter mais de uma zona de disponibilidade.
* Ao criar o VPC, é preciso atribuir o bloco CIDR e não é possível alterar essa faixa após a criação.
  * O maior tamanho CIDR é /16 e o menos /28.
* Da pra fazer com IPv6 também.
* Existem 5 faixas de IPs reservadas, duas são do padrão de rede e outras 3 são por causa da AWS.
* Da pra ter um IP elástico.
  * Pode ser remapeado a qualquer momento.
* Uma interface de rede elástica é uma interface que é possível anexar a uma instância e separar da instancia para redirecionar o trafego de rede para outra.
* A tabela de rotas contém um conjunto de regras ou rotas para direcionar o trafego da sub rede.
* Cada sub rede deve estar associada a uma tabela de rotas (e no máximo uma).
  * Por padrão contém uma rota local (comunicação que nunca sai do VPC).
  * A tabela de rota é automaticamente criada junto ao VPC.
* O gateway de internet faz para do VPC.
* Tem gateway NAT.
* Da pra compartilhar VPCs entre organizações.
* Da pra emparelhar duas VPCs.
  * E so duas, não da pra fazer algo como uma cascata.
* AWS Direct Connect é usado para estabelecer uma conexão privada entre o VPC e uma rede corporativa que está fora da AWS.
* VPC Endpoints podem ser de interface ou gateway.
* O AWS Transit Gateway é um recurso que faz toda a conexão e configurações necessárias para a comunicação entre VPCs.
* Quando tiver 0.0.0.0/0 quer dizer que é a rede mais "aberta" possível, que no caso seria a rede que tem acesso a internet.
* O CloudFront é uma rede de entrega de conteúdo (CDN) global com pontos de presença em regiões (edge locations).
  * Procura eficiência, salvando o conteúdo em cache.
  * Paga conforme o uso.
  * Usado junto com a geolocalização do Route 53 para encontrar os melhores pontos de presença para determinado usuário. 

## Segurança
* VPCs podem ter grupos de segurança, que trabalham no escopo da instância e controlam as entradas e saídas com regras.
  * Filtra os tráficos de rede para as instancias.
  * Todas as regras são avaliadas antes da decisão de permitir o tráfico.
  * Apenas regras de permissão.
* Network ACLs são os firewalls no escopo da sub rede em si.
  * A AWS já cria alguns por padrão.
  * Tem as regras de entrada e saída.
  * As regras são avaliadas dem ordem numérica antes de permitir o tráfico.
  * Regras de permissão e negação.

## Route 53
* Serviço de resolução de DNS da Amazon.
* Compatível com IPv4 e IPv6.
* Vários tipos de roteamento, como simples, round robin, latência, localização (tanto dos usuários como dos recursos), etc.
  * A geográfica permite fazer a resolução para o recurso no idioma da localização, com os recursos específicos daquela região, etc.
* Da pra ter um site estático (splash page) de failover, que vai redirecionar quando o site primário der problema.