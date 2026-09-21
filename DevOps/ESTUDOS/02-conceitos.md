# DevOps — Conceitos (ordem das aulas)

---
## AULA 01 — Introdução ao DevOps + Controle de Versão

### Antes do DevOps: os "muros"
| Dev | Ops |
|---|---|
| inovação, novas funcionalidades, **velocidade** | **estabilidade**, segurança, infraestrutura, evitar falhas |
- **Conflito:** metas opostas → lentidão, "jogar a culpa", retrabalho.

### DevOps
- **Definição:** união de **cultura, práticas e ferramentas** para entregar aplicações em **alta velocidade**, melhor que abordagens tradicionais.
- **Pegadinha:** DevOps **não é só ferramenta** e não é um cargo — é **cultura** também.

### Pilares C.A.M.S ⭐
| Pilar | Uma linha |
|---|---|
| **Cultura** | colaboração, responsabilidade compartilhada, confiança |
| **Automação** | automatizar tarefas repetitivas (testes, deploy, infra) |
| **Medição** | métricas e monitoramento — "o que não é medido não é gerenciado" |
| **Compartilhamento (Sharing)** | compartilhar conhecimento, feedback, sucessos e falhas |

### Benefícios
Velocidade de entrega · confiabilidade (menos falhas, recuperação rápida) · colaboração · melhoria contínua · satisfação do cliente.

### Sem controle de versão (o caos)
`codigo_final_2.js`, perda de trabalho, merge manual com erros, **impossível reverter** → medo de mudar.

### VCS (Sistema de Controle de Versão)
- **Definição:** registra todas as mudanças ao longo do tempo e permite recuperar versões.
- **Benefícios:** histórico (quem, o quê, quando) · rastreabilidade (voltar versões) · trabalho paralelo.
- **Ferramenta dominante:** **Git**.

### Ciclo de colaboração
| Comando | Faz |
|---|---|
| `git clone` | baixa cópia do repositório central |
| `git commit` | salva a mudança **localmente** |
| `git push` | envia para o repositório **remoto** |
| `git pull` | baixa mudanças dos colegas |
- **Pegadinha:** `commit` é **local**; só o `push` envia ao servidor.

### Branch
- **Definição:** linha de desenvolvimento **isolada** da principal (`main`/`master`).
- **Para quê:** trabalhar em feature/bug sem quebrar produção; base para PRs.
- **Fluxo:** cria branch → muda e testa → abre **PR** → **merge** na main.

### Pull Request (PR)
- **Definição:** pedido para mesclar sua branch na principal.
- **Funções:** **revisão de código** · **gatilho do CI/CD** · discussão/feedback.

### VCS + CI/CD
`git push` ou abrir PR → **dispara o pipeline de CI**. "Sem Git, não há CI/CD eficiente."

---
## AULA 02 — Containers e Docker

### Problema "Na minha máquina funciona"
Causas: versão diferente do Java (JDK 8 × 17), biblioteca faltando, configs do SO diferentes, variáveis de ambiente ausentes.

### Container ⭐
- **Analogia:** contêiner de navio — tamanho padrão, o navio não se importa com a carga.
- **Definição:** pacote padronizado com **código + runtime + bibliotecas + configurações**.
- **Princípio:** roda **igual em qualquer ambiente**.

### Docker
- **Definição:** plataforma mais popular para **construir, distribuir e executar** containers.
- **Componentes:** **Docker Engine** (roda containers) · **Imagem** (modelo estático, "receita final") · **Docker Hub** (repositório de imagens, "GitHub das imagens").
- **Slogan:** "Construa uma vez, execute em qualquer lugar".
- **Pegadinha (complemento):** **imagem** = molde parado; **container** = imagem **em execução**.

### VM × Container ⭐
| Característica | VM | Container |
|---|---|---|
| Recursos | pesado (SO dedicado, GB) | leve (compartilha **kernel** do host, MB) |
| Isolamento | **forte** (hardware virtualizado) | **médio** (processos isolados) |
| Inicialização | minutos | segundos |
- **Pegadinha:** container **não** tem SO completo próprio; VM tem **isolamento mais forte**.

### Dockerfile
- **Definição:** arquivo de texto com as instruções para **construir a imagem**.
- **Infraestrutura como Código:** versionado no Git junto com o código.
- Instruções: `FROM` (imagem base), `WORKDIR`, `COPY`, `RUN`, `EXPOSE` (porta), `CMD`/`ENTRYPOINT` (comando de execução).

### Por que containers são essenciais ao DevOps
**Consistência** (igual em dev/teste/prod) · **Imutabilidade** (imagem não muda: o que passou no teste vai pra produção) · **Portabilidade** (AWS, Azure, GCP) · **Escalabilidade** (Kubernetes orquestra milhares).

---
## AULA 03 — Integração Contínua (CI)

### CI ⭐
- **Definição:** integrar o código de forma **frequente, automática e testada** — várias vezes ao dia.
- **O "robô" (pipeline), a cada push/PR:**
  1. **Baixa o código**
  2. **Instala dependências**
  3. **Executa testes** (se 1 falhar, **para**)
  4. **Build** (gera pacote — aqui, imagem Docker)
  5. **Notifica** (feedback rápido)
- **Por que:** feedback rápido · bugs fáceis (mudanças pequenas) · main sempre estável · menos erro humano · **base para CD**.

### Prática (Node.js + Express)
- `app.js` (lógica, exporta `app`) separado de `server.js` (só sobe o servidor) → **facilita testes**.
- Testes com **Jest + Supertest** (`app.test.js`): GET `/` → status 200 e texto "Olá Mundo DevOps!".
- **Dockerfile multi-stage** (builder + produção, `node:22-alpine`, `npm ci --omit=dev`).
- **`.dockerignore`**: não copiar `node_modules`, `npm-debug.log`, `.git`, `.gitignore`.
- **GitHub Actions**: arquivo `.github/workflows/ci.yml`; job `test-and-build`, `runs-on: ubuntu-latest`.
- **Pegadinha:** o CI **não usa** `server.js` (testa o `app`); o **Docker usa**.

---
## AULA 04 — Proteger a Branch main e Publicar no Registro

### Branch Protection
- **Definição:** regra que impede merge na `main` se o **status check** (job de CI) não passar.
- **Onde:** Settings > Branches > Add branch protection rule > `main` > "Require status checks to pass before merging" + "Require branches to be up to date" > check `test-and-build`.

### Publicar a imagem só após o merge
- **No PR:** só testa e faz build (steps de login/push ficam **skipped**).
- **No push na main (após merge):** loga no **GHCR** (`ghcr.io`), extrai metadados (tags `sha` e `latest`) e faz **push** da imagem.
- **Condição:** `if: github.event_name == 'push' && github.ref == 'refs/heads/main'`.
- **Senha:** `secrets.GITHUB_TOKEN` (segredo automático do GitHub).
- **Pegadinha:** o merge **gera um push** na main → o pipeline roda de novo, agora publicando.

---
## AULA 05 — Entrega Contínua (CD)

### Entrega × Implantação Contínua ⭐
| Termo | Significado na aula |
|---|---|
| **Entrega Contínua** | após merge, a imagem é **publicada** no registro (GHCR) — pronta para ir ao ar |
| **Implantação Contínua** | após publicar, o pipeline **implanta automaticamente** no servidor |
- **Pegadinha:** as duas são chamadas de "CD". Diferença: **publicar o artefato** × **colocar no ar sozinho**.

### Ferramentas
- **Self-hosted Runner:** "agente" instalado na sua máquina que escuta jobs do GitHub ("Listening for jobs..."). Pasta `actions-runner` vai no `.gitignore`.
- **docker-compose.yml:** define o serviço `app` com `image: ghcr.io/USUARIO/REPO:latest`, `ports "3000:3000"`, `restart: always`, `pull_policy: always`.
- **Job 2 `deploy-to-local`:** `needs: test-and-build` · `runs-on: self-hosted` · só em push na main · faz `docker-compose pull` + `up -d --no-build` + `docker image prune -f`.
- **Pegadinha:** `needs` = só roda se o Job 1 terminar **com sucesso**.

---
## AULA 06 — DevSecOps

### DevSecOps
- **Definição:** integrar **segurança automaticamente** no pipeline de CI/CD (complemento: "shift left" = testar segurança cedo).

### 3 tipos de verificação ⭐
| Sigla | Nome | Verifica | Ferramenta da aula |
|---|---|---|---|
| **SCA** | Análise de Composição de Software | vulnerabilidades nas **dependências** (`package.json`/lock) | `npm audit --audit-level=high` |
| **SAST** | Teste de Segurança de Aplicação **Estática** | o **seu código-fonte** (SQL Injection, caminhos inseguros) | **CodeQL** (GitHub Code Scanning) |
| **Container scan** | Verificação de contêiner | vulnerabilidades na **imagem** (ex.: `node:22`) | **Trivy** |
- **Extras:** **Secret Protection** e **Push protection** (impede dar push de senha por engano).
- **Onde no pipeline:** segurança **depois** dos testes e **antes** de publicar a imagem. Trivy fica **entre o build e o push**.
- **`--audit-level=high`:** falha só com vulnerabilidade **alta ou crítica**.
- **Efeito:** falha crítica → não publica → Job 2 (deploy) **não roda**.
- **Corrigir localmente:** `npm audit` → `npm audit fix` → (se preciso) `npm audit fix --force` → confirmar "found 0 vulnerabilities".
- **Pegadinha:** SAST = **seu** código; SCA = código **dos outros** (bibliotecas).

---
> ⚠️ **Observações:** (1) O YAML completo com Trivy (Aula 06) está num link externo do GitHub do professor, não na pasta — descrevi pela explicação do slide. (2) O slide 8 da Aula 06 mostra `npm audit -.audit-level=high` (erro de digitação); o correto é `--audit-level=high`. (3) Na Aula 03, `npm install express –save` usa travessão; o correto no terminal é `--save` / `-D`.
