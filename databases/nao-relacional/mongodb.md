# MongoDB

* MongoDB é um banco não relacional orientado a documentos (JSON é o documento).
  * Atlas é a versão na nuvem dele.
* O Mongo também usa um sistema de autenticação.
  * Dá pra adicionar os IPs que vão ser usados, para que seja possível fazer o login.
* Para fazer a conexão, usar o `MongoDB Compass` (o compass seria a GUI, a parte visual em si).
  * Copiar a string de conexão e colocar no URI do compass
  * Colocar os dados do usuário no `Authentication`
* No compass, criar uma nova DB
* A `collection` é como uma tabela é chamada no banco não relacional
  * É uma coleção de documentos, não exatamente uma tabela.
* Para inserir um novo dado pela GUI:
  * Ir em `Add Data`
    * Podemos ter documentos com propriedades diferentes.
    * Cada documento tem um ID inteiro gerado pelo próprio Mongo
* No shell do Mongo (canto inferior esquerdo, o `mongosh`), usar o comando `use NomeDaDatabase` para colocar na database que queremos fazer a alteração (caso a mesma não esteja selecionada).
  * Para adicionar um novo valor por esse shell, colocar `db.NomeTabela.insertOne({JSON})`
  * Atualizar a collection depois.
* Para fazer um `SELECT` no compass:
  * No filter, colocar um valor com a propriedade `({“Prop: Valor”})`
    * É como se fosse o `WHERE`
* O `project` seria o local para definir quais as colunas serão mostradas
  * Usar 0 e 1 nas colunas para dizer se são visíveis ou não
* No `Sort`, colocar com 1 ou -1
  * Para definir se vai ser na ordem crescente ou decrescente.
* Para fazer o `SELECT` pelo MongoShell:
  * `db.NomeDB.find({Propriedade: Valor})`
    * Colocar uma vírgula para colocar quais colunas estarão visíveis.
    * Colocar um `.sort({PropParaOrdenar: 1 ou -1})` para a ordenação ASC ou DESC.
      * Sempre colocar `{}` nas condições.
* Podemos fazer o find usando condições de maior/igual menor/igual:
  * Colocar `$lt` (less then) ou `$lte` (less then equal) (`$gt`, `$gte`) e depois colocar dois pontos como se fosse uma propriedade.
    * Ex.: `{Preco: {$lte : 50}}`
* Para alterar um documento pela linha de comando:
  * `db.NomeDaDB.updateOne({id: x}, {$set {Preco: x}})`
    * Atualizando o valor do preço no ID x.
    * Cuidar com o filtro, pois sem filtro faz que nem no SQL, atualiza tudo.
* Para deletar um documento no MongoShell (dá pra fazer pela GUI também, como todos os outros):
  * `db.NomeDaDB.deleteOne({Id: x})`
    * Vai deletar filtrado pelo Id.
  * Tem também o `deleteMany` que vai deletar mais que um.
* Pelo site do Mongo, dá pra ver as coleções que foram adicionadas pelo compass/MongoShell