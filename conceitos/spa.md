# Camadas de Responsabilidade de uma WebApp (SPA)

* Lógica usada pelas frameworks (e libs como o React)
* Possui 4 camadas, componentes, gerenciamento de estados, roteamento e renderização.
* É possível criar sem usar framework, mas acaba sendo extremamente complexo e desnecessário, visto que a fremework fará isso por baixo dos panos.

## Components
* É a parte visual (que precisa ser renderizado), aquela que tem o HTML e o CSS.
* Customizável e reutilizável.
* Uma página é composta por componentes.

## Gerenciamento de Estados (States)
* Evita o uso excessivo de ifs, gerenciamento os estados dos componentes.
* Cuida da lógica, cuidando da "conversa" entre componentes.
* Tipo o `toggle`, ou seja, vai mudar de um estado para o outro.
* Se um componente ficar de um jeito, muda o outro.
* Bibliotecas como Flux, redux, context api, etc.
  * No angular: NGRX E NGXS.

## Roteamento (Routes)
* Responsável pela navegação da aplicação, de forma em que apenas troque a URL sem precisar recarregar toda a página.
* Vai ter uma página, e o roteamento vai dizer quais são os componentes que vão ser mostrados nela.
* Altera apenas a "última" parte da URL.
* No angular, tem o Angular RoutingModule
  * Se não usar bibliotecas, vai usar o History API por padrão.

## Renderização (Render)
* Vai processar a partir das rotas, componentes e estados
  * Ele que vai decidir a melhor estratégia para renderizar os componentes no navegador.
* Três tipos de estrategias renderização:
  * 100% Server
    * O servidor entrega exatamente o que foi pedido (com tudo montado).
  * Parte server e parte client
    * Vai receber o HTML, porém terá partes que vão ser montadas dinamicamente.
  * 100% Client
    * Tudo vai ser montado dinamicamente.
      * Por  padrão, o Angular e React funcionam assim.
    * Acaba não tendo SEO.