# SOLID

* Representa os 5 princípios que facilitam o processo de desenvolvimento.
* São fundamentais na POO.
* Foi criado por Robert C. Martin, mas a sigla em si surgiu mais tarde por Michael Feathers.

## S - Single Responsibility Principle
* Cada classe deve ter um, e somente um motivo para mudar.
* A classe não pode ter várias responsabilidades totalmente distintas e únicas.
* Uma dica é colocar o nome da classe com tudo que ela é capaz de fazer, e se o nome ficar muito longo, pode significar que ela deve ser refatorada.

## O - Open Closed Principle
* Entidades de software (classes e métodos) devem estar abertas para extensão, mas fechadas para modificações.
* A ideia não é adicionar mais recursos, mas sim adaptar o código deixando capaz de estende-lo.
* Costuma-se usar interfaces para representar métodos genéricos, onde cada classe adapta-o (implementa) da forma que achar necessário.
* Substitui a "obrigação" de alterar alguma condição para comportar uma nova opção, pois essa modificação pode ocasionar erros.

## L - Liskov Substitution Principle
* Classes derivadas (ou classes filhas) devem ser capazes de substituir suas classes base (ou classes mães).
* Uma classe filha deve ser capaz de executar tudo que sua classe mãe faz, o que se encaixa muito no princípio de polimorfismo.
* Ambas as classes (mãe e filha) devem funcionar caso fossem substituídas umas pelas outras.

## I - Interface Segregation Principle
* Uma classe não deve ser forçada a implementar interfaces e métodos que não serão utilizados.
* Criar interfaces específicas, e ir implementando todas as que se fazem necessárias naquela classe.

## D - Dependency Inversion Principle
* Dependa de abstrações e não de implementações concretas.
* Abstrações não devem depender de detalhes (implementações concretas), mas detalhes devem depender de abstrações.
* O conceito da injeção de dependência é baseado neste princípio.
* Prioriza o baixo acoplamento.
* A classe de baixo nível é a concreta, enquanto a de alto nível é a mais abstrata, pois orquestra a interação entre vários componentes.