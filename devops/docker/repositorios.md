# Docker Registries

* Hub com imagens prontas
* Existem imagens oficiais criadas por serviços.
* O maior é o Docker Hub.
* Existem registradores privados, geralmente são usados serviços de AWS (ECR), Google Cloud, Azure, etc.
  * O Docker Hub também permite armazenar imagens privados.
  * No ECR, cada repositório tem apenas uma imagem.
    * Mas várias tags da mesma imagem.
* O conceito de repositório é um pouco diferente de registradores.
  * Registrador: Um serviço que providencia armazenamento ou uma coleção de repositórios.
  * Repositório: Coleção de imagens relacionadas com o mesmo nome mas diferentes versões.
* Em um repositório privado, antes de fazer o push precisa estar logado com o `docker login`.
* A nomenclatura de imagens em um registrador é `registryDomain/imageName:tag`.
  * Por baixo dos panos é feito dessa maneira também no pull, sendo o comando que usamos normalmente um shorthand.
    * Por isso que quando é privado precisa colocar, para dizer de onde vem ja que não é o default (do Docker Hub).
* Portanto para que o nome da imagem contenha o registro completo, é necessário usar o comando `docker tag {NOME APP}:{TAG} {registryDomain/imageName:tag}`
  * Assim o nome fica "completo".
  * Fazer isso toda vez que for uma nova versão (dai so mudar a tag da versão).
* Depois de fazer a tag, fazer um `docker push` com o caminho completo.
* No docker compose, colocar a imagem que está no repositório privado (caminho completo). 
  * O ambiente que executar o compose precisa estar logado.