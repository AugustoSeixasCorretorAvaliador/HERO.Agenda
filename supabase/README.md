# Supabase

Este diretório armazenará migrations, políticas RLS e seeds controlados.

## Estrutura planejada

```text
supabase/
├── migrations/
├── policies/
├── seeds/
└── tests/
```

## Regras

- inspecionar o schema remoto antes da primeira migration;
- migrations iniciais somente aditivas;
- nunca incluir credenciais;
- toda tabela operacional com `organization_id`;
- RLS habilitada antes de exposição ao cliente;
- políticas testadas com usuários de organizações diferentes;
- seeds apenas com dados fictícios;
- registrar rollback e impacto de cada migration.

## Processo

1. gerar migration local;
2. revisar SQL;
3. testar em projeto de desenvolvimento;
4. validar RLS;
5. registrar resultado;
6. somente depois solicitar autorização para produção.
