# Fase A — Visão de Arquitetura

## Objetivo

Alinhar problema, valor, escopo, stakeholders e restrições; comparar Conta de Pagamentos e Cashback; obter autorização para o trabalho arquitetural.

## Pergunta executiva

Qual produto aumenta o engajamento e, ao mesmo tempo, cria uma fundação reutilizável para acelerar novos lançamentos?

## Simulação da etapa

### 1. Problema e drivers

- **Confirmado:** produtos de crédito foram construídos em silos.
- **Confirmado:** Conta de Pagamentos e Cashback tiveram boa aceitação em testes.
- **Confirmado:** apenas um produto será priorizado.
- **Driver:** aumentar engajamento e portfólio.
- **Driver:** acelerar lançamentos sem abandonar microservices.
- **Restrição:** coexistência com legados e continuidade operacional.

### 2. Stakeholders e concerns

| Stakeholder | Concern | Resposta na visão |
|---|---|---|
| C-level | crescimento e retorno | Conta como relação recorrente e plataforma reutilizável |
| CTO | eventual aquisição de core | fit-gap buy/build/compose antes da compra |
| CIO | alinhamento corporativo | capability map, roadmap e governança |
| Produto | time-to-market | catálogo, APIs, eventos e jornadas reutilizáveis |
| Risco/Compliance | exposição regulatória | controles desde o desenho e gates |
| Operações | conciliação e exceções | ledger, workflow, SLO e observabilidade |
| Clientes | simplicidade e confiança | onboarding digital, Pix e suporte integrado |

### 3. Opções avaliadas

| Opção | Valor | Limitação | Decisão simulada |
|---|---|---|---|
| Cashback primeiro | entrega rápida | engajamento dependente de parceiros e campanhas | manter no roadmap |
| Conta de Pagamentos | base transacional e alto reuso | maior risco/custo inicial | **recomendada** |
| Comprar core integral | rapidez potencial | lock-in e risco de novo silo | não aprovar sem fit-gap |
| Plataforma componível | flexibilidade e evolução | exige governança e integração | **direção recomendada** |

Pontuação da visão: Conta 4,25/5; Cashback 3,20/5, conforme documento principal.

### 4. Escopo

**Incluído:** onboarding, cliente/consentimento, conta, ledger, Pix, risco/compliance, conciliação, atendimento, APIs/eventos e integração progressiva com crédito.

**Posterior:** cashback, campanhas e ecossistema ampliado.

**Fora do primeiro ciclo:** substituição integral dos sistemas de crédito e migração big bang.

### 5. Cenário de negócio

1. cliente recebe oferta digital;
2. conclui cadastro, consentimento e KYC;
3. banco cria conta e identidade financeira;
4. cliente ativa a conta com Pix;
5. eventos permitem atendimento, analytics e personalização;
6. produtos de crédito passam a reutilizar capacidades comuns;
7. cashback é conectado posteriormente aos eventos liquidados.

### 6. KPIs e hipóteses de valor

| Objetivo | KPI | Hipótese |
|---|---|---|
| Engajar | MAU e transações/cliente/mês | conta aumenta frequência |
| Relacionar | produtos ativos/cliente | conta facilita cross-sell |
| Acelerar | lead time de produto | building blocks reduzem esforço repetido |
| Reutilizar | percentual de capacidades compartilhadas | cliente, risco, eventos e pagamentos atendem múltiplos produtos |
| Operar | disponibilidade e sucesso | SRE reduz falhas e tempo de recuperação |
| Controlar | fraude e não conformidade | controles comuns aumentam consistência |

Metas numéricas dependem de baseline.

## Entregáveis simulados

- Architecture Vision;
- Statement of Architecture Work;
- mapa de stakeholders;
- business case inicial;
- riscos e premissas;
- decisão do produto;
- escopo e critérios de sucesso;
- requisitos de alto nível.

## Gate de saída

O Comitê aprova:

1. Conta de Pagamentos como prioridade;
2. plataforma componível como direção;
3. etapa de baseline e PoCs;
4. patrocinadores e funding inicial;
5. ausência de compromisso antecipado com core integral.

## Evidências requeridas

Baseline de engajamento e custos, viabilidade regulatória, capacidade operacional, volumes, orçamento, pesquisa de cliente e avaliação inicial de fornecedores.
