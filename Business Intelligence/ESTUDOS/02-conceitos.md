# Business Intelligence — Conceitos (ordem das aulas)

Fontes: slides "bi-aula-01" (Fundamentos), textos "bi-1-introdução" e "bi-2-relatórios", Estudo de Caso 1, Atividade de Fixação 1, dataset `d_produto.sql`.

---
## PARTE 1 — Fundamentação (slides aula 01)

### Business Intelligence (BI)
- **Definição:** conceito que engloba ações práticas que **agreguem inteligência aos processos empresariais**.
- **Luhn (IBM):** citou o termo pela 1ª vez em artigo nos **anos 1950**.
- **Dresner:** definiu nos **anos 1990** (o texto de estudo diz **1989**, Gartner) como "conjunto de conceitos e métodos para melhorar a tomada de decisões empresariais através do uso de **sistemas baseados em fatos**".
- **Pegadinha:** **Luhn** = primeiro a usar o termo. **Dresner** = popularizou/definiu o conceito moderno.

### Business Analytics (BA)
- **Definição:** leitura dos dados **em seu contexto** e uso de ferramentas para interpretá-los.
- **Componente mais importante:** **os dados**.
- **Pegadinha:** BI tradicional é **descritivo** ("o que aconteceu? por que?"). Analytics/IA avançam para **prever e recomendar**.

### Dado
- **Definição (Laudon):** fluxos de **fatos brutos** que representam eventos, **antes de serem organizados** para as pessoas entenderem.
- **Exemplo da aula:** "34" sozinho = dado. "Destinatário: Rua Bom Jesus, **34**, Centro, Pouso Alegre-MG" = informação (tem contexto).
- **Pegadinha:** dado sem **contexto** não serve para decisão.

### Pipeline do BI (diagrama da aula)
```
Source 1 ┐
Source 2 ├─Extract (raw data)→ [Staging area: Transform] ─Load (prepared data)→ [Data Warehouse] ─Analyze→ 📊
Source 3 ┘
```
- **E**xtract = tirar das fontes · **T**ransform = limpar/padronizar (na staging area) · **L**oad = carregar no DW.
- **Pegadinha:** a **transformação** acontece na **staging area**, antes do DW.

### Técnicas de preparação (escada)
**Requisitos → Dados disponíveis → Medidas → Dimensões → Visuais**
- **Medida** = número que se soma/calcula (valor total, quantidade). **Dimensão** = como se "corta" a análise (produto, data, cliente). (complemento na explicação)
- **Pegadinha:** a escolha do visual é o **último** passo, não o primeiro.

### Camada de visualização — Relatório × Dashboard (Eckerson)
- **Dashboard:** visão **resumida** do desempenho; monitoramento rápido; identifica **exceções**.
- **Relatório:** análise **detalhada** e **investigação**.

### Roteirizando (3 perguntas)
| Pergunta | Relatório | Dashboard |
|---|---|---|
| Qual informação? | detalhe de transações, **auditoria**, investigação de causas | indicadores de desempenho, tendências, evolução no tempo, comparação |
| Para quem? | Coordenadores, analistas, operadores (análise investigativa) | Diretoria, executivos, gerentes (monitorar metas) |
| Qual decisão? | **Operacional** → relatório analítico | **Estratégica** → dashboard agregado · **Tática** → dashboard com **drill-down** |

### Aspectos importantes na escolha
Nível de **granularidade** · **carga cognitiva** do usuário · **tempo** para interpretar · **frequência** de uso · necessidade de **exploração**.

### Comparativo (tabela do slide) ⭐
| Critério | Relatório Analítico | Dashboard Agregado |
|---|---|---|
| Objetivo | Investigar detalhes | Monitorar desempenho |
| Nível de detalhe | Alto | Baixo a médio |
| Volume de dados | Grande | Resumido |
| Público | Analistas e operação | Gestores e executivos |
| Tempo de leitura | Longo | Curto |
| Foco | Precisão e rastreabilidade | Tendências, KPIs e exceções |
| Suporte à decisão | Operacional | Tática e estratégica |

### Fluxo de Decisão (5 passos) ⭐
1. **Objetivo de negócio** — Qual informação desejo produzir?
2. **Público-alvo** — Para quem será produzida?
3. **Tipo de decisão** — Estratégica, tática ou operacional?
4. **Nível de agregação** — Dados resumidos ou detalhados?
5. **Escolha da visualização** — Qual formato atende melhor?

### Referências e para que servem (slide)
| Autor | Aplicação |
|---|---|
| Kimball & Ross | pipeline de BI, modelagem dimensional, preparação de dados |
| Eckerson | relatório × dashboard, monitoramento de desempenho |
| Few | design da camada de visualização, escolha de indicadores e gráficos |
| Tufte | boas práticas visuais, **redução de ruído** |
| Davenport & Harris | BA, decisão baseada em dados, **vantagem competitiva** |

---
## PARTE 2 — Texto "BI nas Organizações Modernas"

### BI (Turban, Sharda e Delen)
- **Definição:** conjunto de **arquiteturas, ferramentas, bancos de dados, aplicações e metodologias** que transformam dados → informação → conhecimento → ações.
- **Pegadinha:** BI **não é** a ferramenta (Power BI, Tableau, Qlik). A ferramenta é só a **camada de apresentação**.

### Cadeia de valor dos dados
**Dados > Informações > Conhecimento > Decisões > Ações > Resultados** (Data-Driven Decision Making).

### Evolução: OLTP → Data Warehouse
- **OLTP:** sistemas de transação (nota fiscal, estoque, folha). Rápidos para incluir/alterar/excluir, **ruins para análise**.
- **Data Warehouse:** dados **históricos** de múltiplas fontes, organizados para consulta analítica.
- **DW segundo Inmon:** **orientado por assunto · integrado · variante no tempo · não volátil**.
- **Kimball:** abordagem **incremental** com **Data Marts** integrados por **dimensões conformadas**.
- Depois vieram: OLAP, Data Mining, dashboards executivos, BA, Self-Service BI, IA.
- **Pegadinha:** "não volátil" = dado no DW **não é alterado/apagado** no dia a dia (complemento na explicação).

### Níveis da organização
| Nível | Exemplos de apoio do BI |
|---|---|
| Operacional | produção, vendas, estoque, chamados, produtividade |
| Tático | desempenho, metas, orçamento, indicadores de departamento |
| Estratégico | expansão, investimentos, posicionamento, planejamento, governança |

### Benefícios
Integração das informações (ERP, CRM, planilhas) · melhoria da qualidade (ETL) · agilidade · menos tempo de análise · apoio à governança · **cultura orientada por dados**.

### Outros pontos
- **Self-Service BI:** o próprio gestor monta dashboards sem depender da TI.
- **Risco:** painéis bonitos com dados ruins. Few: bom dashboard **comunica rápido o relevante**, não tem mais gráficos.
- **Kimball:** "qualidade das decisões depende da **qualidade dos dados**".
- **Transformação digital:** volume, velocidade, variedade → Big Data, Data Lake, IA.
- **Exemplos:** Amazon (recomendação, estoque), Netflix (recomendação), Walmart (demanda), Einstein (indicadores hospitalares), Nubank, Magalu.
- **Sucesso do BI depende de:** qualidade dos dados, arquitetura, integração, modelagem dimensional, KPIs, visualização, cultura data-driven.

---
## PARTE 3 — Texto "Relatórios" (camada de visualização)

### Camada de visualização
- **Definição:** ponto de contato entre o sistema analítico e o **usuário final**.
- **Deve:** apresentar dados **contextualizados** (tempo, produto, cliente) · permitir **comparação** · garantir **confiabilidade** (fiel ao DW).
- É o elo entre a **técnica** (ETL, modelagem) e o **estratégico** (decisão).

### Os 4 autores ⭐
| Autor | Abordagem | Relatório deve... | Lema |
|---|---|---|---|
| **Inmon** | **Top-down**, DW corporativo, **fonte única da verdade** | ser padronizado e consistente; apoiar decisões táticas/estratégicas; via OLAP | preservar a **integridade** |
| **Kimball** | **Bottom-up**, Data Marts **dimensionais** | usar **fato e dimensão**; ser entendido sem suporte técnico; permitir **self-service** | pensar no **usuário** |
| **Davenport** | **Gerencial**, cultura analítica | ter **propósito** (perguntas de negócio); usar **storytelling** | promover **cultura analítica** |
| **Few** | **Design** e comunicação visual | evitar sobrecarga; hierarquia visual; gráfico certo; consistência | **comunicar com clareza** |
- **Pegadinha:** **Inmon = top-down**, **Kimball = bottom-up**. Não inverta!
- **Few:** série temporal (linha) → **tendência**; colunas → **comparação**.

### 7 boas práticas de relatórios
1. Conheça o **público-alvo**
2. Comece pelo **problema de negócio**
3. Garanta **integridade** dos dados
4. Use **visualizações adequadas** (simples > elaborado)
5. Facilite **navegação e drill-down**
6. **Documente** métricas e indicadores
7. **Valide** com o usuário final

### Pentaho Report Designer (PRD)
- Ferramenta **open source** de relatórios da suíte Pentaho.
- **Fontes:** bancos relacionais (**JDBC**), cubos OLAP (**Mondrian**), CSV/XML/JSON.
- **Recursos:** layouts parametrizados, gráficos, tabelas, grupos, sub-relatórios.
- **Exporta:** PDF, Excel, HTML, CSV.

---
## PARTE 4 — Modelo dimensional (Estudo de Caso 1 + dataset)
- **Fato (f_):** tabela com os **números** (valor total) e as **chaves** das dimensões. Ex.: `f_vendas`, `f_reservas`, `f_consultas`.
- **Dimensão (d_):** tabela descritiva. Ex.: `d_produto` (produto, categoria), `d_data` (data, mês, ano), `d_cliente`, `d_medico`.
- **Dataset `d_produto`:** 50 produtos de supermercado com `id_produto, nome_produto, categoria_produto, vlr_uni, qtd_estoque`.
- **Pegadinha:** o **valor** fica no **fato**; o **nome/categoria** ficam na **dimensão**.

> ⚠️ **Observações:** (1) O Estudo de Caso 1 diz "resultado apresentado em 06/11", mas a própria folha e a Agenda marcam apresentação em **15/09** — provavelmente erro de digitação. (2) Documentos citam "Período 8"/"4º ano"; confira se o conteúdo é o mesmo da sua turma. (3) Pastas `04-paineis-dashboard` e `07-projetos` citadas no README **não existem** na sua cópia.
