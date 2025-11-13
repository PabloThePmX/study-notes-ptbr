# Databases

* Existem serviços gerenciados e não gerenciados.
  * Os não gerenciados são controlados pelo usuário, definindo a escalabilidade, tolerância e afins, enquanto os para os gerenciados, os serviços mantém essas responsabilidades.

## Amazon Relational Database Service (RDS)
* O RDS é um banco relacional gerenciado, ou seja, é um banco que escala automaticamente conforme o uso.
* Pode-se usar vários mecanismos de banco, como MySql, Aurora, SQL Server, PostgreSQL, etc.
* Geralmente fica em uma sub rede privada.
  * O próprio RDS permite criar uma sub rede pelo dashboard do serviço dele na AWS. 
* Da pra ter um deploy de múltiplas zonas de disponibilidade, ou seja, os dados são replicados de forma assíncrona para outra zona em uma instância do RDS em espera.
  * Se a DB principal falhar, a AWS automaticamente vai buscar os dados na instância RDS em espera, tornando-a a principal.
* Busca a DB via DNS.
* Da pra ter uma instância apenas de leitura (réplica).
* Faturamento é feito por hora e pela capacidade física do banco.
* Pode-se ter instâncias sob demanda ou reservadas.
* Ao acessar o IP da aplicação web, é possível alterar os registros das tabelas do RDS na web page (ao menos no lab foi possível).

## Amazon DynamoDB
* Banco de dados NoSQL
* Armazenamento praticamente ilimitado.
* Pode usar chave única ou chave composta.
  * A única contém apenas a chave de partição, enquanto a composta contém a de partição e de classificação.
* Os atributos são os valores que não são chave.
  * Por ser NoSql, cada item pode ter diferentes atributos.
  * É um elemento de dados fundamental.
* Da pra popular as tabelas usando arquivos json.

## Amazon Redshift
* Usado para armazenar e analisar dados do banco com consultas analíticas complexas (em SQL).
  * Data warehouse (EDW) e big data.
* Separado em diversos nós, tendo um que é considerado o nó líder e os outros são de computação densa.
* Compatível com ferramentas BI.
* Pode ser usado como um SaaS para providenciar análises para serviços.

## Amazon Aurora
* Banco de dados de nível empresarial compatível com MySQL ou PostgreSQL.
* Automatiza tarefas demoradas, como backups, recuperação, detecção de falhas (ao detectar, reinicia mais rápido e eficiente), provisionamento, etc.
* Foi criado com ênfase em alta disponibilidade.
* Os dados são replicados automaticamente para três zonas de disponibilidade que salvam no S3.