# Fase E — Oportunidades e Soluções

## Objetivo

Transformar gaps das arquiteturas B/C/D em work packages, arquiteturas de transição e opções de solução; consolidar a estratégia buy/build/compose.

## Gaps consolidados

1. identidade de cliente e consentimento fragmentados;
2. ausência de catálogo/composição de produtos;
3. conta, ledger e pagamentos não compartilháveis;
4. risco, compliance e conciliação repetidos;
5. integração ponto a ponto;
6. plataforma e observabilidade heterogêneas;
7. operating model orientado a silos;
8. dados sem ownership e lineage ponta a ponta.

## Work packages simulados

| WP | Escopo | Dependências | Valor |
|---|---|---|---|
| WP0 Governança e baseline | inventário, métricas, princípios, modelo regulatório | patrocínio | reduz incerteza |
| WP1 Plataforma mínima | IAM, APIs, eventos, CI/CD, observabilidade | WP0 | paved road reutilizável |
| WP2 Cliente e Produto | identidade, consentimento, catálogo | WP1 | visão integrada e composição |
| WP3 Compliance | KYC, AML, fraude, casos | WP1/2 | controle comum |
| WP4 Conta e Ledger | ciclo de vida, postings, saldo, extrato | WP1/2/3 | núcleo da conta |
| WP5 Pix e Operações | pagamentos, limites, reconciliação, atendimento | WP4 | MVP operacional |
| WP6 Integração Crédito | ACL, eventos e capacidades comuns | WP1/2 | redução de silos |
| WP7 Engajamento | analytics, ofertas e experimentos | WP1/2/5 | frequência e cross-sell |
| WP8 Cashback | rewards, parceiros, funding e settlement | WP5/7 | evolução do engajamento |

## Alternativas de solução

### Opção A — Core bancário integral

- vantagem: suíte funcional e responsabilidade concentrada;
- risco: lock-in, customização, novo silo e menor autonomia;
- uso: somente se fit-gap e TCO forem claramente superiores.

### Opção B — Core/BaaS componível

- vantagem: acelera capacidades comoditizadas mantendo diferenciação;
- risco: integração e operação distribuída;
- **recomendação simulada:** opção preferencial, condicionada a PoCs.

### Opção C — Construção predominante

- vantagem: controle e aderência;
- risco: prazo, custo e complexidade regulatória/operacional;
- uso: apenas em capacidades diferenciadoras ou sem solução aderente.

## Matriz buy/build/compose

| Capacidade | Direção inicial | Motivo |
|---|---|---|
| Experiência/jornadas | Build | diferenciação |
| Catálogo/composição | Build ou produto extensível | autonomia de produto |
| Ledger | Buy/compose ou build especializado | criticidade e maturidade de mercado |
| Pix | Buy/compose/BaaS | conectividade e regulação |
| KYC/AML/Fraude | Buy + regras próprias | commodity especializada |
| Conta/Pagamentos | Compose | combinar domínio próprio e componentes |
| Eventos/observabilidade | plataforma vigente ou buy | padronização tecnológica |
| Cashback | Build/compose posterior | diferenciação e ecossistema |

## PoCs obrigatórias

- pagamento e lançamento ponta a ponta;
- idempotência, falha e retomada;
- reconciliação e divergência;
- alteração/configuração de produto;
- volume e latência;
- exportação integral e reconstituição;
- observabilidade e suporte;
- simulação de substituição/saída.

## Entregáveis simulados

- implementation and migration strategy;
- work package portfolio;
- transition architectures;
- benefit dependency network;
- solução conceitual e matriz buy/build/compose;
- RFI/RFP e critérios de PoC;
- business case refinado.

## Gate de saída

- work packages com owner, benefício, custo e dependências;
- ABBs mapeados a opções de SBB;
- fornecedores aprovados somente após evidências;
- arquitetura de transição viável operacionalmente;
- business case atualizado pelo Comitê.
