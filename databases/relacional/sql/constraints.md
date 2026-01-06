# Constraints

* Constraints são regras a ser seguidas na inserção em uma tabela. Alguns exemplos:
  * `NOT NULL`
  * `UNIQUE`
    * Garante um valor único na coluna em toda a tabela.
  * `CHECK`
    * Garante uma determinada condição (Ex. valor da coluna sempre maior que x)
  * `DEFAULT`
    * Define um valor padrão qual o valor caso não seja enviado o valor
  * `PRIMARY KEY`
    * Teoricamente é uma condição de NOT NULL e UNIQUE
  * `FOREIGN KEY`
* Caso as regras não forem seguidas, vai mostrar um erro.
* Dá pra nomear (colocar alias) nessas constraints.
  * Escrever depois do `CONSTRAINT` e antes do tipo da regra.
* Para alterar uma tabela existente e inserir a regra (Ex.: Unique)
```sql
ALTER TABLE Tabela
ADD UNIQUE(Coluna)
```
* No `ADD CHECK()`, dentro dos parênteses, devemos colocar a condição.
* Para adicionar a constraint default:
  * `ADD DEFAULT Valor FOR Coluna`
    * Vai adicionar automaticamente, quando omitimos o valor na inserção.
* Para apagar uma constraint de uma tabela:
```sql
ALTER TABLE Tabela
DROP CONSTRAINT NomeDaConstraint
```
