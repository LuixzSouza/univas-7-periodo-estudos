# Governança de TI — Fórmulas, diagramas e passo a passo

## Fórmulas / modelos
| O quê | Fórmula |
|---|---|
| Valor realizado (ITIL 4) | **Utilidade + Garantia − Custos & Riscos** |
| Cocriação de valor | **Provedor + Consumidor (sponsor, customer, user)** |
| Governança (ciclo) | **Avaliar → Direcionar → Monitorar** |

## Diagramas
```
SVS:  Demanda ──► [ Princípios | Governança | CADEIA DE VALOR | Práticas | Melhoria contínua ] ──► Valor
                         (tudo apoiado nas 4 dimensões + fatores PESTLE)

CADEIA (6):  Planejar · Melhorar · Engajar · Desenhar e Transicionar · Obter/Construir · Entregar e Suportar

LINHA DO TEMPO
ITIL : 1989 v1 ─ 2001 v2 ─ 2007/11 v3 ─ 2019 ITIL 4 ─ 2026 ITIL 5
COBIT: 1996 v1 ─ 1998/2000 v2/v3 ─ 2005/07 v4 ─ 2012 COBIT 5 ─ 2019 COBIT 2019
DONO ITIL: CCTA/OGC (1989) → Axelos (2013) → PeopleCert (2021)
```

---
## TIPO 1 — Gestão, Governança ou ambos? (Semana 1) ⭐
**Passo a passo:**
1. A **execução** (chamados, processos, mudanças, projeto) funciona? Se não → problema de **gestão**.
2. Existe **direção**: prioridades, aprovação central, indicadores de valor, alinhamento com o negócio, prestação de contas? Se não → problema de **governança**.
3. Os dois faltam → **ambos**. Justifique com **alinhamento de valor**.

**Exemplos resolvidos (gabarito do professor):**
| Caso | Diagnóstico | Por quê |
|---|---|---|
| TechFar: TI técnica ótima, mas diretoria não sabe custo por área, projeto parado 8 meses, sem indicadores | **Governança** | operação ok; falta direcionamento, priorização e **accountability** |
| Vale Alto: comitê existe e aprova orçamento, mas técnicos sem processo, mudança direto em produção | **Gestão** | governança formal existe; falha na **execução** |
| EduPlus: cada coordenador contrata ferramenta sem aprovação; equipe apagando incêndio | **Ambos** | sem controle central **e** sem capacidade de execução |
| Ferro Sul: ERP entregue no prazo e sem bugs, mas não conversa com vendas | **Governança** | faltou **alinhamento TI–negócio** antes do projeto |

---
## TIPO 2 — Qual versão do ITIL? (Semana 2) ⭐
| Pista no cenário | Versão |
|---|---|
| manuais separados por processo, padronização e controle | **ITIL v2** |
| serviços ao negócio, estratégia → desenho → transição → operação (ciclo de vida) | **ITIL v3** |
| práticas ágeis, adaptar o framework, criação conjunta de valor | **ITIL 4** |
| nuvem, automação, **IA**, uso responsável de novas tecnologias | **ITIL 5** |
| "como garantir que a TI gere valor?", pessoas + processos + tecnologia + fornecedores | **ITIL 4** (sistema de valor, visão sistêmica) |

---
## TIPO 3 — Qual princípio orientador? (Semana 4) ⭐
**Passo a passo:** 1) ache o erro do cenário; 2) escolha o princípio que o evita; 3) diga a ação concreta; 4) diga o que acontece se ignorar.

| Cenário | Princípio | Ação | Se ignorar |
|---|---|---|---|
| Reescrever help desk "feio" do zero, parando 2 semanas | **Começar de onde você está** | reaproveitar o que funciona e evoluir aos poucos | atendimento parado, desperdício |
| Processo não documentado, cada um faz de um jeito | **Colaborar e promover visibilidade** | mapear com a equipe como **realmente** funciona | "consertar" uma versão irreal |
| Ferramenta complexa para problema que planilha resolve | **Manter simples e prático** | avaliar se precisa de tanto | custo e curva de aprendizado altos |
| Projeto de 8 meses sem checagem | **Progredir iterativamente com feedback** | entregas menores com pontos de ajuste | erro descoberto só no fim |
| Infra otimiza isolada, sem falar com desenvolvimento | **Pensar e trabalhar de forma holística** | envolver o outro departamento | melhoria local vira piora geral |
| Automatizar aprovação com etapas redundantes | **Otimizar e automatizar** | **primeiro otimizar, depois automatizar** | ineficiência "engessada" |

---
## TIPO 4 — Montar o fluxo de valor (Semana 5) ⭐
**Passo a passo:**
1. A demanda **chega** por onde? Usuário/cliente → começa em **Engajar**. Decisão estratégica → começa em **Planejar**.
2. Precisa **projetar** algo novo? → **Desenhar e Transicionar**.
3. Precisa **adquirir/configurar** componentes? → **Obter/Construir**.
4. Entrega e suporte ao usuário → **Entregar e Suportar**.
5. Há investigação/ajuste/lições? → **Melhorar**.
6. Pule o que não é necessário. Ordem e tamanho **variam**.

**Exemplos resolvidos (gabarito do professor):**
| Demanda | Fluxo |
|---|---|
| Redefinir senha no portal | Engajar → Entregar e Suportar (fluxo mais curto) |
| VPN para 200 funcionários | Planejar → Desenhar e Transicionar → Obter/Construir → Entregar e Suportar → Melhorar |
| Lentidão recorrente sem causa | Engajar → Melhorar (investigar) → [Desenhar e Transicionar → Obter/Construir, se precisar mudar] → Entregar e Suportar |
| Nova ferramenta de projetos para a empresa | Planejar → Engajar → Obter/Construir → Desenhar e Transicionar → Entregar e Suportar → Melhorar |
| Notebook para recém-contratado | Engajar → Obter/Construir → Entregar e Suportar (já existe pacote padrão) |
| Slide: novo app mobile | Planejar → Engajar → Desenhar/Transicionar → Obter/Construir → Desenhar/Transicionar (testes) → Entregar e Suportar |

---
## TIPO 5 — Incidente, Solicitação ou Problema? (Semana 6) ⭐
**Passo a passo:**
1. Algo **quebrou/degradou** sem planejamento? → **Incidente** (restaurar rápido).
2. É um **pedido padrão** previsto no catálogo? → **Solicitação**.
3. É dúvida/status? → **Service Desk**.
4. A falha **se repete** / precisa de causa raiz? → **Problema**.
5. Escalonar se: muitos afetados, serviço crítico, precisa de especialista (N2/infra).

**Exemplo resolvido — Universidade Alfa (resposta minha, a atividade não tem gabarito):**
| Caso | Classificação | Prática | 1ª ação | Comunicação | Escalonar? |
|---|---|---|---|---|---|
| 1 Portal do Aluno não abre, vários alunos | **Incidente** (grave) | Ger. de Incidentes | registrar, priorizar alto, aplicar workaround/reiniciar | aviso geral de indisponibilidade e previsão | **Sim** — muitos afetados, período de matrícula, envolve infra |
| 2 Novo professor precisa de e-mail e acesso | **Solicitação** | Ger. de Solicitações | executar procedimento padrão de criação de conta | informar prazo e credenciais | Não — rotina predefinida |
| 3 VPN não conecta, folha de pagamento urgente | **Incidente** | Ger. de Incidentes | testar credenciais/cliente VPN, workaround | retorno rápido ao usuário | Sim se for falha no servidor VPN (N2/infra) |
| 4 Esqueceu a senha | **Solicitação** | Ger. de Solicitações (autoatendimento) | orientar reset pelo portal | passo a passo | Não |
| 5 Lento toda segunda até meio-dia | **Incidente recorrente → Problema** | Incidentes + **Ger. de Problemas** | registrar e contornar; abrir problema | informar investigação | Sim — análise de causa raiz |

**Incidente × Problema (servidor cai toda segunda 9h, 3 semanas):**
1. A equipe **restaurou** o serviço (reiniciou). 2. O **incidente** foi resolvido. 3. A **causa raiz não** foi eliminada. 4. Acionar **Gerenciamento de Problemas**.

---
## TIPO 6 — Dissertativa COBIT × ITIL (Trabalho 01)
**Roteiro:**
1. **Origem:** ITIL = CCTA 1989, padronizar serviços de TI do governo; COBIT = ISACA 1996, auditar/controlar TI para conformidade.
2. **Mudanças de filosofia:** ITIL v2 (processos isolados) → v3 (ciclo de vida) → 4 (sistema de valor); COBIT auditoria → gestão → governança → 2019 (fatores de design).
3. **Convergência:** **COBIT 5 (2012)** coordena-se com ITIL v3/ISO → guarda-chuva.
4. **Uso conjunto:** COBIT = governança (o que, top-down, GPS); ITIL = gestão (como, motor). Empresa complexa precisa de **ambos**.
