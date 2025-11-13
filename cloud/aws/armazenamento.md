# Armazenamento

## Amazon Elastic Block Store (EBS)
* Dados persistentes (não volátil) para EC2.
  * São anexados as instâncias, pois eles podem ser criados separadamente.
* Existe diferença entre armazenamento em bloco (que nesse caso é o EBS) e de objetos.
  * O de bloco altera so uma parte, enquanto o de objeto precisa atualizar todo o arquivo, mesmo que tenha sido uma alteração pequena.
  * O de bloco costuma ser mais rápido.
  * Esse de bloco é como a maioria dos armazenamentos do computador funcionam.
* Pode ter backup automático por meio de snapshots no S3.
  * Os snapshots são backups incrementais.
* Da pra escolher entre HD ou SDD.
  * Somente SSDs podem ser usados como boot.
* Tem snapshots, criptografia e elasticidade.
* Por ser elástico, da pra aumentar a capacidade e o tipo (HD e SSD).
* O custo do SSD é calculado pela quantidade de GB alocada no mês, enquanto o HD (magnético) é cobrado pelo número de solicitações para o volume.]
* A transferência de dados de entrada e gratuita, enquanto a de saída entre regiões gera cobrança.
* Dependendo vai ser preciso montar o armazenamento na instância depois de anexa-lo.
  * Ou fazer um resize caso ele já existe para quando ele foi aumentado ou foi criado baseado no snapshot mas com tamanho diferente.
* O EBS precisa estar na mesma zona que o EC2.

## Amazon Simple Storage Service (S3)
* Armazena arquivos como objetos e não blocos.
  * Objetos em bucket.
* Cada bucket pode ter seu acesso configurado usando o IAM.
* Por padrão armazena dados em pelo menos três zonas de disponibilidade.
* As classes do S3 são: Standard, Standard - Infrequent Access, Intelligent, One Zone, Glacier e Glacier Deep Archive.
* O S3 glacier permite armazenar dados que não precisam ser buscados com tanta frequência.
  * Tem o glacier deep archive que é ainda mais barato.
    * Pode ser usado quando uma empresa precisa legalmente guardar documentos por 10 anos ou mais.
* Para colocar objetos no bucket, primeiro é necessário criar um bucket em uma região, depois fazer o upload dos objetos via endpoint.
  * Existem dois tipos de URL para o bucket.
* Da pra armazenar sites estáticos nele.
* Só entra no custo os GBs por mês usados, as transferências para fora ou para outras regiões e as solicitações HTTP.
  * As taxas de requisições GET são diferentes.
  * Existe a requisição do tipo COPY, que faz algo como um GET + PUT.
* O nome do bucket precisa seguir padrões de DNS, pois vai ser usado na url.
  * Por isso o nome precisa ser único.
* Existem eventos que podem ser configurado para notificar quando um objeto e armazenado ou deletado.
  * Isso pode ser usado com o Lambda.

## Amazon Elastic File System (EFS)
* Um tipo de armazenamento que várias instâncias podem acessar ao mesmo tempo.
  * Um tipo de armazenamento compartilhado.
* Compatível com AMIs baseadas em Linux.
* Precisa ser montado nas instâncias que vão utiliza-lo.
  * O painel do EFS disponibiliza o comando exato que precisa ser executado no terminal.
* Obviamente precisa estar na mesma VPC que as instâncias.
  * E estar na sub rede correta.
* O grupo de segurança precisa permitir o acesso da instância para o EFS e vice versa.

## Amazon S3 Glacier
* Armazenamento de baixo custo.
* Costuma ser usado para arquivamento de longo prazo, pois costuma demorar para estar apto a pegar um arquivo.
  * Ele primeiro precisar restaurar o objeto, para então ficar disponível.
* Fornece três opções de acesso à arquivos: expresso (mais cara pois permite recuperar o arquivo em minutos), padrão e em massa.
* Vault Lock impõe a conformidade por meio de uma política.
  * O Vault é um contêiner para armazenar os arquivos.
* Da pra salvar no glacier usando requisições, SDKs ou o próprio S3 com ciclo de vida.
  * O ciclo de vida do S3 permite que os objetos sejam movidos para o glacier ou excluídos após um tempo pré determinado.
* Como ele não é usado para buscar a todo momento, o custo por requisição é maior que o de um S3 normal.
* Diferente do S3 padrão, no glacier a criptografia é uma etapa opcional, e não por padrão.
* Costuma não ser acessado pela interface, mas sim de forma programática.