# App Service
Colocar o mesmo grupo de recursos que o banco de dados que foi criado.
* É recomendo rodar em Linux para ter uma maior performance.
* É preferível colocar a região com a mesma que foi colocada para o banco.

### Para aplicar a migration
Colocar a string de conexão do banco azure no appsettings do desenvolvimento, para aplicar o comando de atualizar o banco com as migrations.
* Dica: tirar a string de conexão do appsettings do desenvolvimento.

* Depois de aplicar a migração, publicar a aplicação pela própria IDE.

## Subindo o código para o serviço
Primeiramente, pegar a string de conexão da DB no Azure e colocar no `appsettings.json`. Ao copiar, precisa colocar a senha na string de conexão.
> Vai ser colocado neste json, pois é nele que é colocado a conexão dos bancos de produção. Obs.: melhor deixar o nome da string com o mesmo nome que estava no desenvolvimento.
* Dicas: Parece que ao conectar, precisa estar com o banco padrão no perfil, depois de conectar no banco do azure pode apagar o outro (porém não tenho 100% de certeza quanto a isso).
* Se ao fazer o deploy, estiver faltando itens do wwwroot, verificar se não a algo no csproj dizendo para remover os itens.

### Para publicar
> Caso for o VSCode, baixar a extensão, clicar com o botão direito no serviço, e selecionar a opção `Deploy to Web App`.
> Caso for o VS, botar para publicar, porém, deletar os bancos presentes nas dependências do serviço, visto que já colocamos manualmente pelas strings de conexão.
  * OBS.: Caso estiver dando erro ao fazer o publish do deploy pelo VS, habilitar a opção `SCM Basic Auth Publishing Credentials` no serviço do azure.
