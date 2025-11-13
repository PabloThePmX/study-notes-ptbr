# Recursos de Computação

* O EC2 pode ser encaixado como IaaS (VMs).
* Lambda é computação sem servidor, baseado em função.
* ECS, EKS, Fargate e ECR para containers.
* Elastic Beanstalk é um PaaS para aplicativos web.

## EC2
* Serviço de VMs.
* São chamadas de instâncias do EC2.
* São executadas a partir de Imagens de máquina da Amazon (AMIs).
  * É um modelo, nele consta o SO bem como softwares pre-instalados.
  * Da pra pegar as prontas da AWS, criar, buscar do marketplace ou até mesmo da comunidade (tomar cuidado com essa última).
  * Da pra criar uma instancia, modifica-la e criar uma AMI baseado nisso.
* Existe em todas as zonas de disponibilidade.
* O tipo da instancia determinara a memória RAM, CPU, armazenamento e performance de rede.
  * Existem diversas categorias, algumas para uso geral, para computação, memória, armazenamento e computação acelerada (machine learning).
  * Para a nomeação do tipo da instancia, por exemplo "t3.large" significa que "T" é o nome da família, "3" é o número da geração e "large" é o tamanho.
* Se atentar a largura de banda, pois o Elastic Network Adapter (ENA) suporta até 100 Gbps, enquanto o Intel 82599 apenas 10 Gbps.
* Colocar a instância em uma rede VPC.
  * Se a instância é pra estar aberta para a internet, ela precisa estar em uma rede pública (obviamente).
  * Se não especificar, a instância vai ser lançada no VPC padrão.
    * Com IP público por padrão também.
* Da pra usar funções IAM para permitir que a instância tem acesso à algum outro serviço.
  * Por exemplo, para fazer uma chamada HTTP para um bucket.
  * Dessa forma, as credencias não são salvas na VM (e não é nem recomendado fazer isso).
* É possível passar dados do usuário para uma VM usando scripts.
  * Personalizando assim a instância em tempo de execução.
  * Ele é executado na primeira vez que a instância é iniciada (por padrão).
  * Reduz o número de AMIs, pois o script é quem vai ser responsável pela configuração do ambiente.
  * Da pra usar pra instalar/atualizar softwares necessários.
    * Tipo um `apt update && app upgrade`.
* Para cada volume da instância, da pra configurar o tamanho, o tipo (HDD ou SSD), se vai ser excluído ao encarrar a instancia e se vai precisar de criptografia.
  * Possível ter o volume raiz (com o SO) e volumes adicionais.
* Os tipos de armazenamento são:
  * Amazon Elastic Block Store (EBS), usa blocos duráveis, que não são apagados ao encerrar a instância.
    * É como se tivesse um armazenamento externo, "fora" da VM.
  * Armazenamento de instancias do EC2, aqui se as instancias forem interrompidas, os dados serão excluídos.
    * Instancias com o volume root dessa forma, não permitem que sejam desligadas via API.
    * Não recomendado para deixar o SO, pois vai ser perdido e a instância não vai conseguir ser ligada.
  * Sem ser do volume raiz temos também:
    * EFS e S3.
* Uma tag é como se fosse uma forma de anexar metadados a uma instância, permitindo assim que a instância tenha um rótulo e possa ser filtrada.
  * É chave valor.
    * Um uso comum é a chave "nome" com o valor sendo o nome dado, e é desse local que a AWS vai preencher a coluna de mesmo nome na lista.
* O grupo de segurança é um conjunto de regras de firewall que controlam o tráfego para a instância.
  * Da pra criar regras que especificam a origem e as portas que podem ser usadas.
    * Especificando a porta e o protocolo e a origem sendo o endereço IP ou outro grupo de segurança.
  * Existe fora do SO.
  * Por padrão o grupo permite todo o tipo de tráfego.
* Da pra especificar um par de chaves para acessar a instância.
  * Consiste em uma chave pública que a AWS armazena e uma privada armazenada.
  * Com essa chave da pra fazer o login como admin nas VMs ou obter um acesso SSH.
  * Só da pra pegar a chave privada no momento da criação.
* As instâncias podem ser criadas de forma programática (CLI ou SDK). 
* O IPv4 público externo é alterado caso a instancia foi interrompida.
  * Se precisar de um IP persistido, é necessário utilizar um endereço de IP elástico.
* Da pra pegar os metadados da instancia acessando `/latest/meta-data` e para pegar os dados do usuário especificado acessando `/latest/user-data`.
  * A partir disso da pra criar um script que lê essas informações para usar em outro local.
* Usar o Amazon CloudWatch para monitorar as instâncias.
  * O monitoramento básico (dados são enviados a cada 5min) é gratuito, mas o detalhado (dados enviados a cada 1min) tem taxa mensal fixa.

### Otimização de Custos do EC2
* Existem modelos de definição de preço sob demanda, com host ou instâncias dedicadas (por causa de licenciamentos), instâncias reservadas, instâncias reservadas programadas e instâncias spot.
  * As reservadas são com pagamento integral.
  * A spot muda o valor conforme a demanda de uso (flutua o valor).
    * Executa apenas quando esteja conforme a sugestão de preço.
    * Pode ser encerrada após dois minutos de receber a notificação da amazon.
* Para otimizar custos, é necessário definir o tamanho certo, aumentar a elasticidade, definir o modelo igual e otimizar as opções de armazenamento.
* Usar o CloudWatch para verificar o quanto está sendo usado.
* Utilizar a escalabilidade automática para atender as necessidades conforme o uso.

## Serviços de Container
* O Amazon Elastic Container Service (ECS) é usado para gerenciar containers.
* Ele orquestra a execução dos containers.
* Permite o uso de recursos de outros serviços da AWS.
* Distribui os containers nos clusters, de forma que não sobrecarregue nenhum.
* Se for definido gerenciar os clusters do ECS, vai ser criado um cluster do ECS baseado no EC2, que fornece mais controle sobre a infraestrutura.
  * Caso não for gerenciado, vai ser criado um ECS baseado no Fargate, que é mais fácil de manter pois tem foco em seus aplicativos.
    * O cluster vai ser gerenciado pela AWS.
    * Quase como um IaaS e PaaS.
* Existe um serviço que permite executar o Kubernetes na AWS chamado Elastic Kubernetes Service (EKS).
* O Amazon ECR é um serviço de container gerenciado do Docker, que facilita o armazenamento e gerenciamento de imagens Docker.
  * O ECS podem buscar a imagem do ECR.

## AWS Lambda
* Sistema de computação sem servidor.
* É uma função executada em decorrência de algum gatilho (evento).
  * Pode ser por valores, horário (CloudWatch), erros, etc.
* O valor é descontado somente pelo tempo que for utilizado.
* Pode rodar até 15min, após isso ele encerra automaticamente.
  * Da pra setar timeouts para menos que 15min.
* A alocação máxima de memória para uma função é 3008 MB.
* Oferece suporte a várias linguagens de programação.
* Da pra orquestrar várias funções.
* Alguns serviços podem chamar a função diretamente.
* Definir as permissões que a função tem para se comunicar com outros serviços.
* Ao criar o lambda, da pra setar diversos gatilhos e destinos.

## AWS Elastic Beanstalk
* Uam maneira de colocar aplicativos web em execução.
* Serviço gerenciado que lida automaticamente com provisionamento da infra, implantação, balanceamento de carga, escalabilidade, log, etc.
* Oferece suporte para várias linguagens de programação.
* Implanta em servidores como Apache, NGINX, IIS, etc.
* Ele faz todo o processo de implementação, e o usuário somente envia o código.
* Da pra pegar o código diretamente do github.
* Ele cria instâncias EC2 que rodam recursos necessários para que a instância do Beanstalk funcione normalmente.