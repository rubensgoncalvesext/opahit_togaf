# Pacote de Simulação TOGAF ADM

Este diretório detalha a aplicação do TOGAF ADM ao programa de Conta de Pagamentos e modernização arquitetural do banco.

## Navegação

| Ordem | Etapa | Arquivo | Decisão principal |
|---:|---|---|---|
| 0 | Preliminar | [00-preliminar.md](00-preliminar.md) | capacidade e governança arquitetural |
| 1 | Fase A — Visão | [01-fase-a-visao.md](01-fase-a-visao.md) | produto, escopo e autorização |
| 2 | Fase B — Negócio | [02-fase-b-negocio.md](02-fase-b-negocio.md) | capacidades e modelo operacional |
| 3 | Fase C — Dados | [03-fase-c-dados.md](03-fase-c-dados.md) | ownership e arquitetura de dados |
| 4 | Fase C — Aplicações | [04-fase-c-aplicacoes.md](04-fase-c-aplicacoes.md) | bounded contexts, APIs e eventos |
| 5 | Fase D — Tecnologia | [05-fase-d-tecnologia.md](05-fase-d-tecnologia.md) | plataforma e requisitos técnicos |
| 6 | Fase E — Oportunidades e Soluções | [06-fase-e-oportunidades-solucoes.md](06-fase-e-oportunidades-solucoes.md) | work packages e buy/build/compose |
| 7 | Fase F — Migração | [07-fase-f-migracao.md](07-fase-f-migracao.md) | roadmap e arquiteturas de transição |
| 8 | Fase G — Governança | [08-fase-g-governanca.md](08-fase-g-governanca.md) | contratos e conformidade |
| 9 | Fase H — Mudança | [09-fase-h-mudanca.md](09-fase-h-mudanca.md) | monitoramento e novos ciclos ADM |
| Contínua | Gestão de Requisitos | [10-gestao-requisitos.md](10-gestao-requisitos.md) | rastreabilidade e controle de mudanças |
| Alternativas | ABB | [11-alternativas-abb.md](11-alternativas-abb.md) | opções lógicas de arquitetura |
| Alternativas | SBB | [12-alternativas-sbb.md](12-alternativas-sbb.md) | opções de implementação e sourcing |

## Convenções da simulação

- **Confirmado:** informação fornecida no caso.
- **Hipótese:** premissa plausível ainda não validada.
- **Decisão proposta:** recomendação sujeita ao gate indicado.
- **Evidência requerida:** dado ou aprovação necessário para converter hipótese em decisão.

O ADM é iterativo. As fases não constituem um waterfall: descobertas de Dados, Aplicações ou Tecnologia podem exigir revisão da Visão, dos requisitos e do business case.

## Governança mínima

- patrocinadores: Executivo de Negócio e CIO/CTO;
- accountable: líder do programa de Conta de Pagamentos;
- Architecture Board: Arquitetura Corporativa, Segurança, Dados, Risco, Operações e domínios;
- fórum de valor: Produto, Finanças, Estratégia e Tecnologia;
- repositório: princípios, requisitos, modelos, building blocks, ADRs, contratos e evidências de conformidade.

## Referências internas

- [Visão de Arquitetura](../visao-arquitetura-banco.md)
- [Resumo Executivo](../resumo_executivo.md)
