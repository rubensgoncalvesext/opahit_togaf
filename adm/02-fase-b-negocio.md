# Fase B — Arquitetura de Negócio

## Objetivo

Modelar value streams, capacidades, organização e serviços de negócio AS-IS/TO-BE; identificar gaps e mudanças operacionais necessárias.

## Método

Workshops de Event Storming, entrevistas, análise de jornadas, capability assessment e value stream mapping com Produto, Operações, Risco, Compliance, Finanças e Tecnologia.

## Simulação AS-IS

### Value chain atual

`Atrair → Originar produto isolado → Avaliar risco no silo → Contratar → Servir no silo → Cobrar/Encerrar`

Problemas: baixa interação fora do ciclo de crédito, cadastro repetido, controles duplicados, visão fragmentada e dependência de integrações locais.

### Capacidades críticas e maturidade simulada

| Capacidade | AS-IS | Alvo | Gap |
|---|---:|---:|---|
| Cliente e consentimento | 2 | 4 | visão unificada e ownership |
| Gestão de produtos | 1–2 | 4 | catálogo e composição |
| Conta e ledger | 1/silos | 5 | capacidade compartilhável e íntegra |
| Pagamentos | 1–2 | 4 | orquestração e Pix |
| Risco/compliance | 2/silos | 4 | controles comuns e case management |
| Operações/conciliação | 2/silos | 4 | automação e exceções |
| Dados/engajamento | 2 | 4 | eventos, analytics e personalização |
| Plataforma digital | 2–3 | 4 | paved roads e governança |

### Subdomínios DDD

- **Core:** experiência, engajamento, composição de produtos, ofertas e parceiros.
- **Supporting:** conta, pagamentos, limites, tarifas, conciliação e cashback.
- **Generic:** IAM, KYC, AML, notificações e infraestrutura.

## Arquitetura de negócio TO-BE

### Value stream: adquirir e ativar conta

| Estágio | Outcome | Capacidade principal | Owner proposto |
|---|---|---|---|
| Descobrir | oferta relevante | Engajamento/Produto | Head de Produto |
| Solicitar | jornada simples | Canais/Cliente | Produto Digital |
| Verificar | cliente elegível e conforme | KYC/AML/Fraude | Risco/Compliance |
| Provisionar | conta operacional | Conta/Ledger | Banking Products |
| Ativar | primeiro Pix concluído | Pagamentos | Payments Lead |
| Engajar | uso recorrente | Dados/Ofertas | Growth/CRM |
| Servir | problema resolvido | Atendimento/Operações | COO |

### Serviços de negócio

- identificar e conhecer cliente;
- configurar e ofertar produto;
- abrir e administrar conta;
- custodiar e movimentar valor;
- executar pagamento;
- monitorar risco e conformidade;
- conciliar e liquidar;
- atender e resolver exceção;
- analisar comportamento e personalizar.

### Modelo operacional proposto

Times stream-aligned para Onboarding, Conta/Pagamentos, Engajamento e Crédito; time de plataforma; enabling teams temporários de DDD, segurança, dados e SRE. Cada domínio possui Product Owner, Domain Owner e responsabilidade operacional.

## Gaps e iniciativas

| Gap | Iniciativa | Prioridade |
|---|---|---|
| cliente duplicado | identidade mestre e consentimento | crítica |
| produto codificado em silos | catálogo/composição | crítica |
| ausência de conta compartilhável | Conta e Ledger | crítica |
| controles locais | serviços de risco/compliance | crítica |
| operação manual | workflow, conciliação e case management | alta |
| pouca telemetria | eventos e product analytics | alta |
| ownership difuso | operating model por domínio | crítica |

## Entregáveis simulados

- value chain e value streams;
- capability map e heatmap;
- catálogo de serviços de negócio;
- organization/actor matrix;
- business footprint diagram;
- mapa de domínios e contextos;
- gap analysis e requisitos derivados.

## Gate de saída

- owners aceitam capacidades e responsabilidades;
- Operações valida exceções e modelo de suporte;
- Risco/Compliance aprova controles conceituais;
- gaps e prioridades possuem patrocinador e KPI.

## Evidências requeridas

Volumes de jornadas, tempos de ciclo, custos operacionais, perdas, reclamações, organograma, RACI atual e inventário de processos.
