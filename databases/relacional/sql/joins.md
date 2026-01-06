# Joins

* O `JOIN` é o comando para juntar duas tabelas (tem vários JOINS diferentes).
* Para fazer um `INNER JOIN` e trazer a informação de mais de uma tabela de uma vez (tabelas que se relacionam entre si):

```sql
SELECT * FROM Tabela
INNER JOIN OutraTabela ON Coluna.PK = OutraColuna.FK
WHERE Tabela.Id = x
```

* Quando o nome da coluna é igual em ambas as colunas:
```sql
SELECT * FROM Tabela
INNER JOIN OutraTabela USING(ColunaId)
WHERE Tabela.Id = x
```

* Ou seja, foi feito um `SELECT` na tabela que é a PK da chave estrangeira, e então foi buscado os valores da tabela estrangeira.
* Aquele `FROM Tabela`, utilizar a tabela que possui vínculo com ambas as tabelas, quando for realizado um inner join com mais de um join (mais de uma tabela).
* A junção não pode ser aleatória, tem que ter algo (coluna) que pode se relacionar entre as duas.
  * Não precisa fazer essa junção necessariamente apenas pela FK, se as duas colunas compartilhar um valor de uma coluna igual, podemos usar isso para referenciá-las.
  * Na junção, podemos ter colunas com o mesmo nome, portanto, se não for usar o `USING` temos que colocar o nome da tabela e a coluna, para dizer qual das colunas é a que queremos.
    * Apenas caso sejam colunas ambíguas.
* Podemos colocar um `ALIAS` depois da primeira vez que o nome da tabela aparece, esse `ALIAS` deverá ser usado quando queremos falar daquela tabela no query.
* Dá pra fazer vários JOINs, porém vai ficando mais complexo, pois precisa existir relacionamento entre as tabelas da direita e da esquerda.
* Tem vários tipos de JOINs:
  * `INNER JOIN`
    * Mais comum, pois ele vai juntar dados da tabela A e B, e depois vai gerar um novo resultado com isso.
  * `RIGHT JOIN`
  * `LEFT JOIN`
  * `FULL OUTER JOIN`