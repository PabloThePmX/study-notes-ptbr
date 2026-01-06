# Criação de Tabela

* A sintaxe básica para criar uma tabela:
```sql
CREATE TABLE Tabela (
    Coluna Tipo (Tamanho) PRIMARY KEY NOT NULL, --o NOT NULL aqui seria redundante, pois primary key não permite ser nulo
    Coluna2 Tipo2 (Tamanho2)
)
```
* Usar `NOT NULL` depois de um tamanho para dizer quando o campo é de preenchimento obrigatório.
  * O contrário pode ser colocado como `NULL` (porém ele já faz isso implicitamente)
* Para o ID podemos usar o tipo `IDENTITY` que é um tipo que vai se auto incrementando.
* A `PRIMARY KEY` garante que o nosso código vai ser único (colocar isso no ID).
* Para fazer a referência da FK:
```sql
CONSTRAINT FK_Nome FOREIGN KEY(ColunaFKDaTabelaAtual)
REFERENCES Tabela(ColunaPKDaOutraTabela)
```
* `FK_Nome` é o nome da restrição, da pra colocar o que quiser (geralmente bota o nome das duas tabelas que estão se comunicando, com o FK na frente do nome)