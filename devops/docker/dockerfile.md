# Dockerfile

* Uma definição de como construir a imagem em um container.
* Criar um arquivo chamado `Dockerfile` sem extensão.
* Para fazer o build da imagem, usar o comando `docker build {caminho}`
  * O parâmetro `-t` permite colocar o nome da imagem.
  * Se o caminho for no diretório atual, usar o `.`.

## Ajustando o arquivo
* Primeiramente precisamos da imagem base, que vai ser a imagem do serviço que vai providenciar o comando para executar o código.
  * Tipo a imagem do sdk do .NET que vai providenciar o comando `dotnet`, para java pode ser o `tomcat`, para js o `node`, etc.
* Para definir a imagem base, usar o comando `FROM`.
  * Colocar o nome da imagem e a tag.
* Precisa buscar os arquivos da aplicação e copia-los para a imagem usando o `COPY`.
  * Esse comando é executado no host.
  * Definimos o que queremos copiar para qual local do container quando o mesmo for instanciado.
    * O container vai ter um sistema de arquivos virtualizado.
  * Geralmente se copia o `src` para uma pasta começando com `/{nome pasta}/` sendo a `/` responsável por dizer pro Linux criar a pasta caso a mesma não exista.
* Ao copiar, é necessário ir para a nova pasta (equivalente ao `cd`), e para isso usar o `WORKDIR {caminho virtual que foi copiado}`.
* Para executar um comando Linux, usar o `RUN`.
  * Fazer o `npm install` dessa forma.
* O último comando é o `CMD`, que é usado para iniciar a aplicação.
  * Nele, colocar o comando é o parâmetro, como `CMD ["dotnet run", "projeto.csproj"]`.
* Exemplo de Dockerfile para js:
```Dockerfile
# é sempre bom definir uma versão específica para que não tenha problemas futuros
# essa versão do node usa a imagem do Linux alpine
FROM node:19-alpine 

COPY package.json /app/
COPY src /app/

WORKDIR /app

RUN npm install

CMD ["node", "server.js"]
```
* Adicionalmente, da pra definir variáveis de ambiente com `ENV`. 
  * Mas costuma ser melhor definir no docker compose, pois se for no dockerfile tem que refazer a imagem.