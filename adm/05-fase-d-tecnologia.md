# Fase D — Arquitetura de Tecnologia

## Objetivo

Definir a plataforma tecnológica capaz de operar jornadas financeiras com segurança, resiliência, escala, observabilidade e portabilidade.

## Baseline simulado

Ambientes, pipelines, observabilidade e controles variam entre os silos. A infraestrutura vigente pode ser reaproveitada quando cumprir os padrões alvo; não se pressupõe migração de cloud ou troca de runtime sem fit-gap.

## Arquitetura tecnológica alvo

| Domínio tecnológico | ABB requerido | Resultado |
|---|---|---|
| Edge | WAF, API management, DDoS, rate limit | exposição segura |
| Identidade | CIAM/IAM, MFA, autorização, secrets | zero trust e segregação |
| Runtime | containers e/ou serverless gerenciados | isolamento e elasticidade |
| Eventos | broker/stream, schema registry, DLQ | desacoplamento confiável |
| Dados | bancos por contexto, cache, lakehouse | persistência adequada ao uso |
| Segurança | KMS/HSM, SIEM, policy as code, scanning | proteção e evidência |
| Entrega | CI/CD, IaC, artifact registry | mudança reproduzível |
| Operação | logs, métricas, traces, alertas, SRE | detecção e recuperação |
| Continuidade | multi-AZ, backup, DR, chaos tests | resiliência comprovada |
| Developer Platform | templates e paved roads | velocidade com conformidade |

## NFRs a quantificar

- SLO por jornada, não apenas por componente;
- latência percentil 95/99 e throughput de pico;
- RTO/RPO por classe de serviço;
- consistência e durabilidade do ledger;
- retenção, backup e restauração testada;
- isolamento, criptografia e rotação de chaves;
- capacidade de auditoria e não repúdio;
- limites de custo e eficiência por transação.

Os números serão derivados de volume, criticidade, regulação e apetite de risco.

## Cenários de qualidade simulados

| Estímulo | Resposta esperada |
|---|---|
| duplicação de mensagem | inbox/idempotência impede efeito duplicado |
| timeout Pix | estado pendente, consulta e reconciliação |
| indisponibilidade de antifraude | política explícita fail-open/fail-closed por risco |
| falha de zona | recuperação automática dentro do SLO |
| perda de credencial | revogação, rotação e auditoria |
| pico de pagamentos | elasticidade, backpressure e proteção do ledger |
| deploy defeituoso | canary/blue-green e rollback automático |

## Standards propostos

- infraestrutura e políticas como código;
- imagens assinadas, SBOM e supply-chain security;
- mTLS/service identity quando aplicável;
- OpenTelemetry ou padrão equivalente;
- secrets fora de código/configuração aberta;
- ambientes segregados e dados de teste protegidos;
- patching e vulnerability management com SLA;
- FinOps por produto/capacidade.

## Entregáveis simulados

- technology standards catalog;
- environments and locations diagram;
- platform decomposition diagram;
- matriz aplicação × tecnologia;
- NFR catalog e quality scenarios;
- plano de continuidade e segurança;
- gap analysis tecnológico.

## Gate de saída

- NFRs críticos acordados;
- padrões e exceções definidos;
- capacidade/DR/security PoCs concluídas para riscos altos;
- custos estimados por cenário;
- plataforma atual classificada em manter, evoluir ou substituir.
