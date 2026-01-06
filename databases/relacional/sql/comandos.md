# Comandos Gerais

* `ORDER BY`
  * Para alterar a ordem (crescente ou decrescente), logo após o comando colocar `DESC` ou `ASC` (esse é o padrão, então pode omitir).
  * Para ordenar por mais colunas, basta colocar as outras colunas depois de uma vírgula.
    * Ex.: `ORDER BY Nome, Sobrenome`.
* `WHERE`
  * O `WHERE` deve ir antes do `ORDER BY`.
  * Para filtrar por mais colunas ou valores, colocar `AND` ou `OR`.
  * Para filtrar valores que existem dentro de um valor (não o valor concreto em si), no `WHERE` ao invés de usar `=` colocar `LIKE`.
  * Depois colocar a `%` também (wildcard), exemplo, todos os nomes que começam com a letra "F", `WHERE Nome LIKE 'F%'`.
* `GROUP BY`
  * Usado para agrupar (juntar) todos os dados iguais de uma coluna.
* A ordem das expressões fica: SELECT, FROM, WHERE, GROUP BY e ORDER BY.

## Insert

```sql
INSERT INTO Tabela (Coluna1, Coluna 2)
VALUES (Valor1, Valor2)
```

* A ordem das colunas pode ser invertida.
* `INSERT INTO Tabela VALUES ()`, dessa vez omitindo as colunas e colocando direto os valores (ainda precisa obedecer a ordem das colunas na tabela).
* Ao fazer o `INSERT`, não é preciso declarar e passar o valor do `ID`, pois ele incrementa automaticamente pelo banco. (o identificador único do registro)

## Update

```sql
UPDATE Tabela 
SET Coluna = 'valor', Coluna2 = 'valor2' 
WHERE id = 1
```

* É MUITO IMPORTANTE colocar o `WHERE`, para dizer qual o registro que será atualizado.
  
## Delete

```sql
DELETE Tabela 
WHERE Coluna = valor --(é bom usar o ID)
```

* Como no Update, é essencial colocar o WHERE para não aplicar esse commit em tudo

## Alter

```sql
ALTER TABLE Tabela ADD NovaColuna TIPO
```

* Update para setar um valor nessa coluna depois.

## Drop Column

```sql
ALTER TABLE Tabela DROP COLUMN Coluna
```

