# Functions

* Functions são códigos SQL que você pode armazenar diretamente no banco de dados, parecido com um procedimento, mas com limitações, como por exemplo, precisam sempre ter um retorno, e aceitam apenas parâmetros de entrada.
  * A diferença principal entre entre procedimento e função, seria realmente que a função tem que retornar obrigatoriamente uma variável, um valor.
  * Seria como as built in functions, porém, criadas pelo programador.
* Para criar a função (vai ser criado no banco, e depois é só chamar, enviando os parâmetros): 
```sql
    CREATE FUNCTION Nome(@Parametros TIPO())
    RETURNS Tipo
    BEGIN
        RETURN -- A função que queremos fazer
    END
```
* Ele salva na pasta de funções no banco.