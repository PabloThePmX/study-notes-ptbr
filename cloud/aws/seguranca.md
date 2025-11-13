# Segurança

* Modelo de responsabilidade compartilhada da AWS.
  * A AWS tem a responsabilidade pela segurança DA nuvem.
    * Softwares, serviços, armazenamento, regiões, datacenters, etc.
  * O cliente tem a responsabilidade pela segurança NA nuvem.
    * Dados, firewall, plataforma, aplicações, trafego de rede, etc.
* É recomendado não usar o usuário root da conta, apenas quando necessário.
  * Algumas ações podem ser apenas realizados por ele, como atualizar a senha do usuário raiz, plano, restaurar permissões, etc.
  * Para isso, criar um usuário do IAM para você mesmo, então criar um grupo com permissões de administrações e colocar no novo usuário.
    * Depois excluir as chaves de acesso do usuário raiz.
* Usar o CloudTrail para rastrear as atividade dos usuários da conta.
  * Por padrão ele salva até 90 dias, mas da pra ajustar e salvar no bucket.
* O Amazon Cognito adiciona login e registro de usuários para os aplicativos web e mobile.
  * Oferece suporte de login com Facebook, Google, Amazon, etc.
* O AWS Shield é um serviço de proteção contra DDoS e ataques gerais a aplicativos.
  * Usado para minimizar o tempo de inatividade e latência do aplicativo.
  * Existe a versão grátis (vem habilitado manualmente) e paga.
* Por padrão os buckets S3 são privados.
  * Usar o Amazon S3 Block Public Access para controlar o acesso aos dados do S3 (sobrescreve qualquer política do bucket).
  * Da pra usar o IAM para bloquear o acesso também.
  * Da pra fazer uma varredura com o Trusted Advisor pra ver se tem algum bucket público na conta.
* A AWS segue princípios da ISO 270001, 27017, 27018 e ISO/IEC 9001.
* o AWS Config permite ver serviços que podem estar com alguma inconformidade em questão de segurança.
  * Cada região vai ter um AWS Config, ou seja, precisa habilitar em cada região.
* O AWS Artifact é um recurso para verificar informações relacionadas à conformidade.
  * Ver certificações da ISO da AWS.
  * Da pra gerenciar as contas que vão processar essas certificações de conformidade.
    * Como aceitar algum contrato em nome de uma organização (AWS Organization ).

## IAM
* O IAM é usado para gerenciar o acesso aos recursos da AWS.
  * Ou seja, quem pode controlar tais instancias.
  * Define os direitos de quem, quais e como os recursos podem ser acessados.
* É um serviço gratuito.
* Componentes essenciais:
  * Usuário do IAM: Uma pessoa ou aplicativo que pode se autenticar com uma conta AWS.
  * Grupo do IAM (admins, dev, testers, etc): Uma coleção de usuários do IAM que recebem autorização idêntica (política).
    * Grupos não podem ser aninhados.
    * Um usuário pode pertencer a vários grupos.
    * Não há grupo padrão.
  * Política de Permissão do IAM: O documento que define quais recursos podem ser acessados e o nível de acesso a cada um deles (atribuição de permissões).
  * Função do IAM: Mecanismo útil para conceder um conjunto de permissões temporárias para fazer solicitações de serviços da AWS.
    * Parecido com o sistema do `sudo` pois te da permissões elevadas temporariamente, até que seja revertida a ação.
    * Políticas são atribuídas as funções.
* Tipos de Acesso que cada usuário poderá ter permissão para usar (da pra definir sobre cada um deles)
  * Acesso programático é autenticado usando o id da chave e a chave secreta (fornece acesso a CLI e ao SDK).
  * Acesso ao Console de Gerenciamento é autenticado usando o id (ou alias), o nome do usuário do IAM e a senha.
    * Pode ter multi factor authentication (MFA).
* A prática recomendada é de seguir o princípio de privilégio mínimo.
* A política do IAM é em JSON.
* Existe dois tipos de políticas:
  * Baseadas em identidade (permissões).
    * Uma politica anexada a qualquer entidade do IAM, podendo dizer o que pode e o que não pode ser feito.
    * Uma única política pode ser anexada a várias entidades e uma única entidade pode ter várias políticas anexadas a ela.
  * Baseadas em recursos.
* Todas os acessos por padrão vem como negado.
  * E se há duas políticas conflitantes, uma dizendo que tal entidade tem acesso a algo, e outra não, a negação "vence".
  * Se o IAM não encontrar algo dizendo explicitamente que está autorizado, ela vai negar o acesso (negação implícita).
* Serviços criados com um role IAM especifico terão acesso à aquelas políticas definidas.
* Os usuários do IAM podem logar com links específicos, onde depois precisam informar o usuário e senha.
  * O link pode ser encontrado no dashboard do IAM.

## Organizations
* Permite consolidar várias contas da AWS permitindo que elas sejam gerenciadas de maneira centralizada.
  * Da pra anexar políticas aos grupos de contas.
* Agrupadas em unidades organizacionais (OUs).
  * Há limites para a quantidade.
* Permite que cada departamento tenha uma conta diferente com acesso a diferentes recursos.
* Suporta IAM.
* As políticas de controle de serviço (SCPs) oferecem controle centralizado sobre contas.
  * São semelhantes as políticas de permissão do IAM.
    * No entanto ela nunca concede permissões, ao invés disso, elas especificam as permissões máximas para uma organização.
* Simplifica a automatização da criação e gerenciamento de contas usando APIs.

## Criptografia
* A AWS Key Management Service permite criar e gerenciar chaves de criptografia.
  * Permite controlar o uso da criptografia nos serviços da AWS e nos aplicativos.
  * Integra-se ao CloudTrail para registrar todo o uso de chaves.
  * Da pra importar chaves já existentes de outros locais.
* A AWS oferece suporte a criptografia de dados em repouso (que estão armazenados fisicamente).
* Para criptografar dados em trânsito (por uma rede) se usa protocolos como TLS, HTTPS e afins.
  * O AWS Certificate Manager auxilia para gerenciar, implantar e renovar certificados TLS (ou SSL).
  * Podem existir dados em transito entre dois serviços.