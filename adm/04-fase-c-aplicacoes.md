# Fase C2 — Arquitetura de Aplicações

## Objetivo

Definir os bounded contexts, serviços, APIs, eventos e interações que implementam as capacidades de negócio sem reproduzir os silos atuais.

## Portfólio AS-IS simulado

- aplicações verticais para CDC, cartão, crédito pessoal, consignado e garantias;
- cadastros e regras duplicados;
- integrações síncronas ponto a ponto;
- bancos compartilhados ou extrações diretas;
- canais dependentes da estrutura interna de cada produto.

## Bounded contexts TO-BE

| Contexto | Responsabilidade | Interfaces principais |
|---|---|---|
| Cliente | identidade e relacionamentos | Customer API, ClienteAtualizado |
| Consentimento/IAM | autenticação, autorização e consentimento | OAuth/OIDC, ConsentimentoRevogado |
| Catálogo | produtos, versões, preços e elegibilidade | Product API, ProdutoPublicado |
| Conta | ciclo de vida e restrições | Account API, ContaAtivada |
| Ledger | lançamentos, reservas e saldos | Posting API, LancamentoEfetivado |
| Pagamentos | ordem, status, devolução e saga | Payment API, PagamentoLiquidado |
| Risco/Fraude | avaliação e casos | Risk API, TransacaoBloqueada |
| Conciliação | comparação, divergência e resolução | Reconciliation API/Event |
| Ofertas | decisão e personalização | Offer API, OfertaAceita |
| Parceiros | onboarding e contratos | Partner API |
| Cashback futuro | regras, accrual e resgate | Rewards API/Event |

## Padrões de interação

- BFF por experiência, sem regra central de domínio;
- API Gateway para exposição, segurança e quotas;
- APIs síncronas para validações imediatas;
- eventos para fatos e integração desacoplada;
- transactional outbox/inbox e idempotência;
- sagas com compensações em fluxos distribuídos;
- anti-corruption layer para legados e fornecedores;
- database per bounded context;
- consumer-driven contract tests;
- versionamento compatível e política de depreciação.

## Cenário simulado: Pix

1. BFF envia ordem idempotente a Pagamentos.
2. Pagamentos solicita avaliação de Fraude.
3. Conta valida estado/limites.
4. Ledger reserva fundos.
5. adaptador Pix envia ordem externa.
6. confirmação efetiva lançamento de dupla entrada.
7. Pagamentos publica `PagamentoLiquidado`.
8. Notificação, Analytics e Ofertas consomem o evento.
9. Conciliação compara registros internos e externos.

Timeout não equivale a falha: a ordem fica em estado desconhecido até consulta/reconciliação. Retry não pode duplicar lançamento.

## Decomposição e implantação

Um bounded context não implica necessariamente um único microservice. A divisão física ocorrerá apenas quando houver necessidade independente de escala, segurança, ciclo de vida ou ownership. Evita-se serviço por entidade e transação distribuída excessiva.

## Migração de aplicações

- fachada/API e ACL à frente dos legados;
- publicar eventos legados governados;
- direcionar novas jornadas aos contextos novos;
- migrar capacidade por capacidade;
- manter execução paralela e reconciliação;
- remover interfaces antigas após consumer mapping e aceite.

## Entregáveis simulados

- application portfolio catalog;
- interface catalog;
- context map;
- application communication diagram;
- API/event standards;
- matriz aplicação × capacidade;
- gap analysis e plano de racionalização.

## Gate de saída

- fronteiras e owners aceitos;
- ausência de banco compartilhado no desenho alvo;
- cenários felizes e de exceção modelados;
- contratos críticos prototipados;
- aplicações candidatas a manter, modernizar ou retirar classificadas.

## Evidências requeridas

Inventário de aplicações/interfaces, dependências reais, SLAs, custos, incidentes, tecnologias, contratos e consumidores.
