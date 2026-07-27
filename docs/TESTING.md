# Estratégia de Testes

## Obrigatórios antes de merge

```text
lint
test
typecheck
build
```

## Unitários

- parsing de datas e períodos;
- duração e buffers;
- horários de funcionamento;
- seleção dos três slots mais próximos;
- confirmação explícita;
- transições de estado;
- idempotência;
- isolamento de tenant.

## Integração

- Supabase;
- OpenAI com respostas simuladas;
- Google Calendar sandbox;
- extensão para backend;
- criação e cancelamento de evento;
- token expirado e retry.

## Concorrência

Testar dois clientes tentando confirmar o mesmo profissional e horário. Apenas uma criação pode ser concluída.

## Regressão da extensão

- toolbar única;
- três botões;
- captura correta de autores;
- leitura de mensagens;
- inserção sem envio;
- ausência de duplicação após mudanças no DOM;
- funcionamento após troca de conversa.

## E2E

Fluxo mínimo:

```text
cliente solicita serviço
→ copiloto identifica
→ backend consulta disponibilidade
→ três slots são oferecidos
→ cliente escolhe
→ confirmação explícita
→ revalidação
→ criação manual/automática conforme flag
→ registro no Supabase e Calendar
```

## Evidências

O relatório de entrega deve informar comandos executados, resultado, arquivos alterados e limitações não testadas.
