# AGENTS.md — Regras para Codex e agentes de engenharia

## Missão

Evoluir o HERO.AgendaFácil com mudanças pequenas, verificáveis e compatíveis com a arquitetura definida neste repositório.

## Antes de alterar qualquer arquivo

1. Leia `README.md`, `ARCHITECTURE.md` e os documentos em `docs/`.
2. Localize implementação equivalente no HERO.IA antes de recriar funcionalidade.
3. Separe fatos encontrados, hipóteses e recomendações.
4. Explique o que será reutilizado e os riscos.
5. Prefira a menor alteração possível.
6. Não altere produção, Render, Supabase ou Google Cloud sem autorização explícita.

## Regras obrigatórias

- Não reconstruir autenticação, licenciamento, integração com WhatsApp ou cobrança sem justificativa.
- Não copiar acoplamentos imobiliários para o novo produto.
- Não permitir que a LLM invente disponibilidade.
- Não criar agendamento sem confirmação explícita e revalidação do horário.
- Não expor segredos, tokens, cookies, service role keys ou credenciais OAuth.
- Não executar migrations destrutivas.
- Toda entidade operacional multiempresa deve possuir `organization_id` e, quando aplicável, `establishment_id`.
- Aplicar RLS e também validação de tenant no backend.
- Nenhum módulo da extensão envia mensagens automaticamente no MVP.

## Fluxo de trabalho

1. Diagnóstico.
2. Plano curto.
3. Implementação em branch.
4. Lint.
5. Testes.
6. Typecheck.
7. Build.
8. Revisão de regressão.
9. Relatório de arquivos alterados e pendências.

## Convenções

- Código e nomes técnicos em inglês.
- Documentação e interface em português do Brasil.
- Commits pequenos com padrão Conventional Commits.
- Preferir TypeScript para novo backend.
- Interfaces explícitas e funções determinísticas.
- Feature flags para capacidades ainda não estáveis.

## Proibições

- Não declarar algo funcionando sem executar validação.
- Não inserir URLs ou IDs de produção fixos no código quando puderem ser variáveis de ambiente.
- Não usar a OpenAI para decidir disponibilidade, gravar eventos ou determinar autorização.
- Não apagar o backend legado antes de registrar rollback.
