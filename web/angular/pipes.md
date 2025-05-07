# Pipes

* São funções prontas para transformar um dado.
* Ele é usado com o `|`, e chama a função da seguinte forma: `variável | método`
  * Isso dentro do HTML, caso for no TS, declarar a classe (o pipe) e chamar o método dentro dela.
    * Porém costuma-se usar mais o pipe no HTML.
  * Precisa importar o pipe no componente.
* Existem métodos de UpperCase, LowerCase, datas, title case (para deixar a primeira letra maiúscula) e afins.
* Da pra colocar vários pipes em uma variável.
* É possível criar pipes.
  * Usando o `ng g p` no cli, ele vai criar um arquivo de pipe.
  * Ele precisa ser importado no componente que vai utiliza-lo.
  * Da pra criar pipes que formatam cpf, telefone, etc.
* Pipes podem receber parâmetros.
  * Para enviar os parâmetros: `pipe: "valor1":"valor2"`
  * O pipe precisa declarar os parâmetros recebidos na sua assinatura, como qualquer outro método.