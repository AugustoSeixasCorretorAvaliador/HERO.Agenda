# Plano de Implementação Incremental

## Fase 0 — Inventário

- confirmar repositório fonte do Copiloto HERO.IA;
- mapear arquivos que serão reutilizados;
- registrar backend legado e configuração Render;
- inventariar variáveis de ambiente sem copiar valores secretos;
- inspecionar schema Supabase antes de migrations.

## Fase 1 — Scaffold

- criar `extension/` e `backend/`;
- configurar lint, testes, typecheck e build;
- criar health check;
- preparar ambientes local, staging e production;
- nenhuma integração de produção nesta fase.

## Fase 2 — Extensão com três botões

- reutilizar observador, leitura do WhatsApp e inserção de texto;
- criar toolbar com `Copiloto`, `Configurar` e `Agenda`;
- manter modo assistido e sem envio automático;
- configurar URL de API por ambiente.

## Fase 3 — Copiloto segmentado

- criar prompt base protegido;
- criar registro de segmentos;
- salvar configuração do estabelecimento;
- gerar análise e rascunho;
- não consultar agenda ainda.

## Fase 4 — Catálogo e disponibilidade

- cadastrar serviços, duração, preços e profissionais;
- cadastrar horários e exceções;
- implementar motor determinístico;
- sugerir três slots.

## Fase 5 — Google Calendar somente leitura

- implementar OAuth;
- selecionar calendário;
- consultar eventos ocupados;
- validar timezone e renovação de token;
- não criar evento.

## Fase 6 — Agendamento manual assistido

- confirmação explícita;
- revalidação de disponibilidade;
- botão humano para criar;
- persistência no Supabase;
- criação idempotente no Calendar.

## Fase 7 — Automação controlada

- feature flag por organização;
- criação automática após confirmação válida;
- remarcação e cancelamento;
- retries, reconciliação e auditoria.

## Critério de passagem entre fases

Cada fase exige lint, testes, typecheck, build, validação manual e relatório de regressão. Não avançar com pendências críticas de isolamento, segurança ou concorrência.
