# Gestão da Qualidade — Questões de treino

---
**1.** Diferencie qualidade de produto e qualidade de processo. Por que "bons processos aumentam a probabilidade de bons produtos"?

**2.** Para cada perspectiva (desenvolvedor, usuário, cliente, auditor), diga o que significa qualidade.

**3.** Classifique no modelo de McCall (Operação, Revisão ou Transição): Portabilidade, Correção, Testabilidade, Eficiência, Reusabilidade, Flexibilidade.

**4.** Associe à característica da ISO 25010: (a) app funciona no Android e no iOS; (b) sistema volta rápido após queda; (c) código fácil de testar; (d) só usuários autorizados veem os dados.

**5.** Um formulário aceita data "31/02" sem aviso e, após salvar, não mostra nenhuma mensagem. Quais heurísticas de Nielsen foram violadas?

**6.** Classifique cada métrica em direta/indireta e produto/processo/projeto:
a) Nº de linhas de código · b) Defeitos por KLOC · c) Custo do projeto em R$ · d) % de casos de teste executados.

**7.** O que é métrica de vaidade? Dê um exemplo.

**8.** Escreva uma meta GQM (modelo Basili) para: diretoria quer saber o custo da não qualidade da ClínicasPA. Proponha 2 perguntas e 2 métricas.

**9.** Diagnostique o nível CMM: "A empresa tem plano de projeto com prazo e custo e projetos parecidos terminam no prazo, mas cada gerente trabalha do seu jeito e não há processo organizacional documentado." O que falta para subir?

**10.** Diagnostique: "A equipe mede a densidade de defeitos e só aceita entregas dentro de limites de controle definidos. Quando algo sai do limite, segue um protocolo." Qual área-chave levaria ao próximo nível?

**11.** Compare CMMI por Estágios e Contínuo (foco, escala).

**12.** Diferencie Verificação e Validação.

**13.** Classifique a técnica de SQA:
a) Dev apresenta o diagrama de classes aos colegas para todos entenderem.
b) Leitura formal do documento de requisitos em voz alta, com checklist, procurando ambiguidades.
c) Auditor externo verifica se todas as sprints têm retrospectiva documentada.
d) Equipe usa DMAIC para reduzir falhas no Pix de 8% para 0,3%.

**14.** (V ou F)
a) O SQA executa os testes de regressão.
b) Garantia da qualidade foca no processo; controle da qualidade, no produto.
c) Técnicas estáticas executam o código.
d) No CMMI contínuo, cada área de processo pode ter um nível de capacidade de 0 a 5.

**15.** Cite 4 itens que um Plano de Qualidade deve conter.

---
# Gabarito

**1.** Produto = características do software entregue (correção, usabilidade, desempenho...). Processo = como é desenvolvido (processos definidos, normas, padronização). Um processo bem estruturado (testes, documentação, código organizado) torna o resultado consistente; um produto bonito feito sem processo tende a falhar com o tempo.

**2.** Desenvolvedor: código limpo, modular, testável. Usuário: fácil de usar, rápido, sem falhas visíveis. Cliente: prazo, orçamento, escopo, ROI. Auditor: aderência a normas, documentação, rastreabilidade.

**3.** Portabilidade – Transição; Correção – Operação; Testabilidade – Revisão; Eficiência – Operação; Reusabilidade – Transição; Flexibilidade – Revisão.

**4.** a) **Compatibilidade** (ou Portabilidade/adaptabilidade — aceite se justificar); b) **Confiabilidade** (facilidade de recuperação); c) **Manutenibilidade** (testabilidade); d) **Segurança** (confidencialidade).

**5.** #5 **Prevenção de erros** (aceitou data inválida) e #1 **Visibilidade do status** / feedback (nenhuma confirmação). Também #9 se não ajuda a corrigir.

**6.** a) direta, produto; b) indireta, produto; c) direta, projeto; d) indireta, processo.

**7.** Número que parece bom mas não indica valor real nem leva a decisões. Ex.: linhas de código escritas, nº de commits.

**8.** Meta: "Analisar **o processo de desenvolvimento e entrega** com a finalidade de **avaliar** com respeito ao **custo da não qualidade** do ponto de vista da **diretoria** no contexto do **projeto ClínicasPA**." Q1: Quanto esforço é gasto com retrabalho e correções emergenciais? Q2: Quanto isso custa por entrega? Métricas: horas de retrabalho por entrega (direta, processo); % do esforço total gasto em correções (indireta, processo); custo em R$ das correções emergenciais (indireta, projeto).

**9.** **Nível 2 – Repetível**: gestão de projeto básica e repetição de sucesso, mas depende da pessoa. Falta (nível 3): **Definição do processo organizacional**, **Foco do processo organizacional**, **Programa de treinamento**.

**10.** **Nível 4 – Gerenciado** (controle quantitativo). Próximo: **Prevenção de defeitos** / **Gerenciamento de mudanças no processo** (nível 5).

**11.** Estágios: foco na **maturidade da organização**, níveis **1–5**, caminho claro, menos adaptável. Contínuo: foco na **capacidade de cada processo**, níveis **0–5**, flexível, mais complexo de gerenciar.

**12.** Verificação: atende aos **requisitos especificados** ("construímos certo?"). Validação: atende às **necessidades do usuário final** ("construímos a coisa certa?").

**13.** a) Walkthrough; b) Inspeção; c) Auditoria; d) Seis Sigma.

**14.** a) **F** (é função do QC; SQA verifica se há plano e registros). b) **V**. c) **F**. d) **V**.

**15.** Objetivos de qualidade; padrões (IEEE/ISO); processos/metodologia; estratégia de V&V; critérios de aceitação e métricas; papéis e responsabilidades; plano de auditorias e revisões (quaisquer 4).
