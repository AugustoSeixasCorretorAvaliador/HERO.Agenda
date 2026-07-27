# Segurança e Isolamento Multiempresa

## Regra central

Nenhuma organização pode acessar clientes, configurações, serviços, profissionais, calendários, credenciais ou agendamentos de outra organização.

## Identificadores obrigatórios

Toda entidade operacional deve possuir:

```text
organization_id
```

Quando aplicável:

```text
establishment_id
```

## RLS

Aplicar Row Level Security em todas as tabelas expostas ao cliente. Políticas devem derivar o acesso do usuário autenticado e de sua associação à organização.

## Backend com service role

A service role ignora RLS. Portanto, cada operação do backend deve:

1. resolver identidade/licença;
2. resolver organização autorizada;
3. validar associação;
4. aplicar `organization_id` em toda consulta;
5. rejeitar IDs de outro tenant, mesmo que existam.

## Tokens Google

- armazenar refresh tokens cifrados;
- nunca enviar refresh token para a extensão;
- limitar escopos OAuth;
- permitir desconexão e revogação;
- registrar falhas sem expor tokens;
- não incluir credenciais em logs.

## Extensão

A extensão não deve conter:

- OpenAI API key;
- Supabase service role key;
- Google client secret;
- refresh token;
- segredo administrativo.

## Auditoria

Registrar ações críticas:

- conexão de calendário;
- alteração de configuração;
- consulta de disponibilidade;
- criação, remarcação e cancelamento;
- transferência para humano;
- falhas e retries.

## LGPD

Coletar apenas os dados necessários. Definir retenção, exclusão, exportação e finalidade antes da automação em produção.
