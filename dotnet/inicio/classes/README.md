# Construtores
* Os construtores permitem que o programador defina valores padrão, limite a instanciação e grave códigos flexíveis e fáceis de ler.
  * Permite colocar valores padrão em uma classe no momento de sua instanciação.
  * Obriga o usuário a enviar os valores para o construtor
* Por convenção, o construtor é o primeiro item a ser declarado em uma classe.
  * A sintaxe para criar um construtor: 
  ```C#
    //o nome do construtor vai ser o nome da classe atual
    public Pessoa() {
      //o código que vai executar quando entrar no construtor
    }
  ```
  * O construtor não tem retorno.
  * Como parâmetro do construtor, é preciso declarar as variáveis das propriedades que queremos usar nele (diferente das já declaradas na classe).
    * Assim, na hora da declaração, podemos passar os valores que queremos usar por parâmetro.
  * Podemos criar o mesmo construtor (com o mesmo nome) porém sem parâmetros também, assim, cabe a nós decidir se queremos enviar valores no parâmetro ou não.
    * Ou seja, ele tem overloads
* Dentro do construtor, alimentar as propriedades com os valores vindo por parâmetro.
  * Ou seja, dentro do construtor será definido onde esses valores irão ir e como serão usados.
* Nos parâmetros enviados, podemos colocar “<nome>:” antes do valor para dizer o que é.
  * Porém precisa ser igual ao nome da variável na declaração do construtor.
