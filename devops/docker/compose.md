# Docker Compose

* Vai estruturar os comandos de inicialização de containers em um arquivo `.yaml`.
  * Orquestrador de containers, pois auxilia a inicialização de vários containers.
* Costuma-se usar o nome `{NOME}-docker-compose.yaml`.
* Começa dizendo a versão do compose com `version: '3'`.
  * Sendo a 3 a última disponível.
* Em um segundo momento, colocar o comando `services:` e abaixo listar todos os containers (pelo nome).
* Dentro do nome do serviço, especificar qual vai ser a imagem usando o comando `image:{NOME IMAGEM}`.
* Junto da imagem, logo abaixo especificar as portas com `ports:`
  * Para especificar as variáveis de ambiente, usar o `environment`.
* Não precisa setar a network, pois se está dentro do compose quer dizer que todos estarão na mesma rede.
  * Ou seja, o compose vai cria-la.
* Exemplo de um docker compose que vai criar um servidor MongoDB com a GUI MongoExpress.
```yaml
version: '3'
services:
  mongodb: 
    image: mongo
    ports:
      - 27017:27017
    environment:
      - MONGO_INITDB_ROOT_USERNAME=admin
      - MONGO_INITDB_ROOT_PASSWORD=password
    volumes:
      - db-data:/var/lib/mysql/data
  mongo-express:
    image: mongo-express
    ports:
      - 8080:8081
    environment:
      - ME_CONFIG_MONGODB_ADMINUSERNAME=admin
      - ME_CONFIG_MONGODB_ADMINPASSWORD=password
      - ME_CONFIG_MONGODB_SERVER=mongodb
volumes:
  db-data:
    driver: local
```
* Como é um arquivo yaml, é necessário respeitar a identação.
* Para executar o compose, rodar o comando `docker compose -f {ARQUIVO YAML} up`.
  * Usar `down` para parar os containers.
    * Ele remove a rede também.
* Os logs ficam juntos.