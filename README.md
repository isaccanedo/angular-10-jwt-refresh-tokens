# angular-10-jwt-refresh-tokens

### Tutorial construído com Angular 10.0.5

O aplicativo angular de exemplo tem apenas duas rotas - uma página de login (/login) e uma página inicial (/). Para fazer login, o aplicativo envia uma solicitação POST à API para autenticar o nome de usuário e a senha, no login bem-sucedido, o aplicativo recebe um token JWT para fazer solicitações autenticadas para proteger as rotas da API e um token de atualização (em um cookie) para obter um novo JWT token da API quando o antigo expirar (também conhecido como atualizar o token).

Na inicialização, o aplicativo tenta se autenticar automaticamente enviando o token de atualização para a API para obter um novo token JWT, que permite que os usuários permaneçam conectados entre as atualizações de página e as sessões do navegador até o logout. Ele funciona enviando o cookie do token de atualização armazenado no navegador para a api, se o cookie não existir ou não for válido ele falhará silenciosamente e a página de login será exibida.

Depois que o usuário faz login no aplicativo inicia uma contagem regressiva para atualizar automaticamente o token um minuto antes de expirar, isso também é chamado de "atualização silenciosa", pois ocorre em segundo plano. A contagem regressiva começa novamente após cada atualização silenciosa para manter o usuário conectado.

O aplicativo angular é executado com um backend falso por padrão para permitir que ele seja executado completamente no navegador sem uma API de backend real (sem backend), para alternar para uma API real, basta remover ou comentar a linha abaixo do comentário / / provedor usado para criar backend falso localizado no módulo do aplicativo (/src/app/app.module.ts). Você pode construir sua própria API ou conectá-la com a API ASP.NET Core ou Node.js + api MongoDB disponível (instruções abaixo).



