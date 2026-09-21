# DevOps — Questões de treino

---
**1.** Explique o conflito entre Dev e Ops que motivou o DevOps.

**2.** Cite e explique os 4 pilares C.A.M.S.

**3.** Qual a diferença entre `git commit` e `git push`? E qual o papel do Pull Request no CI/CD?

**4.** Complete a tabela VM × Container (recursos, isolamento, inicialização).

**5.** Qual a diferença entre imagem Docker e container? E o que é o Dockerfile?

**6.** Cite as 5 etapas que o pipeline de CI executa a cada push/PR.

**7.** (V ou F)
a) Containers têm um sistema operacional completo próprio.
b) No pipeline da aula, a imagem é publicada no GHCR em todo Pull Request.
c) `needs: test-and-build` faz o Job 2 rodar apenas se o Job 1 terminar com sucesso.
d) SAST analisa as vulnerabilidades das bibliotecas usadas no `package.json`.

**8.** Diferencie Entrega Contínua de Implantação Contínua conforme a aula.

**9.** Associe: (A) SCA (B) SAST (C) Container scan
( ) Trivy ( ) CodeQL ( ) npm audit ( ) Vulnerabilidade na imagem node:22 ( ) SQL Injection no app.js

**10.** Um dev abre um PR da branch `dev` para a `main`. Os testes passam. Quais steps rodam e quais são pulados? E depois do merge?

**11.** O que faz cada comando?
a) `docker build -t ola-devops .`
b) `docker run -p 3000:3000 -d ola-devops`
c) `git checkout -b feature-login`

**12.** Por que as verificações de segurança ficam depois dos testes e antes da publicação da imagem?

**13.** No Dockerfile, qual a diferença entre `RUN` e `CMD`?

**14.** Uma empresa sofre com "na minha máquina funciona". Qual tecnologia da disciplina resolve e por quê?

**15.** Explique, em um parágrafo, em que situação o CI/CD é útil numa empresa.

---
# Gabarito

**1.** Dev foca em **velocidade/inovação**; Ops em **estabilidade/segurança**. Metas opostas geram lentidão, culpa mútua e retrabalho.

**2.** **Cultura** (colaboração, responsabilidade compartilhada); **Automação** (testes, deploy, infra); **Medição** (métricas, monitoramento — "o que não é medido não é gerenciado"); **Compartilhamento** (conhecimento, feedback, falhas).

**3.** `commit` salva **localmente**; `push` envia ao **remoto**. PR = pedido de merge com **revisão de código**, discussão e **gatilho do pipeline de CI**.

**4.** VM: pesada (SO dedicado) | isolamento forte (hardware virtualizado) | minutos. Container: leve (compartilha kernel) | médio (processos isolados) | segundos.

**5.** **Imagem** = modelo estático, a "receita final". **Container** = imagem em execução (complemento). **Dockerfile** = arquivo texto com as instruções para construir a imagem (infraestrutura como código).

**6.** Baixa código → instala dependências → executa testes → build → notifica.

**7.** a) **F** (compartilha o kernel do host). b) **F** (só em push na main, após merge). c) **V**. d) **F** — isso é **SCA**; SAST analisa o **seu** código.

**8.** **Entrega Contínua:** após o merge, a imagem é **publicada** no registro (GHCR). **Implantação Contínua:** após publicar, o pipeline **implanta automaticamente** no servidor (runner self-hosted + docker-compose).

**9.** (C), (B), (A), (C), (B).

**10.** No PR: checkout, setup Node, npm install, npm test, npm audit, buildx e build da imagem **rodam**; login no GHCR, extrair metadados e push **skipped**; Job 2 não roda. O PR fica liberado (status check ok). Após o merge: ocorre **push na main** → tudo roda, inclusive login + push da imagem, e o Job 2 faz o deploy local.

**11.** a) constrói uma **imagem** chamada `ola-devops` usando o Dockerfile da pasta atual (`.`). b) cria e roda um container em **segundo plano** (`-d`) mapeando a porta 3000 do host para a 3000 do container. c) cria a branch `feature-login` e muda para ela.

**12.** Para **nunca construir/publicar** um artefato que sabemos estar inseguro; e não gastar tempo escaneando código que nem passa nos testes.

**13.** `RUN` executa **durante a construção da imagem** (ex.: `npm ci`). `CMD` define o comando executado **quando o container inicia** (ex.: `node server.js`).

**14.** **Docker/containers**: empacota código + runtime + bibliotecas + configurações, então a aplicação roda **igual** em qualquer ambiente (consistência).

**15.** Modelo: "Em empresas com vários desenvolvedores alterando o mesmo sistema, o CI testa automaticamente cada mudança e avisa em minutos se algo quebrou, mantendo a main estável. O CD publica e implanta a nova versão sem passos manuais, permitindo lançar correções várias vezes ao dia com menos erro humano."
