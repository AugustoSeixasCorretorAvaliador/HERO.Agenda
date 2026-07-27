# Modelo de Dados Proposto

> Este documento é proposta. Antes de criar migrations, inspecionar o schema Supabase real.

## Entidades principais

```text
organizations
establishments
organization_members
customers
professionals
services
professional_services
business_hours
availability_exceptions
calendar_connections
bookings
booking_events
service_sessions
conversation_messages
audit_logs
idempotency_keys
```

## Regras

- UUID como chave primária.
- `organization_id` obrigatório nas entidades operacionais.
- timestamps em UTC.
- timezone configurado por estabelecimento.
- soft delete quando necessário para auditoria.
- constraints para impedir duplicidade lógica.

## Booking

Campos conceituais:

```text
id
organization_id
establishment_id
customer_id
service_id
professional_id
starts_at
ends_at
timezone
status
source
confirmation_at
google_calendar_id
google_event_id
idempotency_key
created_at
updated_at
```

## Estados de booking

```text
PENDING_CONFIRMATION
CONFIRMING
CONFIRMED
RESCHEDULING
CANCELLED
CALENDAR_SYNC_PENDING
FAILED
```

## Concorrência

A criação precisa impedir dois agendamentos confirmados para o mesmo profissional e intervalo. A estratégia final pode usar constraint por faixa, lock transacional, função SQL ou reserva temporária, conforme suporte confirmado.
