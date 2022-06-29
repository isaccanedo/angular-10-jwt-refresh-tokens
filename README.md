# angular-10-jwt-refresh-tokens

### Tutorial construído com Angular 10.0.5

O aplicativo angular de exemplo tem apenas duas rotas - uma página de login (/login) e uma página inicial (/). Para fazer login, o aplicativo envia uma solicitação POST à API para autenticar o nome de usuário e a senha, no login bem-sucedido, o aplicativo recebe um token JWT para fazer solicitações autenticadas para proteger as rotas da API e um token de atualização (em um cookie) para obter um novo JWT token da API quando o antigo expirar (também conhecido como atualizar o token).

Na inicialização, o aplicativo tenta se autenticar automaticamente enviando o token de atualização para a API para obter um novo token JWT, que permite que os usuários permaneçam conectados entre as atualizações de página e as sessões do navegador até o logout. Ele funciona enviando o cookie do token de atualização armazenado no navegador para a api, se o cookie não existir ou não for válido ele falhará silenciosamente e a página de login será exibida.

Depois que o usuário faz login no aplicativo inicia uma contagem regressiva para atualizar automaticamente o token um minuto antes de expirar, isso também é chamado de "atualização silenciosa", pois ocorre em segundo plano. A contagem regressiva começa novamente após cada atualização silenciosa para manter o usuário conectado.

O aplicativo angular é executado com um backend falso por padrão para permitir que ele seja executado completamente no navegador sem uma API de backend real (sem backend), para alternar para uma API real, basta remover ou comentar a linha abaixo do comentário / / provedor usado para criar backend falso localizado no módulo do aplicativo (/src/app/app.module.ts). Você pode construir sua própria API ou conectá-la com a API ASP.NET Core ou Node.js + api MongoDB disponível (instruções abaixo).

## Executando o JWT angular com exemplo de tokens de atualização localmente

```
- Instale o NodeJS e o NPM de https://nodejs.org;
- Baixe ou clone o projeto Angular de https://github.com/isaccanedo/angular-10-jwt-refresh-tokens;
- Instale todos os pacotes npm necessários executando npm install ou npm i a partir da linha de comando na pasta raiz do projeto (onde o package.json está localizado);
- Inicie o aplicativo executando npm start na linha de comando na pasta raiz do projeto, isso compilará o aplicativo Angular e o iniciará automaticamente no navegador na URL http://localhost:4200.
```

**NOTA:** Você também pode iniciar o aplicativo com o comando Angular CLI ```ng serve --open```. Para fazer isso, primeiro instale a CLI Angular globalmente em seu sistema com o comando ```npm install -g @angular/cli```.

Para obter mais informações sobre como configurar um ambiente de desenvolvimento Angular, consulte Angular - Setup Development Environment.

## Executando o aplicativo Angular com uma API Node.js + MongoDB

- Instale o MongoDB Community Server em https://www.mongodb.com/download-center/community;
- Execute o MongoDB, as instruções estão disponíveis na página de instalação para cada SO em https://docs.mongodb.com/manual/administration/install-community/;
- Baixe ou clone o código-fonte do projeto em https://github.com/cornflourblue/node-mongo-jwt-refresh-tokens-api;
- Instale todos os pacotes npm necessários executando npm install ou npm i a partir da linha de comando na pasta raiz do projeto (onde o package.json está localizado);
- Inicie a API executando npm start (ou npm run start:dev to start with nodemon) na linha de comando na pasta raiz do projeto, você deverá ver a mensagem Server listen on port 4000, e você pode visualizar a documentação da API Swagger em http://localhost:4000/api-docs;
- De volta ao aplicativo Angular, remova ou comente a linha abaixo do provedor de comentários // usado para criar um backend falso localizado no arquivo /src/app/app.module.ts, inicie o aplicativo Angular e agora ele deve estar conectado com a API Node.js + MongoDB.



