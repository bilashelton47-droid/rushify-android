# Rushify Android

Aplicação Android nativa mínima para receber notificações de vendas através do Firebase Cloud Messaging (FCM).

## Configuração necessária no GitHub (pelo telemóvel)

1. Envie todos os ficheiros deste projeto para o repositório `rushify-android`, mantendo os caminhos das pastas.
2. No GitHub, abra **Settings → Secrets and variables → Actions → New repository secret**.
3. Nome do secret: `GOOGLE_SERVICES_JSON_BASE64`.
4. Valor: conteúdo do `google-services.json` convertido para Base64. Não cole o JSON em issues, README ou ficheiros públicos.
5. Abra **Actions → Build Rushify APK → Run workflow**.
6. Quando a execução terminar com sucesso, abra o run e descarregue o artefacto `rushify-debug-apk`.

## Importante

- O token FCM apresentado pela aplicação é um identificador de destino, não uma senha. Envie-o apenas para o backend autorizado.
- O token deve ser registado no backend para que o webhook possa enviar notificações ao dispositivo.
- Nunca coloque credenciais privadas de conta de serviço Firebase no APK ou no repositório.
- A aplicação cria o canal de notificações com som padrão. Se o utilizador silenciar o canal nas definições Android, o som não tocará.
- Para receber alertas em background, o servidor deve enviar mensagens FCM corretamente formatadas. Notificações `notification` são apresentadas pelo Android quando a aplicação está em background; mensagens `data` são tratadas pelo serviço quando a aplicação está ativa.
