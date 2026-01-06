# Manipulando Dados

## Built-in Functions

* Built-in functions são funções pré-existentes no BD.
  * Podemos usar condições nessas functions.
* O `Count` vai contar quantos registros tem na tabela
  * `SELECT COUNT(*) NomeNovaColunaOpcional FROM Tabela`
    * Retorna somente a contagem.
    * Antes do `FROM`, com qualquer function, dá pra colocar um nome para a coluna de resultado da Function.
    * Da pra colocar o `GROUP BY` para saber por exemplo, a quantidade de vezes que aparece aquele valor.
* Função `SUM` para retornar a soma dos valores de uma coluna.
  * `SELECT SUM(Coluna) FROM Tabela`
* Função `MAX` para descobrir o maior valor de uma coluna
  * `SELECT MAX(Coluna) FROM Tabela`
* Função `MIN` para achar o menor valor de uma coluna.
* Função `AVG` para encontrar a média de valor de uma coluna.
* Para colocar os valores da coluna em maiúsculo e minúsculo
  * `SELECT UPPER(Coluna) FROM Tabela`
  * `SELECT LOWER(Coluna) FROM Tabela`
* O `GETDATE` é uma função do SQL que pega a data e a hora atual.

## Formatação

* Para concatenar valores entre colunas
  * `SELECT Coluna + ' - ' + Coluna2 FROM Tabela`
* Podemos usar o `FORMAT` para formatar a visualização de uma coluna.
  * Para ela funcionar, colocamos a string contendo o jeito que queremos que concatene.
  * É feito de uma maneira muito parecida com aquela do C#
  * É bom para ser usado em datas.
