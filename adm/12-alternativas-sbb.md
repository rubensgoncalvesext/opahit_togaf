# Alternativas de Solution Building Blocks (SBB)

## Objetivo

Comparar alternativas de implementação para os ABBs sem escolher marcas prematuramente. Os nomes abaixo representam **categorias de solução**; produtos concretos serão avaliados por RFI/RFP e PoC.

## Estratégias globais

| Estratégia | Descrição | Vantagem | Risco |
|---|---|---|---|
| S1 Suíte/Core integral | fornecedor cobre grande parte da solução | integração funcional de origem | lock-in, customização e novo silo |
| S2 Composable/BaaS | componentes especializados por contratos | velocidade e flexibilidade | operação e integração distribuídas |
| S3 Build predominante | banco constrói os componentes | controle e diferenciação | prazo, custo e especialização |
| S4 Híbrida | build no diferencial e buy no commodity | equilíbrio | exige forte arquitetura/governança |

**Direção recomendada:** S4, usando S2 para capacidades maduras e regulatórias.

---

## SBB para Conta e Ledger

### Opção L1 — Ledger/core SaaS componível

- APIs de postings, reservas, saldo e extrato;
- eventos e exportação completa;
- operação gerenciada.

**Vantagens:** menor tempo e experiência especializada.  
**Riscos:** soberania, custo por volume, limites de customização e saída.

### Opção L2 — Produto de ledger implantado na infraestrutura do banco

**Vantagens:** maior controle operacional e de dados.  
**Riscos:** banco assume upgrades, capacidade e operação crítica.

### Opção L3 — Construção própria

**Vantagens:** aderência e controle.  
**Riscos:** alta responsabilidade sobre integridade, reconciliação, auditoria e evolução.

**Preferência simulada:** PoC de L1 e L2; L3 somente se requisitos diferenciais não forem atendidos.

**Testes:** dupla entrada, idempotência, reservas, estornos, concorrência, fechamento, replay/exportação, DR, performance e reconciliação.

---

## SBB para Pix/conectividade

### Opção P1 — BaaS/participante indireto

- acelera entrada e reduz operação inicial;
- gera dependência de SLA, preço e roadmap.

### Opção P2 — Conectividade própria/participação direta

- maior controle e economia potencial em escala;
- maior complexidade regulatória, certificação e operação.

### Opção P3 — Gateway/adaptador multprovedor

- permite trocar/combinar provedores;
- adiciona camada operacional e deve evitar abstração pelo menor denominador comum.

**Preferência simulada:** P1 no MVP com arquitetura P3-ready; reavaliar P2 por volume e estratégia.

---

## SBB para KYC, AML e fraude

### Opção R1 — Provedor único integrado

**Pró:** implantação simples.  
**Contra:** concentração e cobertura possivelmente mediana.

### Opção R2 — Orquestração própria com provedores especializados

**Pró:** regras e experiência diferenciadas; substituição por componente.  
**Contra:** mais integração, casos e monitoramento.

### Opção R3 — Construção integral

Não recomendada para fontes/verificações comoditizadas; regras e decisão podem permanecer no banco.

**Preferência simulada:** R2, com case management e trilha sob governança do banco.

---

## SBB para APIs e eventos

### APIs

- **A1 plataforma corporativa existente:** preferir se atender segurança, escala, portal e analytics;
- **A2 serviço gerenciado:** menor operação, avaliar portabilidade/custo;
- **A3 solução autogerenciada:** maior controle, maior carga operacional.

### Eventos

- **E1 streaming distribuído:** alto throughput, replay e ecossistema; maior operação;
- **E2 broker de mensageria:** filas/roteamento maduros; replay/analytics podem ser limitados;
- **E3 serviço gerenciado:** reduz operação; avaliar lock-in e custo.

**Preferência simulada:** reutilizar plataforma corporativa aderente; caso contrário, serviço gerenciado com padrões portáveis. Não operar duas plataformas sem justificativa de qualidade.

**Testes:** ordenação por chave, retenção, replay, DLQ, idempotência, schema compatibility, DR, observabilidade e custo.

---

## SBB para dados operacionais

| Necessidade | Categoria recomendada | Observação |
|---|---|---|
| Ledger | banco relacional/ledger especializado ACID | invariantes e auditoria |
| Conta/Produto | relacional por contexto | consistência e consulta estruturada |
| Idempotência/cache | key-value/cache | TTL e durabilidade conforme caso |
| Busca/extrato projetado | search/read model | não é fonte monetária |
| Objetos/documentos | object storage | criptografia, retenção e malware scan |
| Analytics | lakehouse/warehouse | consumo por data products |

A tecnologia é escolhida pelo padrão de uso, não por uniformidade absoluta. Database per context permanece obrigatório no alvo.

---

## SBB para runtime

### C1 — Kubernetes/containers

Adequado a portabilidade e workloads diversos; exige plataforma e SRE maduros.

### C2 — Serverless/PaaS

Reduz operação e acelera entrega; avaliar limites, latência, custo e lock-in.

### C3 — VMs/plataforma vigente

Pode ser mantida na transição se cumprir automação, segurança e SLO.

**Preferência simulada:** paved road corporativo já maduro; containers para serviços contínuos e serverless/PaaS para casos adequados. Não migrar runtime apenas por tendência.

---

## SBB para observabilidade e segurança

### Observabilidade

- suíte integrada gerenciada;
- stack corporativa existente;
- componentes open source operados internamente.

Requisito comum: OpenTelemetry ou padrão neutro, correlação ponta a ponta, retenção, mascaramento e SLOs.

### Segurança

- CIAM/IAM corporativo;
- KMS/HSM gerenciado ou dedicado;
- SIEM/SOAR corporativo;
- policy engine e secrets manager;
- scanners SAST/DAST/SCA/IaC e assinatura de artefatos.

Preferir reuso de capacidades corporativas aderentes; substituir somente por gap comprovado.

---

## Matriz ABB → alternativas SBB

| ABB | SBB A | SBB B | SBB C | Direção inicial |
|---|---|---|---|---|
| Conta/Ledger | SaaS componível | produto self-hosted | build | PoC A/B |
| Pix | BaaS | direto | adaptador multi | BaaS, multi-ready |
| Compliance | suíte única | orquestração multiprovedor | build | multiprovedor |
| API Management | existente | gerenciado | self-hosted | avaliar existente |
| Eventos | streaming | broker | gerenciado | padrão corporativo aderente |
| Runtime | containers | PaaS/serverless | VM | paved roads híbridos |
| Analytics | lakehouse | warehouse | plataforma vigente | reutilizar aderente |
| Cashback futuro | produto SaaS | engine extensível | build | decisão em novo ciclo |

---

## Scorecard de seleção

| Critério | Peso indicativo |
|---|---:|
| aderência funcional | 15% |
| arquitetura/APIs/eventos | 15% |
| segurança e regulação | 15% |
| operação, SLO e DR | 15% |
| dados e portabilidade | 10% |
| TCO de cinco anos | 15% |
| time-to-market | 10% |
| estratégia/saída | 5% |

### Desqualificadores

- impossibilidade de exportar dados completos;
- ausência de idempotência/auditoria em fluxos financeiros;
- segurança ou regulação não atendida;
- APIs incompletas que exijam operação manual crítica;
- DR e capacidade não demonstrados;
- contrato sem estratégia de saída aceitável.

## PoC comparativa

1. configurar produto e abrir conta;
2. executar Pix com sucesso;
3. simular timeout e resposta desconhecida;
4. repetir requisição e comprovar idempotência;
5. estornar/devolver e reconciliar;
6. processar pico e observar degradação;
7. recuperar ambiente e dados;
8. exportar e reconstituir histórico;
9. alterar regra sem customização de núcleo;
10. medir esforço, latência, custo e qualidade operacional.

## Decisão e governança

A seleção final deve gerar ADR, parecer de Segurança/Risco/Jurídico, TCO, mapa de dependências, Architecture Contract, plano de implantação e exit plan testável. O fornecedor selecionado implementa ABBs; não redefine unilateralmente capacidades, ownership ou arquitetura de negócio.
