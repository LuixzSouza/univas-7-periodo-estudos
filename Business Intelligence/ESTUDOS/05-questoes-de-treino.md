# Business Intelligence — Questões de treino

---
**1.** Quem usou o termo Business Intelligence pela primeira vez e quem o definiu como "conjunto de conceitos e métodos para melhorar a tomada de decisões empresariais através do uso de sistemas baseados em fatos"?

**2.** Diferencie **dado** de **informação** usando o exemplo do número "34" visto em aula.

**3.** Explique as etapas do Pipeline do BI.

**4.** Coloque em ordem as técnicas de preparação: Visuais, Medidas, Requisitos, Dimensões, Dados disponíveis.

**5.** Complete a tabela:
| Critério | Relatório Analítico | Dashboard Agregado |
|---|---|---|
| Objetivo | | |
| Público | | |
| Tempo de leitura | | |
| Suporte à decisão | | |

**6.** Qual formato é indicado para cada tipo de decisão: estratégica, tática e operacional?

**7.** Associe o autor à ideia:
(A) Inmon (B) Kimball (C) Davenport (D) Few
( ) Relatórios devem incorporar storytelling e responder perguntas-chave do negócio.
( ) Abordagem bottom-up com Data Marts dimensionais e foco no usuário.
( ) Evitar sobrecarga visual e usar o gráfico adequado a cada análise.
( ) Data Warehouse como fonte única da verdade, abordagem top-down.

**8.** Cite as 4 características de um Data Warehouse segundo Inmon.

**9.** (V ou F)
a) Power BI e Tableau, sozinhos, são o Business Intelligence da empresa.
b) Sistemas OLTP são ideais para consultas analíticas complexas.
c) A transformação dos dados ocorre na staging area.
d) Dashboards servem para identificar exceções rapidamente.

**10.** Caso: Um hospital quer (a) uma lista de todos os atendimentos de ontem, com paciente, médico, horário e procedimento, para o faturamento conferir as contas; e (b) uma visão mensal da taxa de ocupação e do tempo médio de espera por unidade para a diretoria. Aplique o Fluxo de Decisão aos dois pedidos.

**11.** No modelo `f_vendas` + `d_produto` + `d_data`, onde fica o **valor total** e onde fica a **categoria**? Por quê?

**12.** Cite 4 das 7 boas práticas para relatórios analíticos.

**13.** Cite 3 "aspectos importantes" a considerar na escolha da visualização.

**14.** Escreva uma consulta SQL que mostre, por categoria, a quantidade de produtos e o preço médio da tabela `d_produto`, do maior preço médio para o menor.

---
# Gabarito

**1.** **Hans Peter Luhn** (IBM, anos 1950) usou primeiro. **Howard Dresner** (anos 1990/1989, Gartner) deu essa definição.

**2.** **Dado** = fato bruto sem organização/contexto ("34"). **Informação** = dado com contexto ("Rua Bom Jesus, 34, Centro, Pouso Alegre-MG"). Contexto dá significado.

**3.** Fontes → **Extract** (dados brutos) → **Staging area** (Transform: limpa/padroniza) → **Load** (dados preparados) → **Data Warehouse** → **Analyze** (visualização).

**4.** Requisitos → Dados disponíveis → Medidas → Dimensões → Visuais.

**5.** Objetivo: investigar detalhes | monitorar desempenho. Público: analistas e operação | gestores e executivos. Tempo: longo | curto. Decisão: operacional | tática e estratégica.

**6.** Estratégica → **dashboard agregado**; Tática → **dashboard com drill-down**; Operacional → **relatório analítico**.

**7.** (C), (B), (D), (A).

**8.** Orientado por assunto; integrado; variante no tempo; não volátil.

**9.** a) **F** — ferramentas são só a camada de apresentação. b) **F** — OLTP é para transações; consultas pesadas prejudicam a operação. c) **V**. d) **V** (Eckerson).

**10.**
| | (a) Lista de atendimentos | (b) Visão mensal |
|---|---|---|
| Informação | cada atendimento detalhado | ocupação e tempo médio de espera |
| Público | faturamento (operacional) | diretoria |
| Decisão | operacional (conferir contas) | estratégica/tática |
| Agregação | detalhada | resumida por mês/unidade |
| Formato | **relatório analítico** (tabela) | **dashboard agregado** (KPIs, linha mensal, colunas por unidade; drill-down opcional) |

**11.** **Valor total** → **fato** (`f_vendas`), pois é a medida numérica. **Categoria** → **dimensão** (`d_produto`), pois descreve o produto e serve para filtrar/agrupar (Kimball).

**12.** Conhecer o público; começar pelo problema de negócio; garantir integridade; visualização adequada; drill-down; documentar métricas; validar com usuário (quaisquer 4).

**13.** Granularidade; carga cognitiva; tempo para interpretação; frequência de uso; necessidade de exploração (quaisquer 3).

**14.**
```sql
SELECT categoria_produto,
       COUNT(*)      AS qtd_produtos,
       AVG(vlr_uni)  AS preco_medio
FROM d_produto
GROUP BY categoria_produto
ORDER BY preco_medio DESC;
```
