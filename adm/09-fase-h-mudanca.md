# Fase H — Gestão de Mudanças da Arquitetura

## Objetivo

Monitorar resultados, mudanças internas/externas e dívida arquitetural; decidir se a arquitetura continua válida ou se exige novo ciclo ADM.

## Fontes de mudança

- regulação e arranjos de pagamento;
- comportamento e feedback dos clientes;
- estratégia, fusões ou novos parceiros;
- volumes, custos e incidentes;
- obsolescência tecnológica;
- alterações de fornecedor e SLA;
- fraude e novas ameaças;
- resultados dos KPIs e experimentos.

## Processo contínuo

1. coletar sinais e métricas;
2. classificar impacto em negócio, dados, aplicações e tecnologia;
3. comparar com princípios, requisitos e arquitetura alvo;
4. decidir entre ajuste local, change request ou novo ciclo ADM;
5. atualizar roadmap, repository e Architecture Contract;
6. medir resultado da mudança.

## Critérios de escalonamento

| Tipo de mudança | Tratamento |
|---|---|
| correção dentro de padrões | backlog do domínio |
| novo SBB mantendo ABB/contratos | revisão técnica local |
| alteração de contrato cross-domain | Architecture Board |
| mudança de capability/value stream | novo incremento B/C/D |
| mudança estratégica/regulatória relevante | reiniciar Fase A |
| risco crítico | resposta emergencial e revisão posterior |

## Simulação após o MVP

### Cenário 1 — Ativação abaixo da meta

Analisar jornada, elegibilidade e proposta de valor. Não escalar infraestrutura nem adicionar cashback automaticamente. Retornar às Fases A/B para revisar hipótese e jornada.

### Cenário 2 — Fornecedor aumenta custo por transação

Executar análise TCO e portabilidade. Se ultrapassar tolerância, avaliar SBB alternativo preservando ABBs e contratos.

### Cenário 3 — Cashback aprovado

Abrir novo incremento ADM: confirmar business case, modelar Rewards/Parceiros, atualizar requisitos, selecionar SBBs e integrar via `PagamentoLiquidado`.

### Cenário 4 — Crédito deseja reutilizar Conta/Cliente

Avaliar capacidade, contratos e migração por jornada. Atualizar roadmap da Onda 3 e medir redução de duplicação.

## Métricas de saúde arquitetural

- lead time e frequência de deploy;
- adoção dos paved roads;
- contratos quebrados e exceções abertas;
- duplicação de capacidades;
- dependências ponto a ponto;
- SLO e error budget;
- custo unitário;
- idade/dívida dos componentes;
- tempo para substituir fornecedor;
- realização de benefícios.

## Entregáveis simulados

- Architecture Change Requests;
- relatório de saúde e valor;
- technology/business watchlist;
- backlog de dívida e oportunidades;
- roadmap atualizado;
- decisão de novo ciclo ADM.

## Gate periódico

Trimestralmente, o Comitê decide continuar, pivotar, acelerar, desacelerar ou encerrar work packages com base em valor, risco e custo observados.
