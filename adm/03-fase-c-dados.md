# Fase C1 — Arquitetura de Dados

## Objetivo

Definir ownership, fluxos, qualidade, segurança e ciclo de vida dos dados necessários à Conta de Pagamentos e à redução dos silos.

## Simulação AS-IS

- múltiplas representações de cliente por produto;
- dados de produto, risco e operação acoplados aos sistemas;
- reconciliação tardia e dependente de extrações;
- analytics alimentado por cargas heterogêneas;
- lineage, finalidade e retenção incompletos;
- compartilhamento por tabelas, arquivos ou integrações ponto a ponto.

## Domínios e ownership TO-BE

| Objeto | Sistema/contexto autoritativo | Regra |
|---|---|---|
| Cliente | Cliente | identidade, dados cadastrais e vínculos |
| Consentimento | Consentimento/IAM | finalidade, escopo, vigência e revogação |
| Produto | Catálogo de Produtos | definição e versão comercial |
| Conta | Conta | estado, titulares e restrições |
| Lançamento | Ledger | registro monetário imutável de dupla entrada |
| Saldo | Ledger | projeção derivada de lançamentos |
| Pagamento | Pagamentos | ciclo de vida da ordem |
| Avaliação de risco | Risco/Fraude | decisão, motivo e evidência |
| Caso operacional | Case Management | investigação, responsável e resolução |
| Recompensa futura | Cashback | accrual, resgate, funding e liquidação |

Nenhum consumidor altera diretamente os dados de outro contexto.

## Fluxo simulado

`API transacional → contexto owner → banco privado → outbox → event backbone → consumidores operacionais/analytics`

- APIs atendem comandos e consultas que exigem resposta imediata;
- eventos divulgam fatos já ocorridos;
- CDC é usado para migração/integração controlada, não como contrato permanente sem owner;
- dados analíticos são publicados como data products com SLA e qualidade.

## Regras de arquitetura

1. identificadores globais e mapeamento de IDs legados;
2. classificação por sensibilidade e finalidade;
3. criptografia em trânsito e repouso; tokenização quando necessária;
4. minimização e retenção automatizada;
5. schema registry e compatibilidade de eventos;
6. qualidade medida na origem;
7. lineage ponta a ponta;
8. segregação entre dados operacionais e analíticos;
9. trilha de acesso e alteração;
10. reconciliação financeira independente.

## Migração de dados simulada

1. perfilar fontes e definir golden rules;
2. mapear IDs e semântica por domínio;
3. corrigir dados críticos na origem quando possível;
4. carregar baseline versionado;
5. sincronizar deltas por CDC/outbox;
6. executar reconciliação técnica, funcional e financeira;
7. migrar coortes;
8. congelar escrita no legado por capacidade;
9. reter/arquivar conforme política;
10. desativar somente após aceite do owner.

## Qualidade e controles

| Dimensão | Exemplo de métrica |
|---|---|
| Completude | cadastros com campos mandatórios |
| Unicidade | clientes duplicados por milhão |
| Atualidade | atraso de propagação de evento |
| Consistência | divergência Conta × Ledger × Pix |
| Precisão | taxa de correção após onboarding |
| Integridade | lançamentos não balanceados = zero |

## Entregáveis simulados

- data entity/data component catalog;
- data lifecycle diagrams;
- matriz CRUD/ownership;
- classificação e política de dados;
- modelo canônico mínimo de integração;
- plano de qualidade, lineage e migração;
- data governance backlog.

## Gate de saída

- owners de dados nomeados;
- invariantes financeiras aprovadas;
- DPO/Segurança aprovam finalidade e controles;
- estratégia de migração e reconciliação testável;
- requisitos de dados rastreados para ABBs/SBBs.

## Evidências requeridas

Dicionários, esquemas, volumes, qualidade real, política LGPD, retenção, lineage atual, relatórios regulatórios e regras contábeis.
