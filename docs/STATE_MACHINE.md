# Máquina de Estados do Atendimento

## Estados

```text
NEW
IDENTIFYING_NEED
SERVICE_IDENTIFIED
COLLECTING_PREFERENCES
CHECKING_AVAILABILITY
SLOTS_OFFERED
WAITING_SELECTION
WAITING_CONFIRMATION
REVALIDATING_AVAILABILITY
BOOKED
RESCHEDULING
CANCELLING
CANCELLED
HUMAN_HANDOFF
ERROR
```

## Regras de transição

- estados são persistidos no backend;
- a LLM sugere intenção, mas não altera estado diretamente;
- toda transição deve ser validada por função de domínio;
- slots oferecidos devem ter validade temporal;
- seleção não equivale a confirmação;
- confirmação deve ocorrer depois da oferta do slot;
- antes de `BOOKED`, reconsultar disponibilidade;
- falhas parciais devem ir para estado recuperável.

## Confirmações válidas

Exemplos:

```text
Pode confirmar
Sim, esse horário
Fechado
Pode agendar
Confirmo
```

Mensagens ambíguas devem permanecer em `WAITING_CONFIRMATION` e gerar pergunta objetiva.

## Transferência humana

Usar `HUMAN_HANDOFF` quando houver:

- política não cadastrada;
- pedido clínico sensível;
- conflito persistente;
- cliente irritado;
- incerteza de identidade;
- falha de integração;
- solicitação fora da capacidade configurada.
