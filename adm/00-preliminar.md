# Etapa Preliminar — Preparar a Capacidade de Arquitetura

## Objetivo

Definir como a arquitetura será desenvolvida e governada antes de iniciar formalmente o ciclo ADM da Conta de Pagamentos.

## Entradas

- estratégia de crescimento e engajamento;
- portfólio de crédito em silos;
- práticas atuais de arquitetura e engenharia;
- obrigações regulatórias e políticas corporativas;
- estruturas de decisão, orçamento e sourcing existentes.

## Simulação da etapa

### 1. Avaliação de maturidade

| Dimensão | Situação simulada AS-IS | Alvo inicial |
|---|---|---|
| Governança | decisões locais por produto | Architecture Board e gates federados |
| Domínios | fronteiras orientadas a sistemas | bounded contexts e owners de capacidades |
| Integração | ponto a ponto | API-first e eventos governados |
| Dados | duplicados por silo | ownership, catálogo, lineage e qualidade |
| Entrega | pipelines heterogêneos | paved roads DevSecOps |
| Operação | observabilidade parcial | SLOs, tracing e operação por produto |
| Sourcing | avaliação centrada em funcionalidade | fit-gap por capacidade, TCO e exit plan |

A maturidade deve ser confirmada por entrevistas e evidências; a tabela é uma hipótese de trabalho.

### 2. Tailoring do TOGAF

- usar entregáveis enxutos e vinculados a decisões;
- separar Fase C em Dados e Aplicações;
- executar B, C e D em iterações por value stream;
- usar DDD/Event Storming na descoberta das fronteiras;
- registrar decisões relevantes em ADRs;
- gerir modelos no Architecture Repository;
- adotar checkpoints leves para experimentos e completos para fluxos financeiros.

### 3. Princípios aprováveis

1. Capacidade antes de sistema.
2. Bounded context antes de microservice.
3. Dados e regras possuem owner único.
4. Ledger é a fonte monetária autoritativa.
5. Segurança, privacidade e compliance by design.
6. APIs e eventos têm contratos versionados.
7. Automação, resiliência e observabilidade por padrão.
8. Migração incremental, sem big bang.
9. Buy/build/compose com portabilidade e saída.
10. Resultado de negócio governa continuidade do investimento.

### 4. Estrutura de governança

| Papel | Responsabilidade |
|---|---|
| Comitê Executivo | direção, funding e apetite de risco |
| Patrocinador de Negócio | valor, priorização e resultado |
| CIO/CTO | capacidade tecnológica e sourcing |
| Architecture Board | decisões cross-domain e conformidade |
| Product Owner | outcomes e backlog do value stream |
| Domain Owner | semântica, regras, dados e operação |
| Risco/Compliance | controles e aceite regulatório |
| Segurança/Dados/SRE | padrões e evidências não funcionais |

### 5. Metamodelo mínimo

`Objetivo → Requisito → Value Stream → Capacidade → Bounded Context → ABB → SBB → Work Package → Entrega → KPI`

Cada elemento deve possuir owner, estado, versão e relacionamentos rastreáveis.

## Entregáveis simulados

- Architecture Charter;
- princípios de arquitetura;
- estrutura e mandato do Architecture Board;
- tailoring do ADM;
- metamodelo e repositório;
- catálogo inicial de stakeholders;
- processo de exceção e conformidade;
- plano de capacitação em DDD, eventos, segurança e SRE.

## Gate de saída

- patrocinadores nomeados;
- mandato e direitos de decisão aprovados;
- princípios publicados;
- repositório e templates disponíveis;
- recursos para executar a Fase A autorizados.

## Riscos da etapa

- governança excessivamente centralizada: usar guardrails e decisões federadas;
- processo documental: exigir artefatos somente quando sustentarem decisão;
- falta de autoridade: patrocínio executivo e Architecture Contract explícitos.
