# App Service
Colocar o mesmo grupo de recursos que o banco de dados que foi criado.
* É recomendo rodar em Linux para ter uma maior performance.
* É preferível colocar a região com a mesma que foi colocada para o banco.

## Subindo o código para o serviço
Primeiramente, pegar a string de conexão da DB no Azure e colocar no `appsettings.json`. Ao copiar, precisa colocar a senha na string de conexão.
> Vai ser colocado neste json, pois é nele que é colocado a conexão dos bancos de produção. Obs.: melhor deixar o nome da string com o mesmo nome que estava no desenvolvimento.

### Para aplicar a migration
Colocar a string de conexão do banco azure no appsettings do desenvolvimento, para aplicar o comando de atualizar o banco com as migrations.

* Depois de aplicar a migração, publicar a aplicação pela própria IDE.
> Caso for o VSCode, baixar a extensão, clicar com o botão direito no serviço, e selecionar a opção `Deploy to Web App`.


