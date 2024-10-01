# Arquivo config
* Para criar um arquivo de config, executar o comando `npx tsc --init`.
* No `tsconfig.json`:
  * Alterar a `rootDir` para `./src`, para indicar qual a pasta raiz que vão estar os componentes (caso seja omitido o caminho na hora de transpilar).
    * Dessa forma. ao executar o comando `npx tsc`, ele vai dar build em todos os arquivos dentro da pasta.
  * Alterar o `outDir` para `./build`.
  * Temos também a opção `removeComments`, que remove os comentários do arquivo compilado quando é feito o build.
* No `package.json`:
  * Criar um novo scrip chamado `start`, com o valor `npx tsc && node build/index.js`
    * Assim, ao rodar o `npm run start`, ele vai transpilar e executar o código.
* Jeito mais fácil de rodar o código TS (`TS Node Dev`):
  * Primeiro instalar o pacote `npm install ts-node-dev -D`.
    * É um servidor local que entende TS, e por causa disso não precisa gerar build (ele gera em memória).
  * Criar um script novo no `package.json` chamado de `"start:dev"` contendo o valor `ts-node-dev --respawn --transpile-only src/index.ts`.
  * Para executar o novo script `npm run start:dev`
  * Por se tratar de um servidor, ele vai atualizar conforme forem ocorrendo as alterações.