# HERO.AgendaFácil

HERO.AgendaFácil é o produto do ecossistema HERO.IA voltado a atendimento comercial e agendamentos pelo WhatsApp.

Este repositório é a árvore principal do produto e deverá conter:

- extensão Google Chrome para WhatsApp Web;
- backend Node.js;
- integração com Supabase;
- integração com Google Calendar;
- documentação para evolução controlada pelo Codex no VS Code.

## Estado atual

Estrutura inicial e documentação arquitetural. Nenhuma automação de agendamento deve ser considerada pronta até haver implementação, testes e validação.

## Interface planejada da extensão

1. **Copiloto** — analisa a conversa e gera resposta de atendimento usando configuração por segmento.
2. **Configurar** — cadastra segmento, serviços, regras, tom de voz e instruções do estabelecimento.
3. **Agenda** — consulta disponibilidade, acompanha agendamentos e inicia fluxos de criação, remarcação ou cancelamento.

## Regra fundamental

A LLM interpreta intenção e produz linguagem natural, mas não inventa disponibilidade e não confirma reservas. Disponibilidade e criação do agendamento pertencem ao backend determinístico.

## Leitura obrigatória antes de desenvolver

- `AGENTS.md`
- `ARCHITECTURE.md`
- `docs/PRODUCT_SCOPE.md`
- `docs/IMPLEMENTATION_PLAN.md`
- `docs/BACKEND_RENDER.md`
- `docs/SECURITY_AND_TENANCY.md`

## Situação do backend legado

Existe um serviço Render e um repositório legado descartável que poderão ser reaproveitados como destino de hospedagem. Eles não são fonte arquitetural de verdade. Antes de substituir qualquer conteúdo, registrar configuração, variáveis de ambiente, branch conectada e plano de rollback.
