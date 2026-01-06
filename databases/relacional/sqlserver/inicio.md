# Inicio

* Há duas versões do SQLServer, a express e a dev.
  * Não há tantas diferenças entre ambas.
* Connection String é a maneira com que deve ser conectado ao banco de dados.
  * Ex.: `localhost\SQLEXPRESS` ou `dev`
* O DBMS do SQL Server é o Management Studio (SSMS).
* Dá pra mudar nas propriedades (na aba service) para que o banco inicie automaticamente ou manualmente.
* Server name é o ip (`localhost`) justamente com o `\sqlexpress` (aquela connection string)
* A autenticação pode ser feita por usuário do windows.
* Ao executar uma query, verificar se a combobox está apontando a DB certa (não alterar a DB `master`, pois ela é a do sistema)
* Usar `Ctrl+Shift+R` para dar um refresh no cache, e mostrar para o sistema quando uma nova tabela é criada.
* No query do SQL Server, podemos colocar no código o comando `BEGIN TRAN` que diz que será uma transação, e com ele um `ROLLBACK`, assim, o commit feito depois de ter colocado esse comando no query, dá a possibilidade de executar um rollback e recuperar os dados.
* Selecionar a tabela no query e clicar `ALT+F1` no SSMS mostra detalhes dela, como as regras (constraints).