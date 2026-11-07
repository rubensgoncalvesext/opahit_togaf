# Alternativas de Architecture Building Blocks (ABB)

## Objetivo

Comparar alternativas **lógicas e independentes de fornecedor** para atender às capacidades da arquitetura alvo. ABB define o que é necessário e seus contratos; não define marca ou produto.

## Critérios de decisão

- alinhamento a capacidades e DDD;
- autonomia e time-to-market;
- integridade e risco operacional;
- interoperabilidade e reuso;
- complexidade de operação;
- portabilidade e evolução;
- custo total e capacidade interna.

---

## ABB 1 — Plataforma de produto

### Alternativa 1A: produto codificado em cada domínio

Cada produto mantém regras, tarifas e elegibilidade próprias.

- **Pró:** autonomia local e início simples.
- **Contra:** repete o AS-IS, reduz reuso e dificulta visão de portfólio.
- **Aplicação:** somente regras estritamente internas ao domínio.

### Alternativa 1B: catálogo central com composição federada — recomendada

Catálogo governa definições, versões e componentes; cada domínio mantém invariantes próprias.

- **Pró:** reuso sem motor central dominar todos os contextos.
- **Contra:** exige modelo de produto e governança claros.
- **Contratos:** Product API, `ProdutoPublicado`, política de versionamento.

### Alternativa 1C: motor central de produtos

Todas as regras e jornadas dependem de um motor único.

- **Pró:** configuração concentrada.
- **Contra:** risco de gargalo, acoplamento e modelo genérico excessivo.

**Decisão proposta:** 1B.

---

## ABB 2 — Conta e movimentação financeira

### Alternativa 2A: Conta e Ledger no mesmo bounded context

- **Pró:** menor latência e consistência local no MVP.
- **Contra:** escala e evolução acopladas.
- **Adequação:** início controlado, desde que módulos e contratos sejam explícitos.

### Alternativa 2B: Conta e Ledger separados — alvo recomendado

Conta administra ciclo de vida; Ledger administra postings, reservas e saldos.

- **Pró:** ownership e invariantes claros, maior reuso.
- **Contra:** interação distribuída e necessidade de idempotência/sagas.
- **Contratos:** Account API, Posting API e eventos de lançamento.

### Alternativa 2C: ledger por produto

- **Pró:** autonomia local.
- **Contra:** reconciliação fragmentada e duplicação crítica.
- **Decisão:** rejeitada como direção alvo.

**Decisão proposta:** 2B, admitindo implantação modular 2A na transição sem perder as fronteiras lógicas.

---

## ABB 3 — Integração

### Alternativa 3A: APIs síncronas predominantes

- **Pró:** fluxo direto e resposta imediata.
- **Contra:** acoplamento temporal e falhas em cascata.

### Alternativa 3B: eventos predominantes

- **Pró:** desacoplamento e escala.
- **Contra:** consistência eventual e operação mais complexa.

### Alternativa 3C: APIs + eventos conforme semântica — recomendada

- comandos/consultas imediatas por API;
- fatos ocorridos por eventos;
- outbox/inbox, idempotência, schema registry e tracing.

**Decisão proposta:** 3C.

---

## ABB 4 — Integração com legado

### Alternativa 4A: acesso direto/DB compartilhado

- **Pró:** rapidez aparente.
- **Contra:** alto acoplamento e violação de ownership.
- **Decisão:** proibida no alvo.

### Alternativa 4B: ESB/modelo canônico corporativo amplo

- **Pró:** mediação central.
- **Contra:** lógica de domínio no middleware e gargalo organizacional.

### Alternativa 4C: Anti-Corruption Layer por fronteira — recomendada

Traduz modelos e protege o domínio novo; eventos legados são publicados com contrato governado.

- **Pró:** suporta Strangler e reduz contaminação semântica.
- **Contra:** duplicidade temporária e custo de transição.

**Decisão proposta:** 4C.

---

## ABB 5 — Orquestração de pagamentos

### Alternativa 5A: coreografia pura

- **Pró:** baixo acoplamento central.
- **Contra:** difícil visualizar estado e compensações de fluxo monetário.

### Alternativa 5B: orquestrador de domínio — recomendada

Pagamentos mantém estado da ordem e coordena Conta, Ledger, Fraude e Pix.

- **Pró:** auditabilidade, tratamento de timeout e compensação.
- **Contra:** exige evitar concentração de regras pertencentes a outros domínios.

### Alternativa 5C: BPM corporativo central

- **Pró:** visibilidade e configuração.
- **Contra:** possível gargalo e acoplamento de domínios.

**Decisão proposta:** 5B; BPM/case management pode apoiar trabalho humano sem ser owner do pagamento.

---

## ABB 6 — Dados analíticos

### Alternativa 6A: consultas aos bancos operacionais

Rejeitada por risco, carga e acoplamento.

### Alternativa 6B: data lake central sem produtos/owners

- **Pró:** ingestão rápida.
- **Contra:** baixa qualidade e contexto.

### Alternativa 6C: data products orientados a domínio — recomendada

Eventos/CDC alimentam produtos de dados com owner, SLA, qualidade e lineage.

**Decisão proposta:** 6C, sobre a plataforma analítica corporativa existente quando aderente.

---

## ABB 7 — Identidade de cliente

### Alternativa 7A: cadastro mestre central para toda escrita

- **Pró:** visão única.
- **Contra:** gargalo e modelo universal rígido.

### Alternativa 7B: identidade mestre + dados contextuais — recomendada

Cliente mantém identidade e vínculos comuns; cada domínio mantém atributos próprios, referenciando o identificador corporativo.

### Alternativa 7C: identidades independentes reconciliadas apenas em analytics

Insuficiente para jornadas operacionais e compliance.

**Decisão proposta:** 7B.

---

## ABB 8 — Segurança e autorização

### Alternativa 8A: controles em cada aplicação

Rejeitada por inconsistência.

### Alternativa 8B: gateway como único controle

Insuficiente: tráfego interno e autorização de domínio permanecem expostos.

### Alternativa 8C: zero trust em camadas — recomendada

CIAM/IAM, gateway/WAF, identidade de workload, policy enforcement, KMS/HSM, SIEM e autorização no domínio.

**Decisão proposta:** 8C.

---

## Portfólio ABB recomendado

| Código | ABB | Alternativa |
|---|---|---|
| ABB-01 | Catálogo e Composição de Produtos | 1B |
| ABB-02 | Conta e Ledger | 2B |
| ABB-03 | API e Event Integration | 3C |
| ABB-04 | Anti-Corruption Layer | 4C |
| ABB-05 | Payment Orchestration | 5B |
| ABB-06 | Domain Data Products | 6C |
| ABB-07 | Customer Identity | 7B |
| ABB-08 | Security Architecture | 8C |
| ABB-09 | Compliance Services | KYC/AML/Fraude componíveis |
| ABB-10 | Observability/SRE | telemetria e SLO ponta a ponta |
| ABB-11 | Developer Platform | paved roads e policy as code |
| ABB-12 | Reconciliation | comparação e gestão de divergências |

## Gate de decisão ABB

Cada ABB deve ter capacidade/requisito associado, owner, contratos, NFRs, alternativas avaliadas, riscos, decisão registrada em ADR e critérios para seleção de SBB.
