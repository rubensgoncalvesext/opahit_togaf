# Fase F — Planejamento da Migração

## Objetivo

Priorizar work packages, definir ondas e produzir um plano executável que equilibre valor, risco, dependências, custo e capacidade organizacional.

## Critérios de priorização

| Critério | Peso indicativo |
|---|---:|
| valor/engajamento | 25% |
| habilitação de outras capacidades | 20% |
| redução de risco | 15% |
| urgência regulatória | 15% |
| esforço/custo | 10% |
| prontidão organizacional | 10% |
| redução de legado | 5% |

Pesos são hipótese e devem ser aprovados.

## Roadmap simulado

### Onda 0 — 0 a 3 meses

Baseline, arquitetura, modelo regulatório, operating model, inventário, RFI/RFP e PoCs.

**Saída:** go/no-go, orçamento e sourcing.

### Onda 1 — 3 a 6 meses

Plataforma mínima, IAM/consentimento, cliente, catálogo, eventos e ACL de legado.

**Saída:** primeira visão integrada e contratos governados.

### Onda 2 — 6 a 12 meses

Onboarding, KYC/AML, Conta, Ledger, Pix, fraude, conciliação, atendimento e piloto por coorte.

**Saída:** Conta MVP operacional.

### Onda 3 — 12 a 18 meses

Escala, automação, integração com crédito, migração de capacidades duplicadas e desativação controlada.

**Saída:** plataforma reutilizada por múltiplos produtos.

### Onda 4 — 18+ meses

Cashback, parceiros, ofertas e expansão do ecossistema.

**Saída:** engajamento e monetização adicionais.

## Arquiteturas de transição

| Estado | Característica | Controle-chave |
|---|---|---|
| T0 | silos predominantes | inventário e baseline |
| T1 | fachada/ACL + plataforma mínima | contratos e observabilidade |
| T2 | conta nova coexistindo com legado | parallel run e reconciliação |
| T3 | capacidades comuns consumidas por crédito | roteamento por jornada/coorte |
| T4 | silos reduzidos e cashback conectado | desativação e benefícios realizados |

## Estratégia de cutover

1. selecionar jornada/coorte de baixo risco;
2. migrar dados e validar qualidade;
3. executar shadow/parallel run quando aplicável;
4. reconciliar negócio, tecnologia e finanças;
5. habilitar feature flag e monitorar SLO;
6. aumentar tráfego progressivamente;
7. manter rollback testado;
8. retirar legado após critérios de saída.

## Critérios de desativação

- consumidores conhecidos e migrados;
- paridade necessária, não reprodução cega de todo legado;
- dados reconciliados e retenção atendida;
- controles e auditoria aprovados;
- operação e suporte treinados;
- rollback/restore testados;
- contratos/licenças encerráveis;
- custo legado efetivamente removido.

## Plano de benefícios

Cada onda terá baseline, meta, owner e frequência. Exemplos: ativação, transações, lead time, reuso, custo por transação, incidentes, fraude e esforço manual.

## Entregáveis simulados

- prioritized portfolio;
- implementation and migration plan;
- roadmap e release plan;
- transition architecture diagrams;
- benefits realization plan;
- risk register e dependency matrix;
- estimativas e plano de recursos.

## Gate de saída

- Finanças valida business case e funding por onda;
- owners aceitam dependências e capacidade;
- Operações/Risco aprovam cutover e rollback;
- Comitê aprova gates e tolerâncias.
