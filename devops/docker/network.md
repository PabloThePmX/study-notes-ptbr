# Docker Network

* O docker tem uma rede isolada.
* Dois containers podem se comunicar dentro dessa rede.
  * Porém é necessário definir que vai ser na mesma rede ao rodar o container.
* Podem se conectar entre elas somente com o nome do container.
  * Porém conexões de fora precisam usar as portas.
* Para ver as redes docker, usar o comando `docker network ls`.
* Para criar uma rede, usar o comando `docker network create {nome da rede}`.
* Para especificar a rede, ao rodar o container usar o parâmetro `--net`.