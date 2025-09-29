# O que é

* Software de virtualização que cria um "pacote" (container) com tudo que a aplicação precisa para rodar.
* Sem container precisava instalar cada serviço separadamente em cada computador.
* Os containers vão buscar de imagens já existentes (como o Postgres) para utilizar esses serviços.
* Padroniza o processo de rodar um serviço.
* Usando o docker, podemos ter várias versões do mesmo programa rodando na mesma máquina.
* O Docker Artifact contém tudo que a aplicação precisa, sendo o código, configurações, dependências, etc.
  * Previne erros que poderiam acontecer por falhas humanas ou de máquinas específicas.
* Uma VM virtualiza o Kernel, enquanto o docker virtualiza apenas a camada de aplicação.
  * Um PC é composto por 3 camadas: Hardware, Kernel (o meio de tudo, faz a comunicação entre as camadas) e a de aplicação.
    * Por isso as distros de linux mudam, pois elas possuem o mesmo kernel mas camadas de aplicações diferentes.
  * Portanto o Docker usa o kernel do host, dessa forma não tem o processo de boot como uma VM tradicional tem.
* Imagens docker precisam do kernel do linux.
  * O Docker Desktop permite Windows rodar containers pois o cliente possui uma camada de Hypervisor com uma distro leve de Linux (por isso precisa executa-lo, para que o mesmo inicialize a engine).

## Imagens Docker
* É como se fosse um artifact, ou seja, um arquivo de fácil "transporte" que é usado para criar o container.
* Além de incluir o código fonte, possui também a configuração completa do ambiente, incluindo variáveis de ambiente.
* As imagens são versionadas usando "tags".
  * A tag `latest` é a última imagem especificada (e a padrão).

## Container
* É o que executa a imagem, ou seja, o ambiente que roda a imagem.
  * Uma instância que está rodando a imagem.
* Contém camadas de imagens, e geralmente a imagem base é uma imagem de um Linux leve (alpine).
  * Depois vai ter as imagens de aplicação (Postgres, etc).
    * Por isso que quando faz o pull, tem vários downloads, pois são os downloads de cada imagem (porém ele só vai baixar caso alguma das imagens não exista na máquina ainda).
* É quando o ambiente do container foi criado.
* Da pra rodar vários containers de uma mesma imagem.