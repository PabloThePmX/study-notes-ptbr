# API

**TODO: Ajustar e colocar a palavra "Endpoint" onde estaria correto**

### O que é uma API
* Application Programming Interface é uma comunicação que ocorre entre softwares e computadores.
  * A API é a intermediação dessa comunicação.
  * A API pode ser online ou offline, existem dos dois tipos.
* Exemplo do restaurante
  ***TODO: COLOCAR A IMAGEM AQUI**
  * O cliente faz o pedido, o garçom recebe, envia para a cozinha e aguarda receber o que foi pedido, logo após, o garçom pega o pedido e envia de volta para o cliente.
* Outro exemplo: Sistemas de e-commerce costumam usar APIs para enviar a confirmação da compra para a empresa de transporte, confirmado para onde o produto X deverá ser enviado.
  * Quando queremos saber quanto tempo vai demorar para chegar um produto, é feita também uma requisição para a empresa de transportes, que vai retornar essa estimativa.
  * Ambas as empresas, não irão consultar diretamente o banco de dados uma da outra, vai ser a API a responsável por fazer isso.
* APIs podem ser internas, ou seja, que não estão expostas na internet, e estão disponíveis apenas dentro de uma organização.  
  * Podemos também ter APIs externas, que estão expostas na rede, e podem ser acessadas por terceiros, que estão fora da organização.

### Request e Response
* O requisito é aquilo que estamos enviado.
  * Devemos seguir exatamente o que a requisição pede, enviando os parâmetros corretos para enviar um erro 404 (que não encontrou nada)
* A response vai ser a resposta contendo os valores requisitados.
* Isso tudo pode ser encontrado nas documentações das APIs
* **TODO: Explicar Fetch** 

### Verbos HTTP
* POST: Ação de CREATE, ou seja, colocando uma nova informação na api.
* GET: Ação de READ (SELECT), relacionado ao retorno de uma informação.
* PUT: Ação de UPDATE, vai atualizar um recurso existente, precisa enviar todos os valores das colunas da entidade.
* PATCH: parecido com o PUT, porém aqui não é preciso enviar todas as informações da atualização, ou seja, uma atualização parcial.
* DELETE: Apaga o registro.

**TODO: COLOCAR IMAGEM DA TABELA DOS VERBOS HTTP**

# Exemplos de APIs

### Nager.Date (TODO: COLOCAR LINK)
* É uma API que retorna os feriados públicos de todos os países.
* Retorna até os feriados por diferentes anos
* Ela espera receber por parâmetros o ano e o código do país (BR)
* O resultado vai ser um JSON contendo todos os feriados e as datas do ano designado daquele país.

### DogApi
* Imagens aleatórias de cachorros
* Vai retornar uma imagem JPEG
* Nos parâmetros, podemos especificar qual a raça de cachorro que queremos que retorne nas fotos