# Backend HERO.AgendaFácil

Este diretório receberá a API do produto.

## Estrutura planejada

```text
backend/
├── package.json
├── tsconfig.json
├── src/
│   ├── server.ts
│   ├── app.ts
│   ├── config/
│   ├── routes/
│   ├── controllers/
│   ├── services/
│   ├── repositories/
│   ├── domain/
│   ├── prompts/
│   ├── middleware/
│   ├── schemas/
│   └── integrations/
│       ├── openai/
│       ├── supabase/
│       └── google-calendar/
└── tests/
```

## Endpoints conceituais

```text
GET  /health
POST /v1/copilot/analyze
GET  /v1/configuration
PUT  /v1/configuration
GET  /v1/services
GET  /v1/professionals
POST /v1/availability/search
POST /v1/bookings
POST /v1/bookings/:id/reschedule
POST /v1/bookings/:id/cancel
GET  /v1/calendar/connection
POST /v1/calendar/oauth/start
GET  /v1/calendar/oauth/callback
```

Contratos finais devem ser documentados em OpenAPI antes da automação.

## Regras

- validar payloads com schema;
- resolver tenant em middleware;
- regras de disponibilidade em serviços determinísticos;
- prompt não acessa banco diretamente;
- integrações externas atrás de adapters;
- idempotência nas mutações;
- logs estruturados sem PII desnecessária;
- health check não deve revelar segredos.

## Backend legado

Não copiar `server.js` monolítico sem diagnóstico. Reutilizar apenas funções comprovadas, como normalização, licenciamento ou tratamento de texto, extraindo-as para módulos testáveis.
