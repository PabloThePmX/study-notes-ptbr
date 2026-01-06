# Tipos de Memória

* Existem os tipos de memória Stack e Heap.
* Dependendo da declaração, ela pode ir para um lugar ou outro.
* Stack é estática, e heap é mais dinâmica.

## Stack

* A variável vai pro stack.
* O stack é tipo a pilha, o último a entrar é o primeiro a sair.
* Na hora da limpeza de memória, ele limpa nessa ordem
* O stack armazena o nome e o valor da variável.
* A stack envia isso para a memória ram.
* Já na declaração de um objeto, a variável vai ser salva no stack com um referência para o heap.

## Heap

* A heap vai armazenar os objetos mais complexos (inteiro, string, etc são muito simples), enquanto um objeto de uma classe pode ter diversos valores (nome, sobrenome, idade, etc).
* A memória stack e heap de um objeto se comunicam pela referência (ponteiro?) do objeto na stack.
* O Garbage Collector (GC) é quem limpa a memória heap após a execução.
  * Ele vai limpar todas as memórias que não possuem mais referências da stack.
* Uma variável de um tipo de valor contém uma instância do tipo.
  * Contém a variável com seu valor na stack
  * São os tipos primitivos (mais simples) (boolean, int, string, etc.)
* Uma variável de um tipo de referência contém uma referência a uma instância do tipo.
  * Contém um referência para a uma instância da memória heap.
  * Contém instância na stack e na heap.
* A heap não tem ordem específica para armazenar ou remover os dados como tem na stack
* Se tem duas variáveis complexas usando o mesmo valor (Ex:. `p1 == p2`), são criadas duas variáveis na stack que referenciam uma (a mesma) instância no heap.
  * Ou seja, as duas variáveis apontam para o mesmo objeto no heap.
  * Ou seja, se alterar um, o outro altera também.
  * Ao copiar um objeto do tipo completo, alimentar ele com ele mesmo não cria um objeto novo, pois os dois vão referenciar a mesma coisa.
  * O `new` da declaração vai criar um objeto diferente, é isso que cria uma instância no heap.
  * Os tipos primitivos não sofrem com isso.
