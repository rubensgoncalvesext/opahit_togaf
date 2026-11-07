# Fase G — Governança da Implementação

## Objetivo

Assegurar que soluções e entregas permaneçam aderentes à arquitetura aprovada e produzam os resultados esperados sem bloquear a autonomia dos times.

## Architecture Contract simulado

O contrato registra:

- outcomes, escopo e KPIs;
- princípios e ABBs obrigatórios;
- NFRs e SLOs;
- owners e direitos de decisão;
- padrões de dados, APIs e eventos;
- controles de segurança/compliance;
- evidências e checkpoints;
- processo de exceção e prazo de remediação.

## Checkpoints

| Momento | Evidência |
|---|---|
| Discovery | hipótese, jornada, domínio, risco e KPI |
| Solution design | ABB/SBB, ADRs, threat model e contratos |
| Build | testes, IaC, SBOM, telemetria e qualidade |
| Pre-production | desempenho, resiliência, DR, segurança e runbook |
| Go-live | aceite operacional, reconciliação, rollback e comunicação |
| Pós-implantação | SLO, incidentes, custos e benefícios |

## Scorecard de conformidade

| Dimensão | Exemplo de controle |
|---|---|
| Negócio | entrega está ligada a capacidade/KPI? |
| Domínio | owner e bounded context estão claros? |
| Dados | ownership, finalidade, qualidade e lineage existem? |
| Integração | APIs/eventos são versionados e testados? |
| Segurança | threat model e controles foram validados? |
| Resiliência | SLO, capacidade, DR e falhas foram testados? |
| Operação | dashboards, alertas e runbooks estão ativos? |
| Portabilidade | dados e contratos permitem saída? |
| Custo | orçamento e custo unitário são observáveis? |

## Processo de exceção

1. time registra desvio, motivo, risco e alternativas;
2. owner de padrão avalia impacto;
3. Architecture Board aprova, condiciona ou rejeita;
4. exceção recebe responsável, prazo e compensating controls;
5. expiração força revisão; exceção não se torna padrão tacitamente.

## Governança de fornecedor

- SLAs/SLOs e direito de auditoria;
- portabilidade e exportação testada;
- notificação de incidentes e mudanças;
- roadmap e compatibilidade contratual;
- continuidade, concentração e subcontratados;
- métricas de custo e consumo;
- teste periódico de exit plan.

## Simulação de não conformidade

**Caso:** time propõe acesso direto ao banco do Ledger para gerar extrato.

**Decisão:** rejeitar. Usar API/projeção autorizada; registrar requisito de desempenho; testar alternativa de read model. Razão: preservar invariantes, ownership e auditabilidade.

## Entregáveis simulados

- Architecture Contract;
- compliance assessments;
- atas e ADRs;
- registro de exceções;
- readiness reviews;
- relatórios de fornecedor;
- recomendações de correção.

## Gate de saída por release

Não liberar fluxo monetário sem idempotência, reconciliação, threat model, testes de desempenho/resiliência, observabilidade, runbook, rollback e aceite de Operações/Risco.
