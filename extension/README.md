# Extensão Chrome

Este diretório receberá a extensão Manifest V3 do HERO.AgendaFácil.

## Interface

```text
[ Copiloto ] [ Configurar ] [ Agenda ]
```

## Estrutura planejada

```text
extension/
├── manifest.json
├── background/
├── content/
├── modules/
│   ├── copilot/
│   ├── configuration/
│   └── scheduling/
├── services/
│   ├── api/
│   ├── storage/
│   ├── whatsapp-dom/
│   └── text-insertion/
├── ui/
├── assets/
└── tests/
```

## Componentes a reutilizar do HERO.IA

- um único MutationObserver;
- captura de mensagens;
- detecção do composer;
- inserção de rascunho sem envio;
- painel de análise;
- validação/licenciamento, após revisão;
- cliente HTTP, após retirar URL fixa.

## Regras

- nenhum segredo na extensão;
- nenhum envio automático no MVP;
- módulos não criam observers independentes;
- toolbar idempotente;
- seletores do WhatsApp isolados em adapter próprio;
- falhas de DOM devem ser observáveis e não silenciosas.

Nenhum código foi copiado ainda. A reutilização deverá ocorrer após comparação explícita com a implementação atual do HERO.IA.
