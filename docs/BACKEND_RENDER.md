# Backend e Render

## Situação informada

Existe um serviço Render suspenso e um repositório legado descartável preparado para receber o backend do HERO.AgendaFácil.

Referência visual informada:

- serviço Render: `hero.ia-backend`;
- branch conectada: `main`;
- plano exibido: Free;
- estado exibido: suspenso pelo proprietário.

Essas informações devem ser verificadas no painel antes de qualquer deploy.

## Princípio

O serviço existente pode ser reutilizado como destino de hospedagem, mas o código legado não deve determinar a arquitetura do novo produto.

## Checklist antes de substituir o legado

1. Confirmar qual repositório está conectado ao serviço.
2. Registrar Root Directory, Build Command e Start Command.
3. Exportar apenas os nomes das variáveis de ambiente, nunca os valores para o Git.
4. Registrar domínio público e health check atual.
5. Confirmar se há banco ou clientes consumindo o serviço antigo.
6. Criar tag ou branch de backup do legado.
7. Definir plano de rollback.
8. Fazer primeiro deploy de staging.

## Configuração alvo sugerida

```text
Runtime: Node
Root Directory: backend
Build Command: npm ci && npm run build
Start Command: npm run start
Health Check: /health
```

A configuração final deverá seguir o framework realmente implementado.

## Variáveis esperadas

Somente nomes, sem valores:

```text
NODE_ENV
PORT
OPENAI_API_KEY
OPENAI_MODEL
SUPABASE_URL
SUPABASE_ANON_KEY
SUPABASE_SERVICE_ROLE_KEY
GOOGLE_CLIENT_ID
GOOGLE_CLIENT_SECRET
GOOGLE_REDIRECT_URI
TOKEN_ENCRYPTION_KEY
CORS_ALLOWED_ORIGINS
APP_REQUIRE_LICENSE
LOG_LEVEL
```

## Rollback

- manter commit anterior identificável;
- não apagar o serviço antigo no primeiro deploy;
- permitir voltar o deploy para commit conhecido;
- migrations iniciais devem ser aditivas;
- desativar novas funções por feature flag em caso de falha.
