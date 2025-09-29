# Comandos

* `docker images` - Verifica todas as imagens dockers presentes na máquina.
* `docker ps` - Verifica os containers que estão rodando.
  * `docker ps -a` - Verifica todos os containers, inclusive aqueles parados.
* `docker pull {NAME}:{TAG}` - Pega a imagem do repositório (o Docker Hub é o padrão para buscar).
  * Sem a `tag` ele pega a última versão (`latest` tag).
* `docker run {IMAGE}:{TAG}` - Para criar um container com a imagem.
  * Usar o parâmetro `-d` (detach) permite rodar o container em background.
  * Se ele não encontrar a imagem localmente, ele vai buscar no repositório automaticamente sem precisar fazer pull.
  * `docker run -p {HOST_PORT}:{CONTAINER_PORT} {IMAGE}` para fazer o bind da porta para que o host possa se comunicar.
    * O `-p` significa publish.
  * Usar a flag `--name` para colocar um nome no container.
  * Usar a flag `-e {NOME VARIAVEL AMBIENTE}={VALOR}` para adicionar um valor a uma variável de ambiente.
    * Usa-se muito quando é criado um container de banco, pois é assim que o usuário e senha são setados.
  * Usar a flag `--net {REDE}` para especificar qual rede o container vai usar.
  * Usar a flag `-v` para definir um volume `-v {CAMINHO HOST}:{CAMINHO CONTAINER}`.
    * O caminho no host é opcional.
      * Da pra dar um nome a esse caminho com `-v {NOME}:CAMINHO CONTAINER`, dessa forma permite-se chamar o caminho apenas pelo nome.
* `docker logs {container}` - Para ver os logs daquele container.
  * Usar `| tail` para pegar apenas os últimos logs.
  * Usar `-f` para acompanhar.
* `docker stop {container}` - Para o container.
  * Da pra parar mais de um container por vez.
* `docker start {container}` - Para iniciar um container parado.
* `docker build {caminho}` - Para fazer o build de uma imagem (Dockerfile).
  * Ao usar o `-t` (antes do caminho) podemos dar um nome a imagem.
    * Da pra colocar uma tag também usando o `:`.
  * Usar `.` para o caminho caso o Dockerfile esteja no diretório atual.
* `docker exec -it {container} /bin/bash` - Para acessar o terminal do container e verificar as pastas ou executar comandos.
  * Como é executado um Linux mais leve, pode ser que a maioria dos comandos não estejam baixados.
  * Se não funcionar, tentar o `/bin/sh`.
* `docker network ls` - Para ver as redes docker.
* `docker network create {nome da rede}` - Cria uma rede.
* `docker compose -f {ARQUIVO YAML} up` - Executa o docker compose.
  * Com o parâmetro `down` os containers são parados.
* `docker rmi {imagem}` - Remove uma imagem.
* `docker rm {container}` - Remove um container.
  * Precisa remover o container parado para que seja possível remover a imagem.
* `docker login` - Faz o login no repositório privado.
* `docker tag {NOME APP}:{TAG} {registryDomain/imageName:tag}` - Faz o tag (renomeia/copia com esse novo nome) da imagem, colocando o registro completo no nome.
  * Usado para repositórios privados.
* `docker push {caminho}` - Faz o push da imagem para o repositório.
  * Caso for um repositório privado, precisa ir o caminho completo.