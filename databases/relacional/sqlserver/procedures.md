# Procedures

* As Stored Procedures são códigos SQL que você pode salvar diretamente no banco de dados, podendo assim aproveitar um script que é comumente usado.
* Permite chamar um procedimento que tem um código SQL, com parâmetros.
```sql
    CREATE PROCEDURE NomeProcedimento
    @NomeVar Tipo(Tamanho) 
    AS
    --Código SQL, alterando o local dos valores da variável, com o @Nome
```
* Só executar esse procedimento, que ela vai salvar na pasta `Programmability` do BD
* Para executar o procedimento:
  * `EXEC Nome @NomePar1 =  Valor1, @NomePar2 Valor2`
    * Chama o procedimento, enviando os parâmetros.
    * Pode fazer sem dizer o nome do parâmetro, direto com os valores.
* No procedimento, podemos colocar qualquer comando que podemos colocar em uma query comum.
  * Até `SELECT`, usando o valor do procedimento no WHERE.
* Nem toda a procedure precisa receber um parâmetro.