# Auditoria de Segurança da Informação — Conceitos (ordem das aulas)

---
## AULA 00 — Introdução à Auditoria

### Auditoria
- **Definição:** exame de operações, processos, sistemas e responsabilidades gerenciais para verificar **conformidade** com objetivos, políticas, orçamentos, regras, normas ou padrões.
- **Exemplo:** verificar se o sistema de folha de pagamento segue a política interna e a lei trabalhista.
- **Pegadinha:** auditoria **não é só financeira**. Ela avalia processos e sistemas também.

### Contexto da auditoria
- **Definição:** testes de **confiabilidade dos registros** comparando com os **documentos-fonte**.
- Com a TI, é preciso **guardar as informações** para ficarem acessíveis quando a auditoria pedir.
- Com Internet e negócios maiores, cresceram a **vulnerabilidade** (física e lógica) e as **fraudes**.
- **Pegadinha:** proteção da informação tem **dois lados**: **física** (sala, equipamento) e **lógica** (senha, permissão).

### Benefícios da auditoria (lista das aulas)
| Grupo | Exemplos |
|---|---|
| Eficiência | reduzir custos, melhorar fluxo de processos, economia de tempo |
| Qualidade | melhor quantidade/qualidade do trabalho, menor risco de auditoria, melhor apresentação |
| Pessoas | treinamento, superar resistência à tecnologia, qualidade de vida dos usuários |
| Tecnologia | escolher/implantar software e hardware, backup e segurança de arquivos eletrônicos |
| Comunicação | chat, e-mail, portais, workshops; transferência de conhecimento entre equipes |
| Outros | independência do papel, preparar para globalização |

### Aspectos: Auditoria de Sistemas de Informação
- **Definição:** determina a **postura da organização em relação à segurança**; avalia a política de segurança e os controles.
- **Escopo:** avaliação da política de segurança · controle de acesso **lógico** · controle de acesso **físico** · controles **ambientais** · **plano de contingência e continuidade**.
- **Outros controles:** organizacionais, de mudanças, armazenamento de dados, equipamentos, controle de acesso.
- **Pegadinha:** "controle ambiental" = proteção do ambiente físico (temperatura, energia, incêndio) (complemento) — não é "meio ambiente/ecologia".

### Aspectos: Auditoria de Aplicativos
- **Definição:** foca na segurança e no controle de **um aplicativo específico**.
- **Controla:** desenvolvimento/implantação/uso · **entrada, processamento e saída** de dados · conteúdo e funcionamento do app (confidencialidade).
- **Exemplo:** auditar só o sistema de prontuário de um hospital.
- **Pegadinha:** Auditoria de **SI** = visão **global** da organização. Auditoria de **aplicativos** = **um sistema** específico.

### Coleta de informações
Objetivos organizacionais · Política de informação · Grupo de usuários (**amostra**) · Requisitos de informação dos usuários · Recursos de informação · **Representação gráfica** do funcionamento do sistema.

### Avaliação de sistemas
- Avaliar **áreas prioritárias** a auditar
- Análise de **custo-benefício**
- Análise de **falhas / fatores críticos**
- **Teste de todo o sistema** (um processo que passe do início ao fim)

### Processos da auditoria
1. Definir objetivos do sistema
2. Avaliar métodos alternativos
3. Determinar custos das alternativas
4. Modelos que relacionem custo × potencial de atingir objetivos
5. Critérios de custo/benefício para **ordenar** alternativas
6. Gerar soluções para as falhas
7. Avaliar alternativas
8. Verificar regulamentos e normas
9. **Propor recomendações**

### Automação de processos de auditoria
Identificar áreas problemáticas e automatizáveis · agregar valor · equipes virtuais especializadas · fluxo de informação mais rápido · maior satisfação · tarefas feitas por profissionais **menos experientes**.
- **Pegadinha:** automação permite que profissionais **menos** experientes façam tarefas (isso é listado como benefício).

---
## AULA 01 — Auditoria de Sistemas

### O que é Auditoria de Sistemas
- **Definição:** processo de avaliação dos **controles internos** de sistemas computacionais.
- **Objetivo:** assegurar **integridade, confiabilidade, segurança e conformidade**.
- **Exemplo:** verificar quem tem acesso ao banco de dados de clientes e se isso é registrado em log.

### Auditoria Contábil × Auditoria de Sistemas
| Contábil | De Sistemas |
|---|---|
| Foco em **registros financeiros** | Foco em **controles, acessos, segurança e operação de TI** |

### Objetivos da Auditoria de Sistemas
1. Avaliar **controles internos**
2. Garantir **segurança da informação**
3. Identificar **vulnerabilidades**
4. Promover **conformidade** com normas e regulamentos

### Tipos de auditoria
| Tipo | Ideia (complemento na explicação) |
|---|---|
| **Interna** | feita por pessoas da própria empresa |
| **Externa** | feita por empresa/auditor independente, de fora |
| **Operacional** | avalia eficiência e eficácia das operações/processos |
| **De Conformidade** | verifica se cumpre leis, normas, políticas (ex.: LGPD, ISO 27001) |
| **De Sistemas** | avalia controles, segurança e operação de TI |
- **Pegadinha:** uma auditoria pode ser de **mais de um tipo** ao mesmo tempo (ex.: interna + de sistemas + de conformidade).

### Ciclo de Auditoria (6 etapas) ⭐
| # | Etapa | O que se faz |
|---|---|---|
| 1 | **Planejamento** | define objetivos, escopo, equipe, cronograma |
| 2 | **Execução** | aplica os testes e procedimentos |
| 3 | **Coleta de Evidências** | logs, entrevistas, documentos, configurações |
| 4 | **Análise** | compara evidências com normas; classifica riscos |
| 5 | **Relatório** | documenta achados, riscos e recomendações |
| 6 | **Acompanhamento** | verifica se as melhorias foram implantadas |
- **Pegadinha:** a auditoria **não termina no relatório** — existe o **acompanhamento**.

### Importância
Proteção dos **ativos de informação** · detecção e prevenção de **fraudes** · apoio à **governança de TI** · atende requisitos **legais e normativos**.

### Estudo de caso da aula
Hospital universitário com prontuário eletrônico; suspeita de **acessos indevidos a dados confidenciais**. Tarefa: objetivos, tipo, como coletar evidências, 3 evidências, grau de risco, relatório, plano de acompanhamento. (Resolvido no arquivo 03.)

---
## AULA 02 — Segurança da Informação

### Segurança da Informação
- **Definição:** proteção das informações contra acessos não autorizados, garantindo **Confidencialidade, Integridade e Disponibilidade (CID)**.

### Princípios (tríade CID) ⭐
| Princípio | Definição | Exemplo de violação |
|---|---|---|
| **Confidencialidade** | proteção contra **acessos indevidos** | funcionário lê prontuário que não deveria |
| **Integridade** | informação **não foi alterada** indevidamente | alguém muda o valor de uma nota fiscal |
| **Disponibilidade** | acesso garantido **quando necessário** | site fora do ar por DDoS |
- **Pegadinha:** **ransomware** afeta principalmente a **disponibilidade** (dados sequestrados/criptografados). Vazamento afeta **confidencialidade**. Alteração afeta **integridade**.

### Principais ameaças
| Ameaça | Uma linha (complemento) |
|---|---|
| **Malware** (vírus, worms, trojans) | software malicioso |
| **Phishing** | mensagem falsa para roubar senha/dados |
| **DDoS** | sobrecarga para derrubar o serviço |
| **Engenharia social** | manipula **pessoas** para obter acesso |
| **Ransomware** | criptografa dados e pede resgate |

### Vulnerabilidades
- **Definição:** fragilidades em sistemas ou processos que podem ser **exploradas por ameaças**.
- **Exemplos da aula:** software desatualizado · senha fraca · falta de backup · permissões mal configuradas.
- **Pegadinha:** **ameaça ≠ vulnerabilidade**. Phishing é **ameaça**; "usuário sem treinamento" ou "sem autenticação em dois fatores" é **vulnerabilidade**.

### Medidas de proteção
Antivírus e firewall · Criptografia · Controle de acesso · Atualizações frequentes · Políticas de segurança.

### Segurança no ciclo de vida dos sistemas
- **Definição:** segurança incorporada **desde a concepção até o descarte**.
- **Etapas citadas:** análise de riscos → testes de segurança → monitoramento contínuo → descarte seguro.
- **Pegadinha:** segurança **não** é só no final (depois de pronto). E o **descarte** também precisa ser seguro (apagar HD, destruir mídia).

### Estudo de caso da aula
Varejo online com **falhas de login e acesso indevido a contas**. Tarefa: 3 ameaças, vulnerabilidades, problemas para empresa, problemas para clientes, relatório, medidas de mitigação. (Resolvido no arquivo 03.)

---
> ⚠️ **Aviso:** os slides das Aulas 01 e 02 são curtos (tópicos em diagrama). Explicações dos "tipos de auditoria" e das ameaças foram completadas com conhecimento geral (marcado como complemento).
