# Ports

* A aplicação roda em uma rede docker isolada.
  * Portanto, precisa expor a porta do container para que o host possa se comunicar.
* Para fazer isso, usar o `port binding`.
* No `docker ps` da pra ver a porta que o container está rodando.
* Rodar usando o comando `docker run -p {HOST_PORT}:{CONTAINER_PORT} {IMAGE}`.
  * É padrão utilizar a mesma porta do container para o host.
* 