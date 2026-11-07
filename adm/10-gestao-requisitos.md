# Gestão de Requisitos — Processo Contínuo

## Objetivo

Capturar, classificar, priorizar e rastrear requisitos durante todo o ADM, controlando mudanças e demonstrando por que cada entrega existe.

## Fluxo

`Fonte → Requisito → Classificação → Priorização → Capacidade → ABB → SBB → Work Package → Teste/Evidência → KPI`

## Classificações

- negócio e outcome;
- funcional;
- dados;
- aplicação/integração;
- tecnologia;
- segurança, privacidade e regulatório;
- qualidade/NFR;
- transição/migração;
- operação e fornecedor.

## Catálogo simulado

| ID | Requisito | Classe | Prioridade | Fase de origem | ABB | Evidência |
|---|---|---|---|---|---|---|
| BR-01 | aumentar engajamento | negócio | Must | A | Engajamento/Conta | MAU e frequência |
| BR-02 | acelerar lançamentos | negócio | Must | A/B | Catálogo/Plataforma | lead time e reuso |
| FR-01 | abrir conta | funcional | Must | B | Conta | teste E2E |
| FR-02 | executar Pix | funcional | Must | B/C | Pagamentos | sucesso e reconciliação |
| DR-01 | owner único por dado | dados | Must | C | Data Ownership | matriz CRUD/lineage |
| AR-01 | preservar microservices | arquitetura | Must | A/C | Runtime/Contexts | conformidade |
| NFR-01 | integridade monetária | qualidade | Must | C/D | Ledger | soma débito/crédito e auditoria |
| NFR-02 | resiliência | qualidade | Must | D | SRE/DR | chaos/DR test |
| SR-01 | KYC/AML/LGPD | regulatório | Must | A–D | Compliance | aceite formal |
| TR-01 | coexistência com legado | transição | Must | E/F | ACL/Strangler | cutover/rollback |
| VR-01 | portabilidade | fornecedor | Should | E | Exit/Export | teste de saída |
| FR-03 | cashback | funcional | Could | A/H | Rewards | business case futuro |

## Priorização

- **Must:** legal, segurança, integridade ou necessário ao MVP;
- **Should:** alto valor, mas admite alternativa temporária controlada;
- **Could:** valor posterior;
- **Won't now:** explicitamente fora do incremento.

Valor não sobrepõe requisito regulatório ou de integridade.

## Processo de mudança

1. registrar origem, motivo e urgência;
2. analisar impacto em capacidades, arquiteturas e contratos;
3. estimar custo, risco e benefício;
4. obter decisão do owner/fórum apropriado;
5. versionar baseline;
6. atualizar testes, roadmap e comunicação;
7. verificar resultado.

## Matriz de rastreabilidade de exemplo

`BR-02 → Gestão de Produtos → ABB Catálogo/Composição → SBB selecionado → WP2 → release Onda 1 → teste de configuração → lead time de produto`

`NFR-01 → Movimentação Financeira → ABB Ledger → SBB de ledger → WP4 → Onda 2 → reconciliação/invariantes → divergências financeiras`

## Quality attributes

NFRs devem usar cenários mensuráveis: fonte, estímulo, ambiente, artefato, resposta e medida. “Alta disponibilidade” sem número, jornada e período não é requisito verificável.

## Governança

- Product Owner: valor e prioridade;
- Domain Owner: semântica e regra;
- Risco/Compliance/Segurança: requisitos mandatórios;
- Arquitetura: impacto cross-domain;
- QA/SRE: verificabilidade e evidência;
- Comitê: conflitos de investimento/apetite de risco.

## Entregáveis

- Requirements Repository;
- baselines por incremento;
- matriz de rastreabilidade;
- change log;
- critérios de aceite;
- relatório de cobertura e requisitos órfãos.
