# Volumes (Persistência)

* Usado para não perder data ao parar ou excluir um container.
* Ele pega um caminho do host e monta dentro do sistema de arquivos virtuais do container.
* Existem 3 tipos de volumes
  * O parâmetro `-v` usado com o `docker run`, dizendo qual o caminho do host e do container (host volumes).
    * Ou seja, `docker run -v {CAMINHO HOST}:{CAMINHO CONTAINER}`.
  * Da pra criar da mesma forma porém sem especificar o caminho no host (anonymous volumes).
    * Ele cria UUIDs como nomes.
  * Ou pode-se criar uma referência para o caminho, ou seja, uma referência que da pra ser chamada apenas pelo nome (named volumes)
    * Ficando `-v {NOME}:CAMINHO CONTAINER`
    * Esse é o mais recomendado para produção, pois não limita o container a um caminho especifico na máquina do host.
* Para criar um volume no docker compose, só usar o `volumes:` e abaixo o nome e o caminho (ou os caminhos).
  * E ao final, após os services (no mesmo nível), é necessário dizer quais os volumes vamos montar, e nesse momento chamar o volume pelo seu nome.
    * Juntamente colocar uma opção com `driver: local` para dizer que localmente o caminho precisa ser criado.
* O caminho no host fica em `ProgramData\docker\volumes` no windows.