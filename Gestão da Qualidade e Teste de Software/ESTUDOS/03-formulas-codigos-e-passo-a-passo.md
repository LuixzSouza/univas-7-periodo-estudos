# Gestão da Qualidade — Modelos, fórmulas e passo a passo

---
## Diagramas para memorizar
```
McCALL
        Revisão (Manutenibilidade, Flexibilidade, Testabilidade)   /\   Transição (Portabilidade, Reusabilidade, Interoperabilidade)
                                                                  /  \
        Operação (Correção, Confiabilidade, Usabilidade, Integridade, Eficiência)

CMM (escada)
  5 Otimizado          ← melhoria contínua, prevenção de defeitos
  4 Gerenciado         ← controle quantitativo (métricas)
  3 Definido           ← processo padrão da ORGANIZAÇÃO, treinamento
  2 Repetível          ← gestão por PROJETO (prazo/custo), repete sucesso
  1 Inicial            ← caos, heróis

GQM:  Goal ──► Questions ──► Metrics
SQA:  Planejamento ──► Garantia (processo) ──► Controle (produto)
```

## Fórmulas de métricas usadas em exercícios (complemento — ilustram diretas × indiretas)
| Métrica | Fórmula | Tipo |
|---|---|---|
| Densidade de defeitos | defeitos ÷ KLOC (ou ÷ pontos de função) | indireta, produto |
| % de casos de teste executados | executados ÷ planejados × 100 | indireta, processo |
| Taxa de defeitos escapados | defeitos em produção ÷ (defeitos em teste + produção) × 100 | indireta, processo |
| Taxa de reincidência | defeitos reabertos ÷ defeitos corrigidos × 100 | indireta, processo |
| Desvio de esforço | (real − estimado) ÷ estimado × 100 | indireta, projeto |
| MTTR (tempo médio de correção) | Σ tempos de correção ÷ nº de correções | indireta, processo |
| Nº de chamados pós-entrega | contagem | direta, produto |
| SOD | funções entregues ÷ mês | indireta (orientada a função) |
| PDR | horas ÷ função | indireta (produtividade) |

---
## TIPO 1 — Aplicar GQM (Atividade GQM – ClínicasPA) ⭐

### Passo a passo
1. Leia o contexto e marque os **fatos** ligados à **perspectiva** do grupo.
2. Escreva a **meta** no modelo de Basili (5 partes).
3. Crie **2–3 perguntas** que, respondidas, dizem se a meta foi atingida.
4. Para cada pergunta, **≥ 1 métrica** com a ficha: nome · pergunta · definição operacional (fórmula) · direta/indireta · produto/processo/projeto · unidade · fonte · frequência/responsável · **decisão associada**.
5. Aponte **1 métrica de vaidade** e por que descartar.

### Exemplo resolvido — Grupo 1 (Líder de testes: eficácia do teste)
**Meta:** Analisar **o processo de teste** com a finalidade de **avaliá-lo** com respeito à **eficácia na detecção de defeitos** do ponto de vista do **líder de testes** no contexto do **projeto ClínicasPA**.

**Perguntas:**
- Q1: Quantos defeitos escapam do teste e chegam à produção?
- Q2: Quanto do planejado é de fato testado antes da entrega?
- Q3: As correções voltam a falhar?

| Campo | Métrica 1 | Métrica 2 | Métrica 3 |
|---|---|---|---|
| Nome | Taxa de defeitos escapados | % de casos de teste executados | Taxa de reincidência |
| Pergunta | Q1 | Q2 | Q3 |
| Definição | defeitos achados em produção ÷ total de defeitos da entrega × 100 | casos executados ÷ casos planejados × 100 | defeitos reabertos ÷ defeitos corrigidos × 100 |
| Direta/indireta | indireta | indireta | indireta |
| Categoria | processo | processo | processo |
| Unidade | % | % | % |
| Fonte | sistema de chamados + planilha de testes | planilha de casos de teste | quadro de tarefas / repositório |
| Frequência/resp. | a cada entrega (2 semanas) / líder de testes | a cada entrega / testadores | a cada entrega / líder de testes |
| Decisão | se > 20%, reforçar testes nos módulos que mais falham | se < 80%, priorizar casos por risco e automatizar | se > 10%, exigir teste de regressão nas correções |

**Vaidade descartada:** "nº total de casos de teste escritos" — cresce sem dizer se os testes acham defeitos.

### Metas prontas para os outros grupos
| Grupo | Meta resumida | Métricas sugeridas |
|---|---|---|
| 2 Gerente de projeto (previsibilidade) | Analisar o **planejamento** ... com respeito à **previsibilidade de prazo e esforço** | desvio de esforço %, % de entregas no prazo, nº de horas extras não planejadas |
| 3 Gerente de produto (qualidade percebida) | Analisar o **produto em produção** ... **qualidade percebida pelo usuário** | chamados por entrega (classificados por gravidade), nº de correções emergenciais, taxa de falha nos agendamentos |
| 4 Líder técnico (manutenibilidade) | Analisar o **código-fonte** ... **manutenibilidade** | complexidade ciclomática dos 2 módulos críticos, nº de alterações por módulo (churn), tempo médio para implementar mudança |
| 5 Diretoria (custo da não qualidade) | Analisar o **processo de entrega** ... **custo da não qualidade** | horas gastas em retrabalho/correção emergencial, custo (R$) das correções, % do esforço em retrabalho |
Vaidades típicas: LOC escritas, nº de commits, nº de tarefas fechadas.

---
## TIPO 2 — Diagnosticar o nível CMM por evidências (Atividade CMM) ⭐

### Passo a passo
1. Procure **palavras-sinal**:
| Evidência fala de... | Nível |
|---|---|
| ninguém atualiza, "de cabeça", fim de semana não planejado, ninguém sabe | **1 Inicial** |
| plano de projeto, custo/prazo, reutiliza planejamento anterior, **depende do gerente** | **2 Repetível** |
| processo **documentado na organização**, **treinamento formal**, plano integrado entre grupos, adaptação **aprovada** | **3 Definido** |
| números, **limites de controle**, variação normal × desvio, protocolo quando sai do limite | **4 Gerenciado** |
| **causa-raiz**, mudou o processo e **mediu o ganho**, avalia novas tecnologias pelas métricas | **5 Otimizado** |
2. Escolha o **maior nível totalmente sustentado** pelas evidências.
3. **O que falta:** pegue uma área-chave do **nível seguinte**.
4. **Evidência ausente:** o que você precisaria saber para confirmar.

### Exemplos resolvidos (os 5 grupos da atividade)
| Grupo | Nível | Justificativa | Para avançar (área-chave) | Evidência ausente |
|---|---|---|---|---|
| 1 Líder de testes | **1 Inicial** | cronograma não atualizado; prazo salvo por "heróis" no fim de semana; estimativa "de cabeça"; ninguém sabe o que foi testado | Nível 2: **Planejamento do projeto**, **Acompanhamento do projeto**, **Garantia da qualidade** | existe algum plano de testes, mesmo informal? |
| 2 Gerente de projeto | **2 Repetível** | plano com custo/prazo; reuso do planejamento; sucesso **depende do gerente**; sem processo organizacional | Nível 3: **Definição do processo organizacional**, **Programa de treinamento** | há gerência de configuração e de requisitos? |
| 3 Líder técnico | **3 Definido** | processo documentado da organização; treinamento formal; coordenação intergrupos; adaptação aprovada | Nível 4: **Gerenciamento quantitativo dos processos** | a empresa coleta métricas? usa para decidir? |
| 4 Gerente de produto | **4 Gerenciado** | densidade de defeitos em números; **limites de controle**; protocolo documentado; distingue variação normal de desvio | Nível 5: **Prevenção de defeitos**, **Ger. de mudanças no processo** | há análise de causa-raiz e mudanças de processo baseadas nela? |
| 5 Diretoria | **5 Otimizado** | causa-raiz (60% integração) → mudou o processo → −45% reincidência → incorporado; novas técnicas avaliadas por métricas | manter/ampliar (já no topo) | os níveis 3 e 4 estão institucionalizados em todos os projetos? |

---
## TIPO 3 — Avaliar um sistema pela ISO 25010 / Nielsen (Atividades Aulas 2 e 3)

### Passo a passo
1. Escolha ≥ 4 características da ISO 25010 (ou 2 heurísticas).
2. Para cada: **pergunta** → **observação real** → ponto forte/fraco.

### Exemplo resolvido — App de banco
| Característica | Observação | Forte/Fraco |
|---|---|---|
| Eficiência de desempenho | Pix confirma em ~2s | forte |
| Usabilidade | menu de investimentos confuso | fraco |
| Segurança | exige biometria para transferir | forte |
| Confiabilidade | cai no dia de pagamento | fraco |
| Heurística 1 (visibilidade do status) | mostra "processando..." durante o Pix | forte |
| Heurística 5 (prevenção de erros) | pede confirmação com nome do recebedor | forte |

---
## TIPO 4 — Plano de Qualidade (Atividade Aula 7)

### Passo a passo
1. **2 objetivos mensuráveis** (número + unidade).
2. **2 padrões/normas** (IEEE 830, ISO 25010...).
3. **3 técnicas de SQA** + por quê.
4. **1 métrica de QA** (processo) + **1 de QC** (produto), quando coletar.

### Exemplo resolvido — Agendamento médico online
| Item | Conteúdo |
|---|---|
| Objetivos | 99% de disponibilidade em horário comercial; tempo de resposta < 2s no agendamento |
| Normas | IEEE 830 (requisitos); ISO 25010 (qualidade do produto) |
| Técnica 1: Inspeção | requisitos de saúde não podem ser ambíguos (ex.: regras de cancelamento) |
| Técnica 2: Auditoria | dados de pacientes (LGPD) exigem provar que o processo foi seguido |
| Técnica 3: Revisão técnica | após mudanças na integração com convênios |
| Métrica QA | % de sprints com revisão de código registrada — coletada ao fim de cada sprint |
| Métrica QC | % de cobertura de testes automatizados (> 80%) — a cada build/entrega |

---
## TIPO 5 — Classificar técnica de SQA pelo cenário
| Cenário | Técnica |
|---|---|
| Alguém de fora verifica se o processo foi seguido | Auditoria |
| Leitura formal do documento procurando defeitos, com checklist | Inspeção |
| Autor apresenta para a equipe entender | Walkthrough |
| Conferir se mudança técnica quebrou regras | Revisão técnica |
| Gerência analisa indicadores do processo | Revisão gerencial |
| Comparar processo com CMMI/norma | Avaliação |
| DMAIC com estatística | Seis Sigma |
| Executar o sistema | Teste (dinâmica, QC) |
