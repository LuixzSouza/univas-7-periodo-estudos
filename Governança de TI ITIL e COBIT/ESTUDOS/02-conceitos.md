# Governança de TI: ITIL e COBIT — Conceitos (ordem das aulas)

---
## SEMANA 1 — Governança de TI: por que agregar valor importa

### TI sem bússola (4 sintomas)
1. Chamados se perdem no vácuo · 2. Mudanças sem controle (sistema cai na sexta) · 3. Equipe apaga incêndio 24/7 (reativa) · 4. Negócio vê a TI como **centro de custo caro**.
- **Frase-chave:** "O problema não é falta de gestão. **O problema é a falta de direcionamento.**"

### Gestão × Governança ⭐
| | **Gestão (Management)** | **Governança (Governance)** |
|---|---|---|
| Foco | **Operar e executar** | **Direcionar, monitorar e avaliar** |
| Objetivo | fornecimento eficaz de serviços e produtos de TI | garantir que a TI **sustente e expanda a estratégia** do negócio |
| Responsáveis | gerentes de TI, líderes técnicos | **diretoria (board), executivos, CIO** |
| Pergunta-chave | "Estamos fazendo as coisas **do jeito certo**?" | "Estamos fazendo **as coisas certas**?" |

### Fluxo de valor da TI para o negócio
**Governança corporativa de TI** (estruturas, processos, relações) —habilita→ **Alinhamento Negócio/TI** (estratégia de TI fundida à da empresa) —habilita→ **Valor de negócio** (receita, eficiência, inovação, mitigação de risco).

### Definições base
- **COBIT** (Control Objectives for Information and Related Technologies): framework da **ISACA** para **governança e gestão** de TI empresarial.
- **ITIL** (Information Technology Infrastructure Library): biblioteca de melhores práticas de **Gestão de Serviços de TI (ITSM)**.

### As 3 imprecisões (atividade corrigida) ⭐
| Afirmação errada | Por que está errada |
|---|---|
| Governança é função **técnica do departamento de TI** | Governança é responsabilidade da **diretoria/executivos**; foca em direção e valor, não em chamados |
| Ter **documentação** = maturidade em governança | Documento sem direcionamento, priorização e prestação de contas não é governança |
| Governança é **projeto com fim** (certificação encerra) | Governança é **contínua** (avaliar–direcionar–monitorar sempre) |

---
## SEMANA 2 — ITIL: histórico e evolução

### ITIL
- **Definição:** framework de boas práticas de **ITSM**, foco em **alinhar serviços de TI às necessidades do negócio**, organizado no **ciclo de vida do serviço** (Estratégia, Desenho, Transição, Operação, Melhoria Contínua), para garantir a **entrega de valor**.

### Gênese (1989)
- "**Faroeste digital**": custos exorbitantes, inconsistências, falhas entre ministérios.
- Criado pela **CCTA** (Central Computer and Telecommunications Agency), governo britânico, para organizar a **TI pública do Reino Unido** e criar **linguagem comum** baseada no que funcionava.
- Virou de "redução de custos do governo" → "**habilitador de valor competitivo** no setor privado".

### Evolução das versões ⭐
| Ano | Versão | Marca |
|---|---|---|
| 1989 | **v1** | padronização governamental (~30–40 livros) |
| 2001 | **v2** | Suporte e Entrega de Serviços; **processos isolados** (descontinuada 2010) |
| 2007/2011 | **v3** | **Ciclo de vida do serviço**, 26 processos; TI parceira estratégica |
| 2019 | **ITIL 4** | **Sistema de Valor de Serviço (SVS)**, **34 práticas**, Agile/DevOps |
| 2026 | **ITIL 5** | ciclo de vida do produto e **governança de IA** |

### Propriedade
1989 **CCTA/OGC** (governo) → 2013 **Axelos** (joint venture governo + Capita) → 2021 **PeopleCert** (privado, ativo comercial/educacional).

### Mudanças de paradigma
| De | Para | Gatilho |
|---|---|---|
| dezenas de livros | suporte/entrega (v2) | tornar consumível para o setor privado |
| processos isolados | ciclo de vida (v3) | TI vira parceira estratégica |
| estrutura fixa | sistema de valor flexível (ITIL 4) | DevOps, Agile, alta velocidade |
| um governo | escala global | caos e custo eram universais |
| biblioteca | certificação formal | demanda por profissionais validados |

### Caso Disney Parks & Resorts (ITIL v3)
- Evitou treinamento massivo e superficial; formou **20 "champions"** internos.
- **4 pilares da liderança:** articular a visão · capacidade de absorção · influência e persuasão · **pragmatismo**.
- Lição: sucesso do framework depende de **liderança** e **flexibilidade**.

### 5 processos operacionais ⭐
| Processo | Ideia | Exemplo |
|---|---|---|
| **Incidentes** | **restauração célere** | reiniciar servidor de e-mail; automatizar reset de senha |
| **Problemas** | **erradicar a causa-raiz** | sistema cai toda segunda → falha no backup corrigida |
| **Mudanças** | governança de **riscos** em atualizações | atualizar faturamento com testes e horário de baixo impacto |
| **Capacidade** | dimensionamento **preventivo** | aumentar CPU antes de campanha |
| **Ativos** | ciclo de vida tecnológico | recolher notebook e licenças de desligado |

### Trilha de certificação ITIL 4
**Foundation** (60 min, 40 questões, mínimo 65% = 26) → **Managing Professional** (CDS, DSV, HVIT, DPI) → **Strategic Leader** (DPI, DITS) → **ITIL Master**.

### Caso Oxford (ITIL 4)
Incidentes graves **8 → 2 por ano** usando **princípios** (Colaborar e promover visibilidade + Focar em valor), não regras rígidas. "Resultados antes das regras."

---
## SEMANA 3 — COBIT

### COBIT
- Framework **global da ISACA** para **Governança e Gestão de TI Empresarial (EGIT)**.
- **Propósito:** preencher a lacuna entre **riscos de negócio**, **necessidades de controle** e **questões técnicas**; tecnologia a favor das metas.
- Camadas: **Negócio (metas e riscos)** ← Governança (controles e objetivos) ← Tecnologia.

### Origem (1996)
- "Nasceu para **auditar e controlar**, não para consertar computadores."
- Dor: auditores financeiros e executivos **não sabiam avaliar riscos de TI** ("caixa preta cara e arriscada").
- Solução: **objetivos de controle mensuráveis e auditáveis**, em linguagem de **risco e valor**.

### Evolução ⭐
| Ano | Versão | Foco |
|---|---|---|
| 1996 | v1 | **Auditoria** (apoio à auditoria financeira) |
| 1998/2000 | v2/v3 | **Gestão** (diretrizes de gestão; "TI entra no jogo") |
| 2005/2007 | v4/4.1 | **Governança** de TI explícita |
| 2012 | **COBIT 5** | **integração**: absorve Val IT, Risk IT, ITAF; coordena com **ITIL e ISO** |
| 2019 | **COBIT 2019** | **fatores de design** (governança customizada), conformidade regulatória |

### COBIT × ITIL ⭐
| | COBIT | ITIL |
|---|---|---|
| Origem | **ISACA** (auditores) | **CCTA** (governo britânico) |
| Escopo | **O QUE** controlar e alcançar | **COMO** desenhar, operar e entregar serviços |
| Foco | governança, diretoria, riscos (**top-down**) | gestão, operação (prática) |
| Metáfora | **painel de controle e GPS** | **motor e transmissão** |
- **Complementares, não concorrentes.** Desde o **COBIT 5 (2012)** o COBIT é um **guarda-chuva** que mapeia seus processos contra o ITIL.
- "Se o ITIL entrega o serviço perfeito, o COBIT garante que é o que a organização precisa."

### Caso Banco Nacional de Angola (COBIT 2019)
- 2019, pressão da **SADC** + pandemia (sem consultoria externa) → CIO implementou COBIT 2019 **só com equipe interna**.
- Falha do passado: **bottom-up** (mapear tudo da base; checklist infinito). Sucesso: **top-down sistêmico** (patrocínio da diretoria).
- Execução: 1) **capacitação em massa** (~60 no COBIT Foundation) · 2) **equipes multidisciplinares** · 3) **autonomia pragmática** (Excel) com os **7 componentes**: Processos, Pessoas, Estruturas, Fluxos, Políticas, Cultura, Infraestrutura.
- Resultados: **300+ melhorias** (gap analysis), **17 processos** avaliados, TI deixa de ser só operacional.

### Trilha COBIT
**COBIT 2019 Foundation** (modelo, **40 objetivos** de governança/gestão) → **Design & Implementation** (fatores de design) → extensões (ex.: **NIST**).

---
## SEMANA 4 — ITIL 4: Sistema de Valor de Serviço (SVS)

### SVS ⭐
Transforma **demanda/oportunidade em valor** por **5 componentes**:
| Componente | Papel (metáfora) |
|---|---|
| **Princípios orientadores** | **a bússola** — como decidir |
| **Governança** | direcionamento: **Avaliar → Direcionar → Monitorar** |
| **Cadeia de valor de serviço (SVC)** | **o motor** — núcleo operacional |
| **Práticas (34)** | **a caixa de ferramentas** |
| **Melhoria contínua** | a evolução, em todos os níveis |

### 7 Princípios orientadores ⭐
| # | Princípio | Quando usar (atividade corrigida) |
|---|---|---|
| 1 | **Focar em valor** | tudo deve gerar valor ao cliente |
| 2 | **Começar de onde você está** | não jogar fora o que funciona (reescrever help desk do zero ✗) |
| 3 | **Progredir iterativamente com feedback** | quebrar projeto de 8 meses em entregas menores |
| 4 | **Colaborar e promover visibilidade** | mapear com a equipe como o processo **realmente** funciona |
| 5 | **Pensar e trabalhar de forma holística** | não otimizar um departamento isolado |
| 6 | **Manter simples e prático** | não comprar ferramenta complexa se planilha resolve |
| 7 | **Otimizar e automatizar** | **primeiro otimizar, depois automatizar** |
- **Pegadinha:** automatizar processo ruim = processo ruim mais rápido.

### Princípios × Práticas
| Princípios | Práticas |
|---|---|
| bússola; **como decidir**; universais, flexíveis | ferramenta; **o que fazer**; específicas, estruturadas |
| ex.: Colaborar (o que Oxford **usou**) | ex.: Gestão de Incidentes (onde Oxford **operou**) |

### 6 atividades da cadeia de valor
Planejar · Melhorar · Engajar · Desenhar e Transicionar · Obter/Construir · Entregar e Suportar.

---
## SEMANA 5 — Cadeia de valor, Fluxos de valor, 4 Dimensões

### 4 Dimensões ⭐
| Dimensão | Ideia |
|---|---|
| **Organizações e pessoas** | cultura, competências, estrutura de autoridade |
| **Informação e tecnologia** | conhecimento, informação e ferramentas |
| **Parceiros e fornecedores** | relações externas |
| **Fluxos de valor e processos** | como as partes trabalham integradas |
- Sofrem influência de fatores externos **PESTLE**: Políticos, Econômicos, Sociais, Tecnológicos, Legais, Ambientais.

### Cocriação de valor ⭐
- **Provedor + Consumidor (sponsor, customer, user) = cocriação** (colaboração ativa, não mão única).
- **Utilidade** (adequado ao **propósito**: o que faz) **+ Garantia** (adequado ao **uso**: como performa) **− Custos e Riscos = Valor realizado**.
- **Pegadinha:** utilidade = "o que faz"; garantia = "quão bem/confiável funciona".

### As 6 atividades ⭐
| Atividade | Pergunta | Faz |
|---|---|---|
| **Planejar** | O que queremos alcançar? | visão, situação atual, direção |
| **Engajar** | O que as pessoas precisam? | entender necessidades, relacionamento com stakeholders |
| **Melhorar** | Como fazer melhor? | evolução contínua |
| **Desenhar e Transicionar** | Como colocar em operação com sucesso? | atender custo/qualidade e levar à produção |
| **Obter/Construir** | Como conseguimos os componentes? | obter/criar componentes |
| **Entregar e Suportar** | Como operamos no dia a dia? | operação e suporte nos níveis acordados |
- A cadeia é **caixa de ferramentas flexível, não receita linear**.

### Cadeia × Fluxo de valor ⭐
- **Cadeia:** 6 atividades **universais** (blocos estáticos).
- **Fluxo de valor (value stream):** **combinação específica** delas para um cenário real. A ordem e a quantidade **mudam** conforme a demanda.

### Atividades × Práticas
| Atividades | Práticas |
|---|---|
| **O QUE** fazemos; **6**; espinha dorsal | **COMO** fazemos; **34**; ferramentas que executam as atividades |

### Ecossistema (síntese)
SVS (macroambiente) → Cadeia (6 atividades) → Fluxos (combinações) → Práticas (34), cercados pelas 4 dimensões.

---
## SEMANA 6 — Práticas: Service Desk, Incidentes, Solicitações, Problemas

### Prática
- "**Capacidade organizacional**", mais que processo: conjunto de **pessoas, tecnologias, parceiros e fluxos** para um objetivo.
- **34 práticas:** **14 gerais** (estratégia, portfólio, melhoria contínua, arquitetura, segurança, conhecimento, medição, mudança organizacional, projetos, relacionamento, riscos, finanças, fornecedores, força de trabalho) · **17 de serviço** (service desk, incidentes, solicitações, problemas, disponibilidade, análise de negócios, capacidade, controle de mudança, ativos, eventos, liberação, catálogo, configuração, continuidade, desenho, nível de serviço, validação) · **3 técnicas** (implantação, infraestrutura, desenvolvimento de software).

### As 4 práticas principais ⭐
| Prática | Conceito | Exemplo |
|---|---|---|
| **Service Desk** | canal principal com o usuário; acolhe, classifica, aciona, **mantém informado** | cliente Faruq relata erro no app (Axle Car Hire) |
| **Gerenciamento de Incidentes** | **minimizar impacto restaurando o serviço rápido** (workaround); métrica = **velocidade** | Portal do Aluno cai às 8h na matrícula |
| **Gerenciamento de Solicitações** | pedidos **predefinidos, rotineiros**, que **não são falha** | novo professor precisa de conta e acesso |
| **Gerenciamento de Problemas** | **causa raiz**; evitar recorrência | servidor cai toda segunda às 9h |

### Matriz de diagnóstico ⭐
| Usuário diz... | Natureza | Foco | Prática |
|---|---|---|---|
| "O sistema caiu/parou" | interrupção/degradação **não planejada** | restaurar rápido | **Incidentes** |
| "Preciso de acesso/equipamento" | **pedido padrão** | cumprir procedimento seguro | **Solicitações** |
| "Como faço X? Qual o status?" | dúvida/acompanhamento | comunicação | **Service Desk** |

### Incidente × Problema (iceberg) ⭐
| Incidente (acima da superfície) | Problema (abaixo) |
|---|---|
| apagar o incêndio | descobrir o que causou |
| métrica: **velocidade** | métrica: **investigação da causa raiz** |
| reiniciar, **workaround** | eliminar a vulnerabilidade |
- "**Restaurar o serviço ≠ eliminar a causa.**"
- **3 ideias da prática:** prática é capacidade · interrupção ≠ pedido padrão · restaurar ≠ eliminar causa.

---
> ⚠️ **Observações:** (1) **Dois PDFs de slides** (aula2 "Governança de TI_ ITIL e COBIT.pdf" e aula4) só têm capas em texto — o conteúdo é imagem e foi lido visualmente. (2) A **Atividade da Semana 6** (Universidade Alfa) **não tem correção** na pasta; as respostas no arquivo 03 são minhas, baseadas na matriz da aula. (3) O arquivo `Atividades_Correção.pdf` solto na raiz é a correção da **Semana 5** (fluxo de valor). (4) Semanas 3 (Trabalho 01) e 5 não têm "Atividades" separadas além das listadas. (5) A figura "As 6 atividades" da semana 4 mostra "Melhorar" duas vezes (erro da imagem); as 6 atividades corretas estão acima.
