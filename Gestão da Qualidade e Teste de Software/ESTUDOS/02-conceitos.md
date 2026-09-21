# Gestão da Qualidade e Teste de Software — Conceitos (ordem das aulas)

---
## AULA 0 — Apresentação
- **Ementa:** histórico e conceito de qualidade, métricas, normas, garantia da qualidade, modelos de melhoria de processo, planejamento, padrões, **tipos de testes**, testes de unidade/integração (API)/interface web, ferramentas.
- **Avaliação:** 2 provas (25 cada) + exercícios (10) + seminário (20) + trabalho final (20).
- **Reflexão:** "Software bonito que trava tem qualidade? Feio mas estável?" → qualidade tem **várias dimensões**.

---
## AULA 1 — Introdução à Qualidade de Software

### Qualidade (definições)
- Antecipar e satisfazer necessidades dos usuários · estar em **conformidade com os requisitos**.
- **ISO 9000:** "grau em que um conjunto de características inerentes cumpre os requisitos".
- **NBR ISO 8402:** "totalidade das características que lhe confere capacidade de satisfazer necessidades **explícitas e implícitas**".
- **Pegadinha:** necessidades **implícitas** também contam (o usuário não pede, mas espera — ex.: não travar).

### Histórico ⭐ (ordem)
| Época | Marco |
|---|---|
| Séc. XV–XVII | **Guildas e artesãos**: inspeção manual, retrabalho |
| Início/meados séc. XX | **Controle estatístico** — **Walter Shewhart**, CEP |
| 1950–1970 | **TQM** — **Deming e Juran** no Japão; melhoria contínua |
| Década de 1980 | **ISO 9001** — padronização e certificação |
| 1990 em diante | **Modelos de maturidade** — CMM → CMMI, SPICE, MPS.BR |

### Qualidade de software
- **Definição:** área da Eng. de Software que garante a qualidade do **produto e do processo** por meio de definição e normatização.

### Produto × Processo ⭐
| Produto | Processo |
|---|---|
| características do software **entregue** | **como** o software é desenvolvido |
| correção, usabilidade, desempenho, confiabilidade, segurança | definição de processos, aderência a normas, reuso, padronização, automação |
- **Frase-chave:** "Bons processos aumentam a probabilidade de bons produtos."
- **Pegadinha:** interface bonita sem testes/documentação → **tende a falhar** com o tempo.

### Perspectivas ⭐
| Quem | Qualidade é... |
|---|---|
| Desenvolvedor | código limpo, modular, testável, legível |
| Usuário final | experiência de uso; "funcionar" > "como foi feito" |
| Cliente/Contratante | prazo, orçamento, escopo, **ROI** |
| Auditor/Certificador | aderência a normas (ISO, CMMI), documentação, rastreabilidade |

### Leitura indicada
Pressman 15.3 "O dilema da qualidade" e 15.3.1 "Software bom o suficiente" (texto **não está na pasta**).

---
## AULA 2 — Fatores de Qualidade

### Por que modelar a qualidade
Sem critérios, qualidade é **subjetiva**. Modelos definem **o que medir** e **como avaliar**.

### Modelo de McCall (1977) ⭐
- Criado para a **Força Aérea dos EUA**. Foca na **experiência do usuário**.
| Grupo | Fatores |
|---|---|
| **Operação do produto** | Correção, Confiabilidade, Usabilidade, Integridade, Eficiência |
| **Revisão do produto** | Manutenibilidade (complemento), Flexibilidade, Testabilidade |
| **Transição do produto** | Portabilidade, Reusabilidade, Interoperabilidade |
- ⚠️ A figura do slide repete "Testabilidade" duas vezes no lado "Revisão"; no modelo original o terceiro é **Manutenibilidade** (complemento).
- **Pegadinha:** "Operação" = usar; "Revisão" = mudar/corrigir; "Transição" = levar para outro ambiente.

### ISO 25010 ⭐ (norma mais recente)
**Qualidade em uso (5 características):**
| Característica | Ideia |
|---|---|
| Eficácia | precisão e completude para atingir metas |
| Eficiência | recursos gastos para atingir metas |
| Satisfação | utilidade, confiança, prazer, conforto |
| Ausência de riscos | riscos econômicos, saúde, segurança, ambientais |
| Cobertura do contexto | completude, flexibilidade |

**Qualidade de produto (8 características):**
| Característica | Subcaracterísticas |
|---|---|
| Adequação funcional | completo, correto, apropriado |
| Eficiência de desempenho | tempo, uso de recursos, capacidade |
| Compatibilidade | coexistência, interoperabilidade |
| Usabilidade | adequabilidade, aprendizagem, operabilidade, proteção contra erros, estética, acessibilidade |
| Confiabilidade | maturidade, disponibilidade, tolerância a falhas, recuperação |
| Segurança | confidencialidade, integridade, responsabilidade, autenticidade |
| Manutenibilidade | modularidade, reusabilidade, modificabilidade, testabilidade |
| Portabilidade | adaptabilidade, instalabilidade, substituição |
- **Pegadinha:** **testabilidade** é sub de **manutenibilidade**; **interoperabilidade** é sub de **compatibilidade**; **disponibilidade** é sub de **confiabilidade**.
- **Exemplo (app de banco):** responde rápido? (desempenho) · funciona em vários celulares? (compatibilidade) · protege transações? (segurança).

### Avaliação qualitativa × quantitativa
- **Qualitativa:** checklists, questionários com tarefas para usuários (ex.: perguntas de usabilidade da ISO 25010).
- **Quantitativa:** métricas; sempre **parcialmente imperfeitas** pela natureza subjetiva da qualidade.

---
## AULA 3 — Fatores Humanos

### Fatores humanos
- **Definição:** como pessoas interagem com sistemas (capacidades, limitações, preferências).
- **Impactam:** eficiência no uso, satisfação, redução de erros.

### Fatores humanos na ISO 25010
| Fator | Exemplo da aula |
|---|---|
| Aprendibilidade | app ensina passo a passo o 1º PIX |
| Eficiência no uso | atalhos de teclado no Excel |
| Memorabilidade | menus consistentes, retomar uso rápido |
| Prevenção de erros | campo CPF não aceita letras |
| Satisfação subjetiva | design fluido, sem travar |
| Acessibilidade | compatível com leitor de tela |

### 10 Heurísticas de Nielsen ⭐
1. Visibilidade do status do sistema
2. Correspondência entre o sistema e o mundo real
3. Controle e liberdade do usuário (Ctrl+Z)
4. Consistência e padrões
5. Prevenção de erros
6. Reconhecimento em vez de memorização
7. Flexibilidade e eficiência de uso
8. Estética e design minimalista
9. Ajudar a reconhecer, diagnosticar e **recuperar** de erros
10. Ajuda e documentação

### Boas × más práticas
| Aspecto | Boa | Má |
|---|---|---|
| Consistência | botões previsíveis | mesmo elemento com aparência diferente |
| Feedback | "Enviado com sucesso!" | nenhuma resposta |
| Prevenção de erros | CPF só números + alerta | aceita qualquer coisa |
| Visibilidade de status | barra de progresso | usuário acha que travou |
| Reconhecimento | menus com rótulos claros | abas "Item X" |
| Acessibilidade | contraste, texto redimensionável | texto pequeno, cores claras |
- **Pegadinha:** **prevenção** (#5, evita o erro antes) × **recuperação** (#9, ajuda depois que o erro ocorreu).

---
## AULA 4 — Métricas de Software

### Métrica
- **Definição (IEEE):** "medida quantitativa do grau em que um sistema, componente ou processo possui um atributo".
- "Medir é essencial para gerenciar."
- **Por que medir:** avaliar qualidade, achar problemas, **estimar esforço**, controlar o projeto, ver evolução.

### Propriedades desejáveis
Fácil de calcular/entender · estatisticamente estudável · tem **unidade** · obtida **cedo** · automatizável · **repetível e independente do observador** · ligada a uma estratégia de melhoria.

### Classificações ⭐
| Por objeto | Avalia |
|---|---|
| **Produto** | características do software |
| **Processo** | como é produzido |
| **Projeto** | gerenciamento/execução |

| Por forma | Definição | Exemplos |
|---|---|---|
| **Direta** (básica) | observada/contada | custo, LOC, nº páginas, nº diagramas |
| **Indireta** (derivada) | calculada de outras | produtividade, % retrabalho, complexidade, manutenibilidade |

| Outras | Ideia | Exemplo |
|---|---|---|
| Orientadas a **tamanho** | tamanho dos artefatos | LOC, custo, nº defeitos nos requisitos |
| Orientadas a **função** | ponto de vista do usuário | **SOD** (funções entregues/mês) |
| De **produtividade** | saída do processo | **PDR** (horas por função) |
| **Técnicas** | características do software | complexidade, nº de filhos de uma classe |
- **Pegadinha:** "nº de defeitos" = **direta**; "defeitos por KLOC" = **indireta** (é uma divisão).

### Escolha das métricas
**Relevância · Mensurabilidade · Custo de coleta · Ação** (leva a decisão?).
- **Métrica de vaidade:** número bonito que não indica valor real (ex.: "linhas de código escritas").

### GQM (Goal-Question-Metric) ⭐
- **Goal:** objetivo de medição → **Question:** perguntas que mostram se a meta é atingida → **Metric:** dados que respondem.
- **Benefício:** métricas **alinhadas** a objetivos reais.
- **Modelo de Basili:** "Analisar **[objeto]** com a finalidade de **[propósito]** com respeito a **[foco de qualidade]** do ponto de vista de **[perspectiva]** no contexto de **[ambiente]**."
- **Frase-chave:** "O mesmo contexto produz métricas distintas quando a perspectiva muda."

---
## AULA 5 — CMM (Capability Maturity Model)

### Motivação
Sistema hospitalar 3 meses atrasado e 40% acima do orçamento — faltou talento ou **processo**? Em ambientes caóticos, sucesso depende de **heróis**, não de métodos.

### CMM
- Criado pelo **SEI** (Software Engineering Institute) para avaliar e melhorar a capacitação de quem desenvolve software.
- Foco na **documentação de processos**.
- Classifica a organização por **maturidade** e permite comparar.

### Estrutura
Níveis de maturidade → **Áreas-chave** (metas) → **Características comuns** → **Práticas-chave**.

### 5 níveis ⭐
| Nível | Nome | Resumo | Exemplo do slide |
|---|---|---|---|
| 1 | **Inicial** | caótico; sucesso depende de **esforço individual** | Empresa C: cada projeto de um jeito |
| 2 | **Repetível** | gestão básica (custo, prazo, escopo); **repete** sucessos em projetos similares | Empresa B: projetos similares no prazo, mas cada equipe do seu jeito |
| 3 | **Definido** | processo **documentado e padronizado na organização**; projetos usam versão adaptada e aprovada | Empresa E: todos seguem o mesmo padrão |
| 4 | **Gerenciado** | produto e processo controlados **quantitativamente** (métricas) | Empresa D: diretoria sabe a qualidade em números |
| 5 | **Otimizado** | **melhoria contínua**; prevenção de defeitos | Empresa A: elimina defeito recorrente mudando o processo |
- ⚠️ A figura do slide 9 chama o nível 2 de "Gerenciado" e o 4 de "Quantitativamente Gerenciado" (nomes do **CMMI**). No **CMM** clássico: 2 = **Repetível**, 4 = **Gerenciado**.

### Áreas-chave por nível ⭐
| Nível | Áreas-chave |
|---|---|
| 1 | — |
| 2 Repetível | Ger. de requisitos · Planejamento do projeto · Acompanhamento do projeto · Ger. de subcontratados · **Garantia da qualidade** · Ger. de configuração |
| 3 Definido | Foco do processo organizacional · Definição do processo organizacional · **Programa de treinamento** · Ger. de software integrado · Eng. de produto · **Coordenação intergrupos** · Revisão conjunta |
| 4 Gerenciado | **Gerenciamento quantitativo** dos processos · Ger. da qualidade de software |
| 5 Otimizado | **Prevenção de defeitos** · Ger. de mudanças tecnológicas · Ger. de mudanças no processo |

### 5 Características comuns
| Característica | Práticas |
|---|---|
| Compromisso de realizar | políticas, gerente experiente |
| Capacidade de realizar | recursos, estrutura, treinamento |
| Atividades realizadas | planos, procedimentos, acompanhamento, ações corretivas |
| Medições e análise | medir o estado e a efetividade |
| Implementação com verificação | revisão, auditoria, garantia da qualidade |
- **Práticas-chave** dizem **"o que"** fazer, não **"como"**.

### Implantação (processo cíclico)
Análise da situação → comparação com o **próximo nível** → planejamento de ações corretivas → execução → nova análise.
- Avaliação oficial do SEI: abrangente, **cara** e "traumática".

---
## AULA 6 — CMMI

### Limitações do CMM → CMMI
Restrito a software · vários CMMs separados · difícil melhorar áreas específicas → nasce o **CMMI** (Integration).

### CMMI
- **Framework de melhoria de processos** que **integra** disciplinas (software, sistemas, fornecedores).
- **Estrutura:** Áreas de Processo (PA) → Objetivos **específicos** (o que implementar) / **genéricos** (institucionalizar) → Práticas **específicas** / **genéricas** (repetíveis e sustentáveis).
- **Exemplo — Gerência de Requisitos:** prática específica = "desenvolver entendimento com os fornecedores dos requisitos sobre o significado dos requisitos".

### Representações ⭐
| Aspecto | **Por Estágios** | **Contínuo** |
|---|---|---|
| Foco | maturidade **organizacional** | capacidade de **cada processo** |
| Escala | níveis de **maturidade 1–5** | níveis de **capacidade 0–5** |
| Vantagem | caminho claro | flexibilidade, priorização |
| Limitação | menos adaptável | mais complexo de gerenciar |
- **Níveis de capacidade (contínuo):** 0 Incompleto · 1 Executado · 2 Gerenciado · 3 Definido · 4 Quantitativamente gerenciado · 5 Em otimização.
- **Pegadinha:** **contínuo começa em 0**; **estágios começa em 1**.
- **Exemplo do slide (contínuo):** Ger. de configurações = 4, Monitoração = 3, Verificação = 3, Requisitos = 2, Validação = 2, Riscos = 1, Fornecedores = 1.

### 22 Áreas de processo por nível (estágios)
| Nível | Áreas |
|---|---|
| 2 Gerenciado | Ger. de Configuração · **Medição e Análise** · Monitoramento e Controle · Planejamento · Garantia da Qualidade de Processo e Produto · Ger. de Requisitos · Ger. de Acordos com Fornecedores |
| 3 Definido | Análise e Resolução de Decisões · Ger. Integrado · Definição de Processos Org. · Foco em Processos Org. · Treinamento Org. · Integração de Produto · Desenvolvimento de Requisitos · **Ger. de Riscos** · Solução Técnica · **Validação** · **Verificação** |
| 4 Quant. Gerenciado | Desempenho de Processos Org. · Ger. Quantitativo de Projetos |
| 5 Em Otimização | **Análise e Resolução de Causas** · Ger. de Desempenho Org. |

### Verificação × Validação ⭐
- **Verificação:** o produto atende aos **requisitos especificados** ("fizemos certo?").
- **Validação:** atende às **necessidades do usuário final** ("fizemos a coisa certa?").

---
## AULA 7 — SQA (Planejamento e Garantia da Qualidade)

### Gerenciamento da qualidade = 3 atividades
**Planejamento → Garantia (QA) → Controle (QC)**.

### Planejamento da qualidade
- **Proativo**: define **como** a qualidade será atingida; políticas, padrões, objetivos.
- Documentado no **Plano de Qualidade** (parte do plano do projeto).
- **Plano contém:** objetivos · padrões (IEEE, ISO) · processos/metodologia · estratégia de V&V · critérios de aceitação e métricas · papéis · plano de auditorias e revisões.

### SQA (Garantia)
- Atividades sistemáticas para garantir **conformidade** com padrões, normas e planos.
- Atua em **processos, métodos e artefatos**; visa **prevenir** defeitos.

### Técnicas ⭐
| Tipo | Técnicas |
|---|---|
| **Estáticas** (sem executar código) | Auditoria · Inspeção · Walkthrough · Revisões Técnicas · Revisões Gerenciais · Avaliação · Seis Sigma |
| **Dinâmicas** (executam código) | Testes |

| Técnica | Uma linha | Exemplo do slide |
|---|---|---|
| **Auditoria** | verifica se o **processo** segue padrões (independente) | auditor confere se sprints têm retrospectiva documentada |
| **Inspeção** | revisão **formal** para achar falhas em documentos | ler requisitos em voz alta e achar "rapidamente" (ambíguo) |
| **Walkthrough** | revisão **informal**; educar/entender | dev apresenta o diagrama de classes aos colegas |
| **Revisão Técnica** | conformidade do produto e integridade após mudanças | revisar acesso a dados após trocar ORM |
| **Revisão Gerencial** | eficácia dos processos/padrões | gerência analisa indicadores trimestrais |
| **Avaliação** | compara processo com modelo/norma | consultoria CMMI: nível 2, falta X para o 3 |
| **Seis Sigma** | dados e estatística — **DMAIC** | falhas no Pix de 8% → 0,3% |
| **Testes** | executa o código | SQA **não executa**; verifica se há plano e registro |

### Tabela comparativa (slide 16)
| | Auditoria | Inspeção | Walkthrough | Rev. Técnica | Rev. Gerencial |
|---|---|---|---|---|---|
| Grupo | 1–5 | 3–6 | 2–7 | 3+ | 2+ |
| Líder | líder de auditoria | **facilitador treinado** | facilitador ou **autor** | engenheiro-chefe | gerente |
| Checklist de defeitos | sim | sim | não | não | não |
| Treinamento formal | sim | sim | não | não | não |
| Participação gerencial | sim | **não** | não | opcional | sim |
| Saída | relatório formal | lista de anomalias | lista de anomalias, itens de ação | doc. da revisão | doc. da revisão |

### QA × QC ⭐
| Garantia (QA) | Controle (QC) |
|---|---|
| foca no **processo** | foca no **produto** |
| **prevenir** defeitos | **detectar** defeitos |
| ex.: auditar aderência ao padrão de documentação | ex.: teste de regressão numa nova funcionalidade |
- **Pegadinha:** o SQA **não executa testes** — isso é QC. Mas um depende do outro.

### Exemplo (Gestão Acadêmica)
Objetivo 99% disponibilidade · padrão IEEE 830 · QA: auditoria mensal do versionamento · QC: testes automatizados por sprint · métricas: resposta < 2s, cobertura > 80%.

---
> ⚠️ **Lacunas:** (1) **Testes de software** (tipos, unidade, integração/API, interface web, ferramentas) estão na ementa mas **sem aula** na pasta. (2) **ISO 9001/normas ISO** citadas só no histórico. (3) A **Atividade de CMMI** exige ler um artigo externo (Synapsis, SBQS 2013) que **não está na pasta**. (4) Leitura do Pressman (cap. 15) também não está na pasta.
