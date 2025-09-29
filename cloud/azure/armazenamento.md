# Armazenamento

## Azure Blob Storage
* Blob = Binary Large Object.
  * Armazena qualquer coisa, pois é binário.
* Salva arquivos (não estruturados) como imagens, videos, logs, backups, etc.
* Da pra salvar arquivos de aplicações.
* Precisa criar uma conta de armazenamento na Azure.
* Criar um container nessa conta de armazenamento.
  * É como se fosse uma pasta.
* Tem o nível de acesso como container também, pois ai permite que o container e seus arquivos sejam lidos por fora.

### Para se conectar ao storage via api
* No `appsettings` colocar duas chaves, uma da connection string do blob storage, e outra com o nome do container, ambas vão ser pegas no controller para que o storage possa ser gerenciado.
  * Pegar a connection string com a chave de acesso na aba "Chaves de acesso" no portal Azure.
    * Se gerar uma nova chave, a antiga vai ser invalidada.
* Para acessar o storage, instalar o pacote `Azure.Storage.Blobs`.

### Upload
* No endpoint da API, receber um arquivo do tipo `IFormFile`.
* Usar o client `BlobContainerClient` para inicializar o storage.
  * Na hora de instanciar, mandar a connection string e o container name.
* Após instanciar o blob container, alimentar o `BlobClient` com o `GetBlobClient(<IFormFile.FileName>)`.
* Para fazer o upload:
```c#
using var data = arquivo.OpenReadStream(); //vai ler o arquivo e transforma-lo em stream
blob.Upload(data, new BlobUploadOptions { //vai mandar a stream do arquivo mais a opção dizendo qual o tipo dele
    HttpHeaders = new BlobHttpHeaders { ContentType = arquivo.ContentType}
});
```
* Depois disso, da pra retornar a `Uri` do blob recém armazenado.

### Download
* Para encontrar e ler o container, é so fazer o `GetBlobClient`, então na hora de fazer o download, da pra começar dessa forma.
  * Enviar por parâmetro no `Get`, o nome do arquivo que iremos baixar.
    * Com a extensão.
* Primeiro fazer um `exists` para verificar se esse blob no container existe.
* Usar o `blob.DownloadContent()` para baixar o arquivo requisitado.
* Na hora de retornar, retornar o valor do conteúdo em binário.
  * Retornar junto o tipo do conteúdo, para isso, buscar no `blob.DownloadContent().Value.Details.ContentType` do conteúdo baixado do blob.
  * E o nome também deve ser retornado, portanto pegar o nome presente no blob.

### Delete
* Inicializar o container novamente.
* Fazer o `blob.DeleteIfExists(<NOME ARQUIVO>);`.
* Retornar o `NoContent`.

### Listar Blobs do Container
* Criar um DTO para o retorno do blob.
* Usar o mesmo client e fazer um `foreach` no `GetBlobs()`.
  * Alimentar os valores no Dto.

## Azure Tables
* É um serviço que armazena grandes quantidades de dados NoSQL em tabelas na nuvem, como chave/valor.
* Fica dentro da conta de armazenamento também.
  * Ao invés de selecionar containers, selecionar "Tabelas".
* Geralmente se usa um programa chamado `Azure Storage Explore` para verificar os registros de uma tabela.
  * Mesmo que exista como ver as tabelas pelo portal do Azure (na parte de `Navegador de Armazenamento`).
  * Da pra conectar em uma so tabela, ou na conta em si (dai marcar o `default directory`).
* Colocar novamente a connection string no `appsettings`
  * Bem como, o nome da tabela.
* Obter essas informações no controller.
* Instalar o pacote `Azure.Data.Tables`.
* Criar um model de como vai ser a tabela e nesse model implementar a interface `ITableEntity` (só deixar as propriedades implementadas, não precisa mudar nada).

### Inserir
* Usar o cliente `TableServiceClient` com a connection string e fazer um `GetTableClient` mandando o table name por parâmetro.
* Fazer um `CreateIfNotExists` para criar caso não exista a mesma.
* Alimentar um GUID no `RowKey` e o `PartitionKey` com algum valor para ser particionado (GUID, estado, cidade, etc).
* Usando o cliente, chamar o método `UpsertEntity` enviando a entidade recebida e alimentada.
  * Cria o registro se não existir, porém se existir só atualiza (a `RowKey` seria tipo a PK).
* Enviar no POST somente as informações (propriedades) da tabela em si, e não essas outras implementadas pela interface.

### Atualizar
* Recebe o id e o valor no endpoint.
* Usando o cliente, pegar a entidade com o `GetEntity<MODEL>(<ROW ID>, <PARTITION BY>).Value`.
* Com a entidade em uma variável, atualizar os valores manualmente e depois chamar o `UpsertEntity` também.
* A lógica é basicamente a mesma do inserir, porém, aqui ele vai pegar a entidade e usar o mesmo método para inserir, visto que esse método server para adicionar ou atualizar o valor.

### Listagem
* Com o cliente, chamar o método `Query<MODEL>().ToList()`.
* Essa `Query` é um LINQ, portanto da pra fazer filtros e tudo mais.
  * Portanto, usando lambda da pra fazer um where `Query(x => x.id == id)`.

### Delete
* Usando o cliente também, usar o método `DeleteEntity(<ROW ID>, <PARTITION BY>)`.