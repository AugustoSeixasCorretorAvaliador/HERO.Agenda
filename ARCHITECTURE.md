# Arquitetura — HERO.AgendaFácil

## Visão geral

O produto é composto por dois executáveis principais:

```text
WhatsApp Web
  ↓
Chrome Extension
  ↓ HTTPS
Backend API
  ├─ OpenAI
  ├─ Supabase
  └─ Google Calendar
```

## Estrutura alvo

```text
HERO.Agenda/
├── extension/
│   ├── modules/
│   ├── services/
│   ├── ui/
│   └── tests/
├── backend/
│   ├── src/
│   │   ├── routes/
│   │   ├── controllers/
│   │   ├── services/
│   │   ├── repositories/
│   │   ├── prompts/
│   │   ├── middleware/
│   │   └── schemas/
│   └── tests/
├── supabase/
│   ├── migrations/
│   ├── policies/
│   └── seeds/
└── docs/
```

## Extensão Chrome

A extensão terá uma única toolbar e um único observador do DOM.

Botões visíveis:

1. `Copiloto`
2. `Configurar`
3. `Agenda`

Responsabilidades da extensão:

- ler a conversa visível;
- identificar o campo de composição;
- chamar a API;
- mostrar painéis;
- inserir rascunhos;
- armazenar configuração local mínima;
- nunca guardar credenciais sensíveis.

## Backend

Responsabilidades:

- resolver organização e estabelecimento;
- validar licença/autenticação;
- selecionar prompt;
- interpretar intenção;
- consultar serviços e profissionais;
- calcular disponibilidade;
- controlar máquina de estados;
- integrar Google Calendar;
- persistir dados no Supabase;
- registrar auditoria e idempotência.

## Separação entre IA e regras determinísticas

A IA pode:

- classificar intenção;
- extrair serviço, profissional e preferência temporal;
- gerar linguagem natural;
- detectar necessidade de esclarecimento.

A IA não pode:

- inventar serviço ou preço;
- declarar horário livre;
- criar evento diretamente;
- confirmar agendamento sem backend;
- acessar outro tenant.

## Núcleo compartilhado e módulos

```text
shared-core
├── api-client
├── licensing/auth
├── tenant-context
├── logging
├── WhatsApp DOM adapter
└── text insertion

agenda-module
├── prompt configuration
├── service catalog
├── professionals
├── availability engine
├── booking state machine
└── calendar adapter
```

## Estratégia de evolução

- copiar apenas componentes necessários do HERO.IA;
- registrar origem e alterações;
- remover acoplamentos imobiliários;
- manter comportamento assistido no MVP;
- automatizar somente após testes de concorrência e idempotência.
